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
- Discovered that the application was actually a local web app running on `localhost`
- Analyzed `.pyc` files using tools like `strings`, `pycdc`, and `pycdas`
- Learned how React/Vite frontend assets can be bundled into a standalone executable
- Realized how difficult production frontend bundles are to understand without the original source code
- Thought deeply about maintainability in the age of AI-generated applications

---

# What I Reverse Engineered

As someone who works in IT administration and internal tooling, I became curious about how a coworker’s AI-generated desktop application was actually structured internally.

The application itself was a harmless PDF-processing utility built for local use, but I wanted to better understand:

- What technologies were being used under the hood
- Whether the executable was simply a packaged Python application
- How modern AI-generated applications are architected
- What maintainability and transparency look like in AI-assisted development

I didn’t approach this from a malware-analysis perspective.

Instead, this became a technical exploration into how a modern Python-based desktop application could be packaged and delivered as a standalone `.exe`.

At first, I assumed it was a traditional Windows desktop application.

However, while inspecting the executable, I noticed something interesting:

```text
localhost:8000
```

That single clue completely changed my understanding of the application.

Instead of being a traditional desktop GUI app, it turned out to be:

```text
React/Vite Frontend
        ↓
FastAPI Backend
        ↓
PyMuPDF / OpenCV
        ↓
PDF Processing
```

In other words, it was actually a local web application packaged into a Windows `.exe`.

That realization made the reverse engineering process surprisingly exciting.

> **Note:**
> The application discussed in this article was an internally shared utility created for local use, and this exploration was performed purely for educational, architectural, and maintainability-learning purposes within an authorized context.
>
> The goal was not malware analysis or bypassing protections, but rather understanding how modern AI-assisted applications are structured and packaged as standalone executables.

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

I installed several tools for inspecting the executable and Python bytecode:

```bash
pip install pyinstaller
pip install uncompyle6
pip install decompyle3
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
PyInstaller
```

This strongly suggested that the application had been packaged using PyInstaller.

---

## Step 2 — Inspecting the PyInstaller Archive

Next, I used:

```bash
pyi-archive_viewer PDF.exe
```

That revealed embedded `.pyc` files and frontend assets.

I found things like:

```text
app.pyc
pdf_stamp_processor.pyc
pdf-stamp-frontend/dist
```

At that point, I realized the application contained both:

- A Python backend
- A built frontend bundle

---

## Step 3 — Analyzing `.pyc` Files

I then used:

```bash
pycdc
pycdas
```

to inspect Python bytecode files.

Although Python 3.13 compatibility was incomplete, I could still reconstruct large parts of the backend structure.

I discovered:

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

# What I Found

The executable was essentially doing this:

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

That architecture was fascinating to uncover.

---

# What I Learned

## Modern `.exe` Applications Can Actually Be Web Apps

This was probably the biggest surprise.

Even though the application looked like a desktop app, internally it was:

- A local HTTP server
- A React frontend
- A browser-based UI

---

## Build Outputs Are Extremely Hard to Read

Without the original source code:

```text
src/
components/
hooks/
```

understanding frontend behavior becomes very difficult.

The production bundle was optimized for browsers, not humans.

---

## “Working Software” and “Understandable Software” Are Different Things

This experience made me think deeply about AI-generated applications.

Generative AI can absolutely produce working software.
However, maintainability becomes a serious concern when:

- The original project structure is missing
- Only compiled artifacts remain
- The author themselves may not fully understand the generated architecture

Even after reverse engineering the executable, I still couldn’t fully reconstruct the original frontend source code or understand every implementation detail.

That experience itself became one of the biggest lessons for me.

It reminded me that modern software — especially AI-generated applications — can become very difficult to maintain or fully understand once only compiled artifacts remain.

---

# Final Thoughts

This reverse engineering journey was honestly a lot of fun.

Watching the architecture slowly reveal itself step by step felt surprisingly exciting:

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

At the same time, it reminded me that understanding software architecture is just as important as making software work.

Especially in the age of AI-generated code.
