# Finetuned RetinaFace with Masked Images

This repository provides codes to finetune and evaluate [RetinaFace: Single-stage Dense Face Localisation in the Wild](https://arxiv.org/abs/1905.00641) with masked images. Official codes and baseline codes for PyTorch can be found below links:

- https://github.com/deepinsight/insightface
- https://github.com/biubug6/Pytorch_Retinaface


## Performances for WiderFace Dataset

| Style | easy | medium | hard |
|:-|:-:|:-:|:-:|
| Original Model (original images with Mxnet) | 88.67% | 87.09% | 80.99% |
| Original Model (original images) | 90.70% | 88.16% | 73.82% |
| Original Model (masked images) | 91.41% | 89.72% | 80.30% |
| Finetuned Model (original images, epoch 2) | 89.83% | 87.54% | 71.18% |
| Finetuned Model (masked images, epoch 2) | 92.21% | 90.25% | 79.28% |


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
