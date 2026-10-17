# Contributing to NVIDIA DGX Spark Agentic Blueprint

Welcome! This blueprint was born out of real-world trials, breakthrough engineering, and empirical problem-solving on the **NVIDIA DGX Spark** (Grace Blackwell GB10, 128GB Unified Memory, ARM64).

We actively invite creators, researchers, systems engineers, and open-source AI developers to collaborate, share discoveries, and evolve this field guide into the definitive sovereign operating manual for the DGX Spark community.

---

## How to Get Involved

Whether you have tested a new model, discovered an optimization flag, or solved an ARM64 dependency riddle, your insights are invaluable.

### 1. Propose New Sub-Commands
If you have automated a tedious deployment on DGX Spark (e.g., NeMo pretraining, vLLM ARM64 serving, Whisper streaming, Wan 2.1 variations), draft a clean, atomic sub-command for [`MASTER_SYSADMIN_PROMPT.md`](./MASTER_SYSADMIN_PROMPT.md).

### 2. Benchmark & Verify SOTA Models
Share your empirical benchmarks on the 128GB Unified Memory architecture:
- Memory bus traffic and generation times.
- Quantization tradeoffs (Scaled FP8 vs. BF16 vs. GGUF).
- Optimal launch flags for ComfyUI, llama.cpp, TensorRT-LLM, and vLLM.

### 3. Report Traps & Workarounds
Did you encounter a newly introduced upstream packaging bug, a translation layer crash, or an OS upgrade trap? Open an Issue detailing:
- The exact failure signature (`SIGABRT`, syscall error, or broken dependency).
- The root cause (e.g. x86 binary masquerading as universal, missing ARM64 symbol).
- The sovereign workaround.

### 4. Become a Collaborator
If you are actively developing, testing, or building on the DGX Spark hardware and want direct write access to contribute regular updates, reach out via GitHub Issues or contact Ajarn Spencer Littlewood ([www.ajarnspencer.com](https://www.ajarnspencer.com)).

---

## Architectural Guidelines for Contributions

To ensure that the blueprint remains reliable and maintainable across all machines, all pull requests must respect the **DGX Spark Operational Invariants**:

1. **Agent-Agnostic First:**  
   Do not hardcode prompts to a single AI tool. Instructions must run seamlessly in **Google Antigravity**, **OpenAI Codex**, **OpenClaw**, **Claude Code**, or standard terminal IDE agents.
2. **ARM64 Native Primacy:**  
   Never recommend or default to x86 translation layers (`box64` / `qemu`) when native ARM64 / aarch64 binaries exist.
3. **OS Distribution Preservation:**  
   Always safeguard Ubuntu 24.04 LTS (Noble) and NVIDIA GB10 proprietary kernel drivers. Never introduce scripts that recommend or trigger distribution upgrades (`do-release-upgrade`).
4. **Declarative Prompts Over Heavy Wrappers:**  
   Prefer atomic bash commands, clean systemd user units (`~/.config/systemd/user/`), and master prompt instructions rather than writing monolithic wrapper software that bitrots.
5. **Zero-Duplication Storage:**  
   Always guide users to centralize master checkpoints in `~/ai-workspace/models/` and link via symlinks (`lms import -l`) or Modelfiles.
6. **Workspace Cleanliness:**  
   Keep user home directories pristine. All environments must reside in `~/ai-workspace/environments/<name>/` and applications in `~/ai-workspace/apps/<name>/`.

---

## Pull Request Workflow

1. Fork the repository.
2. Create a descriptive feature branch (`git checkout -b feature/nemo-fine-tune-subcommand`).
3. Make your edits to `README.md` and/or `MASTER_SYSADMIN_PROMPT.md`.
4. Verify all markdown formatting and links.
5. Commit with a clear, conventional commit message (`feat: add /deploy-vllm-arm64 sub-command`).
6. Push to your fork and submit a Pull Request.

Thank you for contributing to the sovereign AI movement and making the NVIDIA DGX Spark truly shine!
