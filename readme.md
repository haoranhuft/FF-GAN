## FF-GAN

This repository is the official code for the paper "Fine-grained Cross-modal Fusion based Refinement for Text-to-Image Synthesis" by Haoran Sun, Yang Wang (corresponding author: [yangwang@hfut.edu.cn](mailto:yangwang@hfut.edu.cn)), Haipeng Liu, Biaoqian.

### Introduction

### How to use

0. **Requirements** 

```
Python >= 3.6
PyTorch >= 1.0
NVIDIA GPU + CUDA cuDNN
```

1. **Data** 
   1. Download metadata for [birds](https://drive.google.com/open?id=1O_LtUP9sch09QH3s_EBAgLEctBQ5JBSJ) [coco](https://drive.google.com/open?id=1rSnbIGNDGZeHlsUlLdahj0RJ9oo6lgH9)and save them to your path
   2. Download the [birds](http://www.vision.caltech.edu/visipedia/CUB-200-2011.html) image data.
   3. Download [coco](http://cocodataset.org/#download) dataset and extract the images to `data/coco/`

2. **Pretrained Models**
   1. [DAMSM for bird](https://drive.google.com/open?id=1GNUKjVeyWYBJ8hEU-yrfYQpDOkxEyP3V).
   2. [DAMSM for coco](https://drive.google.com/open?id=1zIrXCE9F6yfbEJIbNP5-YrEe2pZcPSGJ)

3. Training 
   * Modify the parameters in parse to your local directory
   * You can modify some parameters in the cfg file
   * change the 

```python
python /FF_GAN/code/main.py --cfg cfg/bird_DMGAN.yml --gpu 0
python /FF_GAN/code/main.py --cfg cfg/coco_DMGAN.yml --gpu 0
```

4. Validation

```python
# image genaration:
python /FF_GAN/code/main.py --cfg cfg/eval_bird.yml --gpu 0
python /FF_GAN/code/main.py --cfg cfg/eval_coco.yml --gpu 0

# FID
python fid_score.py --gpu 0 --batch-size 50 --path1 bird_val.npz --path2 your generated picture path
# R-precision
# You will get the result of R-precision when 30k pictures are generated
python /FF_GAN/code/main.py --cfg cfg/eval_bird.yml --gpu 0
python /FF_GAN/code/main.py --cfg cfg/eval_coco.yml --gpu 0

```


