# DeepSpeed 0.17.4 — Windows x86_64 (Python 3.12, CUDA 12.9)

This repository provides a **prebuilt DeepSpeed 0.17.4 wheel** for **Windows 64-bit**, built against:

- **Python:** 3.12
- **CUDA Toolkit:** 12.9 (NVCC 12.9.41)
- **PyTorch:** 2.8.0+cu129

The wheel includes compiled CUDA kernels, with **Sparse Attention** and **Evoformer Attention** disabled for Windows compatibility.

---

## 📦 Wheel

- **Filename:** `deepspeed-0.17.4+c4b1a8cb-cp312-cp312-win_amd64.whl`
- **SHA256 checksum:** `6d0964a6b204bfd9eff2bf972d0c6587fe6c66c0f29c0972b0f6080a670b1ec3`

---

## 🛠 Build Environment

| Component        | Version / Details |
|------------------|-------------------|
| OS               | Windows 10/11 x64 |
| Python           | 3.12.10 (venv)    |
| CUDA Toolkit     | 12.9 (NVCC 12.9.41) |
| NVIDIA Driver    | Compatible with CUDA 12.9 |
| Visual Studio    | 2022 Build Tools (MSVC v143), **x64 Native Tools** prompt |
| PyTorch          | 2.8.0+cu129       |
| DeepSpeed commit | `c4b1a8cb` (tag `v0.17.4`) |
| Build frontend   | `pypa/build`      |

---

## ⚙ Build Flags Used

```powershell
set DS_BUILD_OPS=1
set DS_BUILD_SPARSE_ATTN=0
set DS_BUILD_EVOFORMER_ATTN=0
set TORCH_CUDA_ARCH_LIST=8.9+PTX
````

These flags:

* Enable main DeepSpeed CUDA ops
* Disable Windows-problematic ops (`SPARSE_ATTN`, `EVOFORMER_ATTN`)
* Target NVIDIA Ada GPUs (8.9) with PTX fallback

---

## 📥 Installation

1. Install a PyTorch build for **CUDA 12.9**:

   ```powershell
   pip install torch torchvision --index-url https://download.pytorch.org/whl/cu129
   ```

2. Install the wheel:

   ```powershell
   pip install deepspeed-0.17.4+c4b1a8cb-cp312-cp312-win_amd64.whl
   ```

3. Verify:

   ```powershell
   python -c "import torch, deepspeed; print(torch.__version__, torch.version.cuda); print('DeepSpeed', deepspeed.__version__)"
   ```
