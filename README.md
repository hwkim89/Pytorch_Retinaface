# Finetuned RetinaFace with Masked Images

This repository provides codes to finetune and evaluate [RetinaFace: Single-stage Dense Face Localisation in the Wild](https://arxiv.org/abs/1905.00641) with masked images. Official codes and baseline codes for PyTorch can be found below links:

- https://github.com/deepinsight/insightface
- https://github.com/biubug6/Pytorch_Retinaface


## Performances for WiderFace Dataset

### Original Image

Finetuned Models were evaluated in different epochs and confidence scores by the validation dataset.

| Style | easy | medium | hard |
|:-|:-:|:-:|:-:|
| Original Model (Mxnet) | 88.67% | 87.09% | 80.99% |
| Original Model (conf 0.02) | 90.70% | 88.16% | 73.82% |
| Finetuned Model (conf 0.02) | 89.53% | 87.07% | 70.24% |
| Original Model (conf 0.6) | 88.26% | 83.95% | 58.15% |
| Finetuned Model (conf 0.6) | 87.48% | 83.26% | 55.22% |

### Masked Image
| Style | easy | medium | hard |
|:-|:-:|:-:|:-:|
| Original Model (conf 0.02) | 91.41% | 89.72% | 80.30% |
| Finetuned Model (conf 0.02) | 92.22% | 90.32% | 78.30% |
| Original Model (conf 0.6) | 88.03% | 84.43% | 67.58% |
| Finetuned Model (conf 0.6) | 90.53% | 86.95% | 68.39% |


## Finetuning

```Shell
python train.py --train_dir ./data/widerface/train/masked_images --resume_net ./weights/mobilenet0.25_Final_ori.pth
```

## Evaluation

### Generate txt files

#### Orginal Image
```Shell
python test_widerface.py --trained_model ./weights/mobilenet0.25_Final.pth --network mobile0.25 --dataset_folder ./data/widerface/val/images/
```

#### Masked Image
```Shell
python test_widerface.py --trained_model ./weights/mobilenet0.25_Final.pth --network mobile0.25 --dataset_folder ./data/widerface/val/masked_images/
```

### Evaluate txt reulsts

```Shell
cd ./widerface_evaluate
python setup.py build_ext --inplace
```

#### Original Image
```Shell
python evaluation.py
```

#### Masked Image
```Shell
python evaluation.py --masked
```


## References

- [RetinaFace (MXNet)](https://github.com/deepinsight/insightface)
- [RetinaFace (PyTorch)](https://github.com/biubug6/Pytorch_Retinaface)
