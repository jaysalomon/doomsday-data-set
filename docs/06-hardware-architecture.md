# Hardware architecture: home server to field system

## 1. Current target: home/server/workshop

The full capability stack is practical now at home-server or workstation scale:

- Local 20–30B-class reasoning model, subject to current benchmarked profiles.
- Large SSD/NVMe capacity for DDS packs, indexes, structured databases, and workspace data.
- CPU/RAM for orchestration, databases, Python, parsing, and normal computation.
- A main inference accelerator with enough memory to keep the model responsive.
- A separate CUDA/tensor worker for heavy numerical work, vision, image generation, simulation, and DDS processing.
- Local scientific tooling, CAD, Blender, and workshop/fabrication interfaces.

The CUDA worker is a power tool, not the resident brain. It can run on demand without competing with the main inference model for VRAM or compute. A VM/passthrough arrangement can make it a clean separate appliance if that suits the host architecture.

## 2. Compute hierarchy

Assign each workload to the least-powerful capable layer:

```text
CPU     → orchestration, parsing, DB work, light Python, device control
NPU     → always-on classification, embeddings, intent routing, light vision
iGPU    → routine inference, reranking, moderate tensor work
main GPU→ strong local reasoning and multimodal workloads
CUDA worker → simulation, image generation, heavy vision, specialist ML
NVMe    → corpus and indexes; mostly dormant until retrieval
```

The scheduler's principle is simple: do not wake expensive silicon unless the cheaper layer cannot complete the task well enough.

## 3. Workshop loop

With a 3D printer, laser cutter, CNC, CAD, Blender, measurement tools, multimeter, oscilloscope, thermal camera, and scanner, DDS supports an AI-assisted microfactory/technical workshop:

```text
identify → retrieve → inspect/measure → calculate → design
→ simulate/check → make → fit/test → revise
```

## 4. Future field system

The desired end state is a rugged laptop-scale field instrument with large unified memory, multi-terabyte NVMe, local model and vision capability, multimodal I/O, and an independently burst-capable accelerator. It is not yet practical at the specified capability, power, cost, and battery envelope.

The sequence remains: prove workflows on the home/server system, keep corpus and interfaces portable, then shrink the compute package as memory-per-watt, model quality-per-parameter, accelerators, and power management improve. The eventual field tool should be an implementation profile of DDS, not a separately designed knowledge system.
