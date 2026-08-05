# Hey there, i'm Gagan 👋

CS student @ Faculty of Technology, Delhi University → building across AI/ML, embedded systems, and computer vision.

I like owning the whole pipeline — train it, optimize it, ship it — and I tend to end up building in domains I've never touched before.

---

## 🔧 What I'm Building

### 🕵️ [PCB Detective](https://github.com/Gagansharma-code/PCB-DETECTIVE)
**point a phone at a board, get a datasheet-backed verdict on what actually works.**

- end-to-end automated PCB component verification, running entirely on-device on an Arduino UNO Q — no cloud dependency anywhere in the pipeline
- pipeline: phone detects components → cross-references against a Knowledge Graph of real datasheet data → ranks pins worth physically probing under a time budget → probes them via onboard MCU → returns a `PASS` / `MISMATCH` / `NOT_TESTED` / `NO_KG_DATA` verdict with the datasheet citation behind it
- built as the independent verification layer of a 5-repo ecosystem (**OpenForge**) — vision in, physical measurement out, evidence throughout
- built for the Snapdragon Multiverse Hackathon on the Arduino UNO Q + Qualcomm AI PC

### 🎾 [Courteye](https://github.com/Gagansharma-code/Courteye) *(co-founder)* — AI Tennis Line-Calling System
**real-time ball detection and tracking for automated in/out calls, on a dual-camera edge deployment (Raspberry Pi + Hailo accelerator).**

- the core challenge: detecting a ball that's just 5–22 pixels in frame — small-object detection under motion blur, variable lighting, and hard real-time constraints
- built the full ML pipeline: leakage-safe dataset curation, a custom YOLOX-Nano training run, and an evaluation harness benchmarking recall/precision against hand-labeled ground truth
- found and fixed critical data bugs — static-ball label contamination, a coordinate-decode bug in ONNX export, and a crop-sampler rebuilt to match real deployment ball-size distribution
- extended YOLOX to take 3 stacked frames (9-channel input) instead of single-frame RGB, inspired by TrackNet/WASB — a **+28pp recall improvement** over single-frame detection
- added a confirmation-gate to the Kalman-filter tracker to stop it "coasting" on false positives — cut the false-positive rate roughly in half

### 🧠 [KG Builder](https://github.com/Gagansharma-code/KG_BUILDER) — OpenForge
**contributions to the orchestration layer of an AI-driven PCB-design pipeline.**

- **ASHA Search Controller** — built the missing loop between generating a design and deciding what to do with it: evaluates BOM candidates in parallel, scores each schematic with a 5-layer structural verifier, and routes the winner to ship, simulated-annealing polish, or beam-search escalation based on score — feeding outcomes back into a TPE sampler so future selection improves over time
- **Weak-Model Self-Improvement Loop** — a small local model (Qwen2.5-1.5B) closing most of the gap to a much larger one purely through verifier-scored retries, no fine-tuning — feeding concrete verifier violations back as correction feedback across an adaptive-temperature retry loop

### 📚 [The Librarian](https://github.com/Gagansharma-code/The-Librarian) — OpenForge
**a component-intelligence service that answers questions about electronic parts with every claim traceable to a cited source — it never guesses.**

- **two-graph architecture**: a shared Global KG (manufacturer datasheets, parsed reference designs, lifecycle/compliance data) and a private, air-gapped Personal KG per org (usage history, rejection/acceptance decisions) — genuinely separate Neo4j databases, not a labeled partition of one
- when the two disagree, nothing is silently merged — an `OverrideDecision` node records who, when, and why, and any answer touching that part surfaces both sides with separate citations
- the agent never writes free-form Cypher — it selects from a fixed catalog of 14 versioned query templates (identity/parametric, topology, ecosystem/co-occurrence, trust/lifecycle, org decision history) and fills in typed parameters
- for the highest-stakes fields (lifecycle status, compliance flags, override reasons), the LLM doesn't even author the wording — a fixed Python renderer produces the sentence straight from the real field value, closing off small-model paraphrase bugs at the architecture level rather than catching them after the fact
- built with a local Qwen2.5-1.5B agent (no external API calls), FastAPI backend, and a React + Vite + Tailwind dashboard

### ⚽ [Gaffer's Guide](https://github.com/Gagansharma-code/GaffersGuide-to-a-good-game) *(co-founder)*
**AI football analytics — turning raw match footage into usable tactical data.**

- FastAPI inference server wired end-to-end into an Electron desktop workspace
- pip-installable Python library on PyPI with lazy-loaded ML dependencies for zero boot-time cost
- ~42 FPS tracking on an RTX 3060 with ~48% VRAM reduction via dynamic FP16 gating
- designed and built the full [marketing website](https://gaffers-guide-website.vercel.app) myself in React, owning the product's end-user-facing side end-to-end

### 🎧 [SignalGuard](https://github.com/Gagansharma-code) — Deepfake Audio Detection
**a WavLM-based transformer model that tells real speech from AI-generated audio.**

- 99.74% validation accuracy on the ASVspoof 2019 benchmark
- custom PyTorch DataLoader handling 2.5GB / 50,000+ `.flac` files with dynamic padding
- mixed-precision training, cosine annealing LR, and W&B-logged experiment tracking

---

## 🌐 Socials
[![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/simplygagann)

## 💻 Tech Stack:
![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white) ![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white) ![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![LaTeX](https://img.shields.io/badge/latex-%23008080.svg?style=for-the-badge&logo=latex&logoColor=white) ![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white) ![nVIDIA](https://img.shields.io/badge/cuda-000000.svg?style=for-the-badge&logo=nVIDIA&logoColor=green) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Google Cloud](https://img.shields.io/badge/GoogleCloud-%234285F4.svg?style=for-the-badge&logo=google-cloud&logoColor=white) ![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white) ![Electron.js](https://img.shields.io/badge/Electron-191970?style=for-the-badge&logo=Electron&logoColor=white) ![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi) ![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white) ![OpenCV](https://img.shields.io/badge/opencv-%23white.svg?style=for-the-badge&logo=opencv&logoColor=white) ![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white) ![Three js](https://img.shields.io/badge/threejs-black?style=for-the-badge&logo=three.js&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white) ![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white) ![Neo4J](https://img.shields.io/badge/Neo4j-008CC1?style=for-the-badge&logo=neo4j&logoColor=white) ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) ![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white) ![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white) ![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black) ![Keras](https://img.shields.io/badge/Keras-%23D00000.svg?style=for-the-badge&logo=Keras&logoColor=white)

---

- 📧 [gs354844@gmail.com](mailto:gs354844@gmail.com)
- 💼 [linkedin.com/in/gagan-sharma07](https://linkedin.com/in/gagan-sharma07)

<p align="center"><em>train it, optimize it, ship it.</em></p>

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->
