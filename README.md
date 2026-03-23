# 🎨 SemiSketch: An ancient mural sketch extraction network based on reference prior and gradient frequency compensation

[![Paper](https://img.shields.io/badge/Paper-SIGGRAPH_2023-green)](https://www.sciencedirect.com/science/article/pii/S0031320325008064)


## 📥 Pre-trained Models
Before training, you need to download the pre-trained weights for HED and contrastive learning.

* **📦 Download Link:** [Google Drive](https://drive.google.com/file/d/1YbddMxgIO57gSwTvYxt-C4QraM2AAgVW/view?usp=sharing)
* **🔧 Setup:** After downloading, unzip the files and place them into the `./pretrained_models` directory (or your specified `--checkpoints_dir`).
---
## 📂 Dataset Structure

The dataset doesn't have to be strictly paired; the model handles unpaired data beautifully. Ensure your dataset directory looks like this:

```text
|   \---[dataroot] (e.g., ./datasets/unpaired_s2a)
|       +---testA
|       |       +---test_1.png
|       +---testB
|       |       +---test_groundtruth1.png # not necessary for testing
|       +---trainA
|       |       +---train_1.png
|       +---trainB
|       |       +---sketch_1.png
```

## 📥 Local Setup: Visdom

We use Visdom to monitor the training process. You need to start the Visdom server locally before running the training script on the server.
 * **Start Server: Open a terminal and run:
```bash
python -m visdom.server
```
