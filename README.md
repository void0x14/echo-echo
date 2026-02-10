# ECHO: THE DISTRIBUTED NEURAL GRID [PROTOCOL V.0.14]

![Architecture](https://img.shields.io/badge/ARCH-DISTRIBUTED__SWARM-critical?style=for-the-badge)
![Network](https://img.shields.io/badge/LINK-RPC__OVER__ETHERNET-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/STATUS-GRID__SYNCHRONIZATION-yellow?style=for-the-badge)

> **"One machine is a tool. Two machines are an organism."**

## 🏴‍☠️ MANIFESTO: THE SWARM PROTOCOL

We reject the limitation of a single chassis. **ECHO** is a **Distributed Cognitive Grid** that unifies separate hardware nodes into a single coherent intelligence.

We do not accept "hardware limitations". We utilize **"Scrap-Metal Clustering"**. We fuse the high-IPC performance of the **Intel i5-13500H** with the multi-core grit of the **Ryzen 5 3600**, linking them via low-latency RPC protocols to create a **32GB Unified Memory Pool**.

**Mission:** To run massive 70B+ / MoE models (DeepSeek, Qwen, Mixtral) by sharding the neural weights across physical devices, turning a "Home Lab" into a "Personal Data Center".

## 🧠 THE ARCHITECTURE: "NEURAL SHARDING"

We do not run the model on *a* computer. We run the model *between* computers.

### 1. The Split-Brain Engine (RPC Inference)
* **Shard A (The Cortex - Node Alpha):** Handles the complex reasoning, prompt processing, and AVX-512 logic.
* **Shard B (The Subconscious - Node Beta):** Handles bulk weight storage, RAG retrieval, and background context processing.
* **The Synapse:** The devices communicate via Gigabit Ethernet / Thunderbolt Bridge, exchanging tensors in milliseconds.

### 2. Tiered Memory & Storage Hierarchy (The 4-Layer Brain)
* **Tier 0 (VRAM - 2GB + iGPU):** Reserved for "Hot" tokens and display output. (Immediate Reflex).
* **Tier 1 (Distributed RAM - 32GB):** The active workspace. 16GB (Laptop) + 16GB (Desktop) combined.
* **Tier 2 (NVMe Cache - Gen4/Gen3):** The "L3 Cache" for swapping active experts.
* **Tier 3 (The Archive - HDDs):** TBs of cold storage for the Vector DB, massive datasets, and logs.

## 🛠 THE GRID (HARDWARE NODES)

**NODE-ALPHA (The Mobile Command)**
* **CPU:** Intel i5-13500H (Hybrid Arch - Performance Cores).
* **GPU:** Intel Iris Xe (Compute Assist).
* **RAM:** 16GB DDR4 (3200MHz).
* **Storage:** 512GB Gen4 NVMe (System/Hot Model Weights).
* **Role:** Orchestrator, Prompt Ingestion, High-Speed Inference.

**NODE-BETA (The Heavy Anchor)**
* **CPU:** AMD Ryzen 5 3600 (6 Cores / 12 Threads).
* **GPU:** AMD RX 460 2GB (OpenCL/Vulkan Offload).
* **RAM:** 16GB DDR4 (3600MHz).
* **Storage:** 1TB Gen3 NVMe + SATA SSDs + Massive HDD Array (7200/5400rpm).
* **Role:** Expert Offloading, Vector DB Host, Background Tasks.

## 🗺 TACTICAL ROADMAP (EXECUTION PLAN)

### PHASE 1: THE SYNAPSE (NETWORK LAYER)
* **1.1 - Physical Bridging:**
    * Establishing a direct Gigabit Ethernet link between Node-A and Node-B (bypassing router latency).
    * *Objective:* Sub-1ms latency ping.
* **1.2 - Kernel Tuning (CachyOS):**
    * Disabling Nagle’s algorithm (`TCP_NODELAY`).
    * Increasing UDP buffer sizes (`net.core.rmem_max`) to handle massive tensor packet bursts.
* **1.3 - The Handshake:**
    * Setting up SSH keys and secured RPC listeners.
    * Verifying raw bandwidth throughput (iperf3) to ensure it can feed the model weights faster than the CPU can compute them.

### PHASE 2: THE SPLIT-BRAIN (INFERENCE ENGINE)
* **2.1 - The Loader (llama.cpp/exo fork):**
    * Configuring the split-strategy: `--split-mode layer` vs `--split-mode row`.
    * Mapping specific layers: Layers 0-40 on Node-A (Speed), Layers 41-80 on Node-B (Capacity).
* **2.2 - Hybrid Offloading:**
    * Compiling with `CLBlast` / `Vulkan` support to force the RX 460 to handle matrix multiplication for its assigned layers.
    * Utilizing i5-13500H AVX-512 instructions for the heavy prompt processing.
* **2.3 - Synchronization Test:**
    * Running a 70B parameter model.
    * Monitoring "Tensor Transfer Time" vs "Compute Time" to find the bottleneck.

### PHASE 3: THE MEMORY (DATA PIPELINE)
* **3.1 - The Janitor Daemon:**
    * Python script running on Node-B (HDD Array).
    * Continuously indexing logs, codebases, and chats into a local Vector DB (`ChromaDB` / `Qdrant`).
* **3.2 - Tiered Caching:**
    * Configuring the system to keep "Recent Context" on Node-A's Gen4 NVMe.
    * Moving "Old Context" to Node-B's Gen3 NVMe.
    * Moving "Archived Context" to Node-B's HDDs.

### PHASE 4: THE SENTINEL (ZSH INTEGRATION)
* **4.1 - Shell Hooks:**
    * Integrating `zsh-autosuggestions` with the local model API.
    * If a command fails (`exit code != 0`), the error log is automatically sent to the Grid for analysis.
* **4.2 - Autonomous Watcher:**
    * A lightweight daemon on Node-B watching filesystem changes.
    * "New project folder created" -> Triggers auto-generation of `.gitignore` and `README` templates based on user habits.

## ⚠️ WARNING

**Latency is the enemy.**
This architecture relies on precise network synchronization. Any packet loss results in brain damage (hallucinations).
**System:** CachyOS (x86_64) | Shell: Zsh

---
*Architect: Void0x14 | Status: GRID_SYNCHRONIZED*
