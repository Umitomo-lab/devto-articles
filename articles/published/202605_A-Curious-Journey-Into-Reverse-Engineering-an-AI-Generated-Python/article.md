---
title: A Curious Journey Into Reverse Engineering an AI-Generated Python .exe
published: false
description: Exploring the inside of a PyInstaller-based Python `.exe` built with generative AI — from FastAPI and React/Vite to `.pyc` analysis and local web app architecture.
tags: beginners, reversing, security, python
series:
canonical_url:
cover_image: https://raw.githubusercontent.com/Umitomo-lab/devto-articles/main/articles/published/202605_A-Curious-Journey-Into-Reverse-Engineering-an-AI-Generated-Python/reverse-engineering-image.png
---

<!--
【MEMO】
■ タグの選択
tagsは最大4つまでなので、以下の中から必要なタグを選択する。,区切りで記述する。
beginners, devjournal, webdev, swift , security
-->

## Introduction

I usually post weekly learning and development updates on Dev.to📝

This time, however, I decided to write a standalone article about something a little different — my first attempt at reverse engineering🦾

What started as simple curiosity quickly turned into an exciting journey of uncovering how a modern AI-generated Python application was actually structured internally🔎

## TL;DR

- Reverse engineered a PyInstaller-based Python `.exe`
- Reconstructed a surprisingly large portion of the application's architecture from the packaged `.exe`
- Analyzed `.pyc` files using tools like `strings`, `pycdc`, and `pycdas`
- Learned how React/Vite frontend assets can be bundled into a standalone executable
- Realized how difficult production frontend bundles are to understand without the original source code
- Thought deeply about maintainability in the age of AI-generated applications

---

# What I Reverse Engineered

As someone who works in IT administration and internal tooling, I often become curious about how applications are actually built under the hood.

This time, a coworker showed me a PDF-processing desktop application that had been created with the help of generative AI.

The overall architecture had already been explained to me verbally beforehand.
However, that led me to a simple but exciting question:

> How much of an application's internal structure can actually be reconstructed just by reverse engineering the final `.exe` file?

That curiosity became the starting point of this exploration.

The application itself was a harmless internal utility designed for local use, and this investigation was performed purely within an authorized and educational context.

Rather than trying to analyze malware or bypass protections, I wanted to understand:

- What information remains inside packaged executables
- How modern Python applications are bundled
- Whether frontend/backend structures could still be inferred after packaging
- How much architectural detail could realistically be reconstructed from compiled artifacts alone

What made the process especially exciting was slowly piecing together the architecture from small clues hidden inside the executable.

---

# Reverse Engineering Environment Setup

Since I was using Kali Linux on WSL for this experiment, I first prepared a small reverse engineering workspace.

## Creating a Python Virtual Environment

```bash
mkdir -p ~/reverse
cd ~/reverse

python3 -m venv venv
source venv/bin/activate
```

At first, the virtual environment failed because `python3-venv` was missing:

```bash
sudo apt install python3.13-venv
```

After that, I recreated the environment successfully.

---

## Installing Basic Analysis Tools

I installed a few basic tools for inspecting the executable and analyzing Python bytecode.

```bash
pip install pyinstaller
```

I also installed `binutils` so I could use `strings`:

```bash
sudo apt install binutils
```

---

## Building `pycdc`

To inspect `.pyc` files more deeply, I built `pycdc` from source:

```bash
sudo apt install -y cmake g++ git

mkdir -p ~/reverse/tools
cd ~/reverse/tools

git clone https://github.com/zrax/pycdc.git

cd pycdc
mkdir build
cd build

cmake ..
make -j4
```

This generated:

```text
pycdc
pycdas
```

which I later used to inspect Python bytecode files.

---

## Extracting the PyInstaller Executable

After confirming the executable was likely packaged with PyInstaller, I used `pyinstxtractor` to extract its contents:

```bash
git clone https://github.com/extremecoders-re/pyinstxtractor.git
```

Then:

```bash
cd ~/reverse/pdf_exe

python ~/reverse/pyinstxtractor/pyinstxtractor.py PDF.exe
```

This generated a directory like:

```text
PDF.exe_extracted/
```

Inside the extracted directory, I was finally able to inspect files such as:

```text
app.pyc
pdf_stamp_processor.pyc
pdf-stamp-frontend/dist
```

This was the point where the application's overall structure started becoming much clearer.

---

# How I Reverse Engineered It

## Step 1 — Running `strings`

I first started with:

```bash
strings PDF.exe
```

Very quickly, I noticed Python-related strings:

```text
python313.dll
pyi-python-flag
...
```

This strongly suggested that the application had been packaged using PyInstaller.

---

## Step 2 — Inspecting the PyInstaller Archive

Next, I used:

```bash
pyi-archive_viewer PDF.exe
```

This helped confirm that the executable had been packaged using PyInstaller and allowed me to inspect the internal archive structure.

---

## Step 3 — Analyzing `.pyc` Files

I then used:

```bash
pycdc
pycdas
```

to inspect the extracted Python bytecode files.

However, when running `pycdc`, I noticed that some parts of the bytecode could not be fully reconstructed.

In many cases, the output stopped after displaying messages like:

```text
Unsupported opcode: CALL_KW (247)
from fastapi import FastAPI, File, UploadFile, Form, HTTPException
...
# WARNING: Decompyle incomplete
```

Instead of fully recovering the original source code, I had to combine multiple fragmented clues together:

- Partial pycdc output
- pycdas disassembly output
- Extracted strings
- Module names
- API route names
- Library imports

I also used generative AI to help interpret and organize those fragmented technical details while reconstructing the application's architecture.

Even with incomplete reconstruction, I was still able to identify:

- FastAPI routes
- PDF processing logic
- OpenCV-based blank-space detection
- PyMuPDF page rendering
- Automatic browser launching
- Local API endpoints such as:

```text
/api/scan
/api/stamp_and_merge
/api/shutdown
```

---

## Step 4 — Investigating the Frontend

The frontend bundle was much harder to understand.

The built JavaScript looked like this:

```js
var e=Object.create,t=Object.defineProperty,...
```

At first, it felt almost impossible to read.

Later, I realized:

- This was a production React/Vite bundle
- The original `src/` files were not included
- Only the compiled `dist/` output remained

That was an important learning moment for me.

The actual development project probably looked something like this:

```text
frontend/
├─ src/
├─ components/
├─ package.json
└─ vite.config.js
```

But after building the frontend:

```bash
npm run build
```

everything became compressed into optimized production assets.

---

# Reconstructing the Architecture

By combining clues from strings, embedded `.pyc` files, frontend assets, and API routes, I was eventually able to reconstruct a rough picture of the application's architecture:

```text
PDF.exe
    ↓
Launch FastAPI server
    ↓
Open browser automatically
    ↓
Serve React frontend
    ↓
React sends API requests
    ↓
Python processes PDFs locally
```

The application was not rendering a desktop GUI directly.

Instead:

- FastAPI served static frontend files
- React rendered the UI inside the browser
- Python handled backend processing

What fascinated me most was not simply discovering the architecture itself, but realizing how much of it could still be reconstructed purely from packaged artifacts.

---

# What I Learned

## Reverse Engineering Can Reveal More Than I Expected

Before starting this experiment, I assumed that most of an application's architecture would disappear once everything had been packaged into a standalone `.exe`.

However, I was surprised by how many clues still remained inside the executable:

- Python runtime artifacts
- PyInstaller structures
- Embedded `.pyc` files
- Frontend build outputs
- API routes
- Localhost references
- Technology-specific strings

By connecting those small clues together step by step, I was able to reconstruct a surprisingly large portion of the application's overall architecture.

That process itself was one of the most exciting parts of the experience.

---

## Production Frontend Bundles Are Extremely Difficult to Understand

One of the biggest challenges was analyzing the frontend.

Without the original source structure:

```text
src/
components/
hooks/
```

understanding the actual UI behavior became extremely difficult.

The built frontend bundle had already been optimized and compressed for browsers, not for humans trying to understand how the application worked internally.

This made me realize how heavily modern frontend development depends on the original project structure and source organization.

---

## “Working Software” and “Understandable Software” Are Different Things

This experience also made me think deeply about AI-generated applications and software maintainability.

Generative AI can absolutely help create working applications quickly.
However, once only compiled artifacts remain, reconstructing the original design and development intent becomes much harder.

Even after reverse engineering the executable, I still could not fully reconstruct the original frontend source code or understand every implementation detail.

That limitation itself became an important lesson for me.

It reminded me that understanding software architecture and preserving maintainable source structures are just as important as making software work.

Especially in the age of AI-assisted development.

---

# Final Thoughts

This reverse engineering journey was honestly a lot of fun.

What made the experience especially enjoyable was gradually reconstructing the application's architecture from small technical clues hidden inside the executable.

Watching the structure slowly reveal itself step by step felt surprisingly rewarding:

```text
PyInstaller
    ↓
FastAPI
    ↓
localhost
    ↓
React/Vite
    ↓
PyMuPDF
```

At the same time, the experience gave me a deeper appreciation for software architecture, maintainability, and the importance of preserving understandable source code alongside AI-generated applications.
