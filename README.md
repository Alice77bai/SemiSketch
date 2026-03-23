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
If you encounter any issues with Visdom configuration, please refer to this comprehensive guide:👉 [Visdom 配置文件参考教程 (CSDN)](https://blog.csdn.net/loveinfall_wyc/article/details/123006831)

## Train & Test
Once your dataset, pre-trained models, and Visdom server are ready, you can start running the model on your server!

### 🏃‍♂️ Training
Run the following command to start training the `semi_cut` model with your unpaired dataset:
```bash
python train.py \
  --name mural \
  --CUT_mode CUT \
  --model semi_cut \
  --dataroot ./datasets/unpaired_s2a \
  --checkpoints_dir ./pretrained_models \
  --dce_idt \
  --lambda_VGG -1 \
  --lambda_NCE_s 0.05 \
  --use_curriculum \
  --gpu_ids 0
```
###🧪 Testing
After training, you can test the model's performance on the paired dataset using the following command:
```bash
python test.py \
  --name mural \
  --model cut \
  --direction AtoB \
  --CUT_mode CUT \
  --phase test \
  --preprocess none \
  --dataroot ./datasets/pair_s2a
```


