# StarVLA — Setup Guide

Installation and deployment guide for running [StarVLA](https://github.com/starVLA/starVLA) on the Robotis SG2 AI Worker with NVIDIA IsaacLab simulation.

> Full guide: **[https://rao-sanaullah.github.io/starVLA_setup/](https://rao-sanaullah.github.io/starVLA_setup/)**

## Quick links

- [Official StarVLA repository](https://github.com/starVLA/starVLA)
- [Full installation guide](https://rao-sanaullah.github.io/starVLA_setup/)
- [Project results](https://yourname.github.io/starvla-results)
- [Paper](#)

## Requirements

| Component | Version |
|---|---|
| Python | 3.10+ |
| PyTorch | 2.12.0+ (CUDA 12.8) |
| GPU VRAM | 32 GB (RTX 5090 tested) |
| OS | Ubuntu 22.04 |

## Quick start

```bash
# Clone official StarVLA
git clone https://github.com/starVLA/starVLA
cd starVLA

# Install
pip install -r requirements.txt
pip install -e .

# Start policy server (state-free)
python deployment/model_server/server_policy.py \
    --ckpt_path results/Checkpoints/ffw_sg2_400k_nostate_v2/checkpoints/steps_200000_pytorch_model.pt \
    --port 5555 \
    --use_bf16

# Run inference bridge
python scripts/inference/starvla_inference.py \
    --task RobotisSG2-PaintBrush-v0 \
    --starvla_host 172.17.0.2 \
    --starvla_port 5555
```

See the [full guide](https://rao-sanaullah.github.io/starVLA_setup/) for complete setup, fine-tuning, and configuration details.

---

*Based on [StarVLA](https://github.com/starVLA/starVLA) by the HKUST team.*
