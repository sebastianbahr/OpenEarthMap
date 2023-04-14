<img src="https://github.com/sebastianbahr/OpenEarthMap/blob/main/images/inference_CV1.png" alt="Title image 1" class="center" style="margin: 0px 0px 0px 0px; padding: 2px 2px 2px 2px;" />
<img src="https://github.com/sebastianbahr/OpenEarthMap/blob/main/images/inference_CV2.png" alt="Title image 2" class="center" style="margin: 0px 0px 0px 0px; padding: 2px 2px 2px 2px;" />
<img src="https://github.com/sebastianbahr/OpenEarthMap/blob/main/images/inference_CV3.png" alt="Title image 3" class="center" style="margin: 0px 0px 0px 0px; padding: 2px 2px 2px 2px;" />
<img src="https://github.com/sebastianbahr/OpenEarthMap/blob/main/images/inference_CV4.png" alt="Title image 4" class="center" style="margin: 0px 0px 0px 0px; padding: 2px 2px 2px 2px;" />
<img src="https://github.com/sebastianbahr/OpenEarthMap/blob/main/images/inference_CV5.png" alt="Title image 5" class="center" style="margin: 0px 0px 0px 0px; padding: 2px 2px 2px 2px;" />

<div align="left">

[![](https://img.shields.io/badge/Colab-white?logo=googlecolab)](#) 
[![](https://img.shields.io/badge/Tensorflow-white?logo=Tensorflow)](#)
[![](https://img.shields.io/badge/Keras-red?logo=Keras)](#)
[![](https://img.shields.io/badge/Python-white?logo=Python)](#)
 
</div>

# OpenEarthMap

The project uses the freely available satellite imagery and corresponding masks from the [OpenEarthMap](https://github.com/bao18/open_earth_map) project to train an U-Net with EfficenctNet B4 backbone.

## Satellite imagery and masks

The satellite imagery and the corresponding masks are not available on this github repository and have to be obtained from [OpenEarthMap](https://zenodo.org/record/7223446#.ZDlGF3ZBxaQ). 

## The model

The model was trained in Keras using most of hyperparameters as suggested by [Xia et al. 2022](https://arxiv.org/abs/2210.10732). The model's performance is shown in the table bellow and correspond to the one found in the original paper. The pre-trained U-Net model with EfficenctNet B4 backbone is freely [available]() and can be used for inference on satellite images of size 512x512 and a resolution between 0.5m-1m per pixel. Higher resolution usually results in better performance. The code for model training and evaluation can be found in [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](). 

### Without TTA
| Metric | Bareland | Rangeland | Developed Space | Road | Tree | Water | Agriculture | Building | Avg.|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| IoU    | 53.70 | 53.82 | 56.21 | 62.09 | 69.44 | 85.49 | 77.74 | 79.85 | 67.29 |
| F1 score | 0.70 | 0.70| 0.72 | 0.77 | 0.82 | 0.92 | 0.87 | 0.89 |0.80 |

### With TTA
| Metric | Bareland | Rangeland | Developed Space | Road | Tree | Water | Agriculture | Building | Avg.|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| IoU    | 53.70 | 53.82 | 56.21 | 62.09 | 69.44 | 85.49 | 77.74 | 79.85 | 67.29 |
| F1 score | 0.70 | 0.70| 0.72 | 0.77 | 0.82 | 0.92 | 0.87 | 0.89 |0.80 |




