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

The model was trained in Keras and most of the hyperparameters are used as suggested by [Xia et al. 2022](https://arxiv.org/abs/2210.10732). The model's performance is shown in the tables bellow and correspond to the one found in the original paper. The pre-trained U-Net model with EfficenctNet B4 backbone is freely [available](https://drive.google.com/drive/folders/1RpSzPsDdSzjjmkW5vWdEOsx1bC4Tdy77?usp=sharing) and can be used for inference on satellite images of size 512x512 and a resolution between 0.5m-1m per pixel [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sebastianbahr/OpenEarthMap/blob/main/OpenEarthMap_inference.ipynb). Higher resolution usually results in better performance. The code for model training and evaluation can be found in [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sebastianbahr/OpenEarthMap/blob/main/OpenEarthMap_image_segmentation.ipynb). 

### Without TTA
| Metric | Bareland | Rangeland | Developed Space | Road | Tree | Water | Agriculture | Building | Avg.|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| IoU    | 53.70 | 53.82 | 56.21 | 62.09 | 69.44 | 85.49 | 77.74 | 79.85 | 67.29 |
| F1 score | 0.70 | 0.70| 0.72 | 0.77 | 0.82 | 0.92 | 0.87 | 0.89 |0.80 |

### With TTA
| Metric | Bareland | Rangeland | Developed Space | Road | Tree | Water | Agriculture | Building | Avg.|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| IoU    | 57.96 | 56.13 | 58.09 | 64.85 | 70.57 | 86.04 | 79.82 | 80.92 | 69.30 |
| F1 score | 0.730 | 0.719| 0.735 | 0.787 | 0.827 | 0.925 | 0.887 | 0.895 |0.813 |

<img src="https://github.com/sebastianbahr/OpenEarthMap/blob/main/images/confusion_matrix.png" alt="Confusion matrix 1" class="center" style="margin: 0px 0px 0px 0px; padding: 2px 2px 2px 2px;" width="800" height="800"/>

### With TTA only in developed countries
| Metric | Bareland | Rangeland | Developed Space | Road | Tree | Water | Agriculture | Building | Avg.|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| IoU    | 45.59 | 54.96 | 55.19 | 64.72 | 73.73 | 88.62 | 83.42 | 80.54 | 68.31 |
| F1 score | 0.604 | 0.709| 0.711 | 0.786 | 0.847 | 0.940 | 0.909 | 0.892 |0.800 |

<img src="https://github.com/sebastianbahr/OpenEarthMap/blob/main/images/confusion_matrix_dev.png" alt="Confusion matrix 2" class="center" style="margin: 0px 0px 0px 0px; padding: 2px 2px 2px 2px;" width="800" height="800"/>


