<h1 align="center">Hi 👋, I'm Saurav Raj Paudel</h1>
<h3 align="center">Systems-ML Engineer | Edge Inference Deployment & CUDA Kernel Optimization</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Focus-Edge%20ML%20%26%20CUDA%20Kernels-blueviolet?style=for-the-badge" alt="Focus" />
  <img src="https://img.shields.io/badge/Hardware-AMD%20Versal%20%7C%20Kria%20%7C%20NVIDIA%20Ada-orange?style=for-the-badge" alt="Hardware" />
</p>

---

I deploy quantized perception models on AMD edge silicon and write hand-tuned CUDA kernels. I'm comfortable working from PyTorch all the way down to C++/NEON/OpenMP and SASS-level GPU profiling.

- 🔧 **Currently building**: A CUDA GEMM optimization ladder on power-constrained mobile Ada (RTX 4050, sm_89, ~55 W TGP). It starts from a naive kernel and works up through SMEM tiling, register tiling, vectorized loads, and warp tiling. Tensor-core and CUTLASS stages are next.
- ⚡ **Core work**: Production edge ML deployment. INT8 PTQ, DPU/NPU partitioning, and op-level PyTorch-to-hardware parity on AMD Versal AI Edge (VE2802) and Xilinx Kria K26.
- 🌱 **Deep diving**: GPU performance engineering (Nsight Compute, bank-conflict analysis, warp scheduling) and inference kernels for VLM/LLM workloads.
- 💬 **Ask me about**: Model compression (pruning and quantization), DPU/CPU/NPU co-design, and squeezing throughput out of a thermally throttled laptop GPU.
- 📫 **Reach me**: [paudelsaurav3@gmail.com](mailto:paudelsaurav3@gmail.com) | [LinkedIn](https://linkedin.com/in/sauravrajpaudel)

---

### 🚀 Featured Work

**[CUDA GEMM Kernel Optimization](https://github.com/Sauravrp67/CUDA-GEMM)**

An FP32 SGEMM optimization ladder on sm_89 (~105 W TGP). It starts from a naive kernel and works up through shared-memory tiling, thread coarsening, 1D/2D register tiling, 128-bit vectorized loads, and warp tiling, all exposed through PyTorch bindings and validated against `torch.matmul`. Nsight Compute drove the tuning: FMA-pipe utilization went from 28% to 53%, SM throughput from 41% to 65%, and the best kernel hits **6.57 TFLOPS** on an 8192x8192 FP32 matmul. That's **8.8x over the naive version** and **89.6% of `torch.matmul`** on the same throttled silicon. Tensor-core (mma/wmma) and CUTLASS stages are still in progress.

---

### 🛠️ Technical Stack

| Domain | Technologies |
| :--- | :--- |
| **HPC & Systems** | **C++ / CUDA**, Nsight Compute, OpenMP, NEON SIMD, Pybind11, PetaLinux, bare-metal ARM |
| **Edge AI Deployment** | **VitisAI (DPU/NPU)**, VART C++, ONNX, INT8 PTQ, model pruning, Metavision SDK |
| **DL Frameworks** | **PyTorch**, cuDNN |
| **Hardware** | AMD Versal AI Edge VE2802 (Cortex-A72 PS + AIE-ML), Xilinx Kria K26 (Cortex-A53), NVIDIA Ada (sm_89) |

---

### 📌 Selected Highlights

- **Bit-accurate C++17 reference model.** Authored a NanoDet-Plus C++17 reference and a .pth-to-.bin exporter that defines the algorithmic spec the Verilog/RTL team builds against. PyTorch parity holds at 1e-5 / 1e-4 across 20 ops.
- **PointPillars on Versal VE2802.** Partitioned PillarLayer/Encoder to the CPU and the dense CNN to the AIE-ML NPU, landing 1.82 ms of NPU compute (18.43 GMACs). Fused PillarLayer and Encoder into a single C++/NEON/OpenMP pass on the Cortex-A72 PS, which got roughly 7x over the Python/NumPy baseline.
- **Event-camera detection on Kria K26.** Ran a Prophesee/Metavision feed through an INT8 YOLOv8n via VART C++. Hit 37.8% mAP@0.5 on PEDRo at 31 ms end-to-end, adding only 3-4 W of DPU power over SOM idle.
- **Structured channel pruning.** Applied VainF/depGraph Taylor-importance pruning to YOLOv3, taking MACs from 32.8G down to 18.8G (43% fewer) and params down 39% for about a 2% mAP@0.5 drop on Pascal VOC. That cut Kria K26 DPU latency by 33%.

---

### 🧰 Languages & Tools

<p align="left">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=cpp,c,linux,bash" />
  </a>
  <br>
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=py,pytorch,docker,git" />
  </a>
</p>

---

### 📊 GitHub Stats

<p align="left">
  <img src="https://github-readme-stats.vercel.app/api?username=Sauravrp67&show_icons=true&theme=tokyonight&hide_border=true" alt="Saurav's GitHub Stats" height="170" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Sauravrp67&layout=compact&theme=tokyonight&hide_border=true" alt="Top Languages" height="170" />
</p>
<p align="left">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Sauravrp67&theme=tokyonight&hide_border=true" alt="Saurav's Streak Stats" />
</p>
