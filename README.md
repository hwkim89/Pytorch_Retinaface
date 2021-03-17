# Finetuned RetinaFace with Masked Images

This repository provides codes to finetune and evaluate [RetinaFace: Single-stage Dense Face Localisation in the Wild](https://arxiv.org/abs/1905.00641) with masked images. Official codes and baseline codes for PyTorch can be found below links:

- https://github.com/deepinsight/insightface
- https://github.com/biubug6/Pytorch_Retinaface


## Performances for WiderFace Dataset

| Style | easy | medium | hard |
|:-|:-:|:-:|:-:|
| Original Model (same parameter with Mxnet) | 88.67% | 87.09% | 80.99% |
| Original Model (original image scale) | 90.70% | 88.16% | 73.82% |
| Finetuned Model (original image scale) | - | - | - |


## Training

```Shell
python train.py --train_dir ./data/widerface/train/masked_images --resume_net ./weights/mobilenet0.25_Final_ori.pth
```


## References

- [Retinaface (MXNet)](https://github.com/deepinsight/insightface)
- [RetinaFace (PyTorch)](https://github.com/biubug6/Pytorch_Retinaface)
