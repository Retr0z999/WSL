# WSL — Windows Subsystem for Linux

> Mission: turn Windows into a first-class Linux ML/HPC dev box — including working GPU acceleration.

This is a **standalone repo**. Check boxes (`- [x]`) to track progress; they render as checkboxes on GitHub.

---

## Learning Pathway (phased)

### Phase 1 — Setup & Config (`setup-and-config/`)
- [X] Install **WSL2** (`wsl --install`), pick a distro (Ubuntu LTS recommended)
- [X] **Windows Terminal** + a good shell (zsh + oh-my-zsh or starship)
- [X] Tune `.wslconfig` (memory, CPU, swap) for ML workloads
- [X] Understand the WSL filesystem boundary — keep projects in the Linux FS (`~/`), **not** `/mnt/c`, for speed

### Phase 2 — Dev Environment (`dev-environment/`)
- [X] Python via **uv** (fast) or conda/mamba; per-project virtualenvs
- [X] **VS Code Remote – WSL** (edit in Windows, run in Linux)
- [X] `git` + SSH keys + credential sharing with Windows
- [X] **tmux** for persistent sessions; dotfiles repo
- [X] Docker (Docker Desktop WSL2 backend or native engine)

### Phase 3 — GPU Acceleration (`gpu-passthrough/`)
This is what makes WSL viable for DL.
- [X] Install the **NVIDIA driver on Windows** (the WSL-enabled driver — do **not** install a Linux driver inside WSL)
- [X] Install the **CUDA Toolkit for WSL2** inside the distro
- [X] Verify: `nvidia-smi` works in WSL
- [X] Verify PyTorch sees the GPU: `torch.cuda.is_available()` → `True`
- [X] Run a real training step on GPU to confirm throughput

### Phase 4 — Automation (`scripts/`)
- [X] Bootstrap script: fresh distro → full ML env in one command
- [ ] Dotfiles (`.zshrc`, `.tmux.conf`, git config) version-controlled
- [ ] Helper scripts (env activation, GPU check, project scaffolding)

---

## Best / Most Effective Practices
| Practice | Why it matters |
|---|---|
| Keep code in the Linux filesystem (`~/`) | `/mnt/c` I/O is dramatically slower |
| Windows-side NVIDIA driver only | Installing a Linux driver in WSL breaks GPU passthrough |
| `uv` for Python | Order-of-magnitude faster installs/resolutions than pip |
| VS Code Remote – WSL | Native-feeling editing with Linux execution |
| A bootstrap script | Rebuild your whole environment in minutes, reproducibly |

## Milestone Projects
- [ ] One-command bootstrap that provisions Python + CUDA + tools on a fresh distro
- [ ] Confirmed GPU training run inside WSL with `nvidia-smi` monitoring
- [ ] Versioned dotfiles you can clone onto any machine

## Top Resources
- [WSL Official Docs](https://learn.microsoft.com/en-us/windows/wsl/)
- [CUDA on WSL User Guide](https://docs.nvidia.com/cuda/wsl-user-guide/)
- [VS Code Remote – WSL](https://code.visualstudio.com/docs/remote/wsl)
- [uv (Astral)](https://docs.astral.sh/uv/)

---
## Progress Log
<!-- date — what I set up -->
6/7/26 
- It took me about 2-3 days to play around with WSL and get to Phase 4.
- Most of it was downloading and installing, so this wasn't that crazy.
- Fiddling period was 6/5/26-6/7/26 for Phases 1-3 and Script for Phase 4.