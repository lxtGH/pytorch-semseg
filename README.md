# pytorch-semseg
# Goal: read code line from dataloader, model , trainning, and evaluation code

[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/meetshah1995/pytorch-semseg/blob/master/LICENSE)
[![pypi](https://img.shields.io/pypi/v/pytorch_semseg.svg)](https://pypi.python.org/pypi/pytorch-semseg/0.1.2)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.1185075.svg)](https://doi.org/10.5281/zenodo.1185075)



## Semantic Segmentation Algorithms Implemented in PyTorch

This repository aims at mirroring popular semantic segmentation architectures in PyTorch. 


<p align="center">
<a href="https://www.youtube.com/watch?v=iXh9aCK3ubs" target="_blank"><img src="https://i.imgur.com/agvJOPF.gif" width="364"/></a>
<img src="https://meetshah1995.github.io/images/blog/ss/ptsemseg.png" width="49%"/>
</p>


### Networks implemented

* [PSPNet](https://arxiv.org/abs/1612.01105) - With support for loading pretrained models w/o caffe dependency
* [FRRN](https://arxiv.org/abs/1611.08323) - Model A and B
* [FCN](https://arxiv.org/abs/1411.4038) - All 1 (FCN32s), 2 (FCN16s) and 3 (FCN8s) stream variants
* [U-Net](https://arxiv.org/abs/1505.04597) - With optional deconvolution and batchnorm
* [Link-Net](https://codeac29.github.io/projects/linknet/) - With multiple resnet backends
* [Segnet](https://arxiv.org/abs/1511.00561) - With Unpooling using Maxpool indices


#### Upcoming 

* [E-Net](https://arxiv.org/abs/1606.02147)
* [RefineNet](https://arxiv.org/abs/1611.06612)

### DataLoaders implemented

* [CamVid](http://mi.eng.cam.ac.uk/research/projects/VideoRec/CamVid/)
* [Pascal VOC](http://host.robots.ox.ac.uk/pascal/VOC/voc2012/segexamples/index.html)
* [ADE20K](http://groups.csail.mit.edu/vision/datasets/ADE20K/)
* [MIT Scene Parsing Benchmark](http://data.csail.mit.edu/places/ADEchallenge/ADEChallengeData2016.zip)
* [Cityscapes](https://www.cityscapes-dataset.com/)
* [NYUDv2](http://cs.nyu.edu/~silberman/datasets/nyu_depth_v2.html)
* [Sun-RGBD](http://rgbd.cs.princeton.edu/)


### Requirements

* pytorch >=0.3.0
* torchvision ==0.2.0
* visdom >=1.0.1 (for loss and results visualization)
* scipy
* tqdm

#### One-line installation
    
`pip install -r requirements.txt`

### Data

* Download data for desired dataset(s) from list of URLs [here](https://meetshah1995.github.io/semantic-segmentation/deep-learning/pytorch/visdom/2017/06/01/semantic-segmentation-over-the-years.html#sec_datasets).
* Extract the zip / tar and modify the path appropriately in `config.json`


### Usage

Launch [visdom](https://github.com/facebookresearch/visdom#launch) by running (in a separate terminal window)

```
python -m visdom.server
```

**To train the model :**

```
python train.py [-h] [--arch [ARCH]] [--dataset [DATASET]]
                [--img_rows [IMG_ROWS]] [--img_cols [IMG_COLS]]
                [--n_epoch [N_EPOCH]] [--batch_size [BATCH_SIZE]]
                [--l_rate [L_RATE]] [--feature_scale [FEATURE_SCALE]]
                [--visdom [VISDOM]]

  --arch           Architecture to use ['fcn8s, unet, segnet etc']
  --dataset        Dataset to use ['pascal, camvid, ade20k etc']
  --img_rows       Height of the input image
  --img_cols       Width of the input image
  --n_epoch        # of the epochs
  --batch_size     Batch Size
  --l_rate         Learning Rate
  --feature_scale  Divider for # of features to use
  --visdom         Show visualization(s) on visdom | False by default
```

**To validate the model :**

```
python validate.py [-h] [--model_path [MODEL_PATH]] [--dataset [DATASET]]
                   [--img_rows [IMG_ROWS]] [--img_cols [IMG_COLS]]
                   [--batch_size [BATCH_SIZE]] [--split [SPLIT]]

  --model_path   Path to the saved model
  --dataset      Dataset to use ['pascal, camvid, ade20k etc']
  --img_rows     Height of the input image
  --img_cols     Width of the input image
  --batch_size   Batch Size
  --split        Split of dataset to validate on
```

**To test the model w.r.t. a dataset on custom images(s):**

```
python test.py [-h] [--model_path [MODEL_PATH]] [--dataset [DATASET]]
               [--dcrf [DCRF]] [--img_path [IMG_PATH]] [--out_path [OUT_PATH]]
 
  --model_path          Path to the saved model
  --dataset             Dataset to use ['pascal, camvid, ade20k etc']
  --dcrf                Enable DenseCRF based post-processing
  --img_path            Path of the input image
  --out_path            Path of the output segmap
```


**If you find this code useful in your research, please consider citing:**

```
@article{mshahsemseg,
    Author = {Meet P Shah},
    Title = {Semantic Segmentation Architectures Implemented in PyTorch.},
    Journal = {https://github.com/meetsahh1995/pytorch-semseg},
    Year = {2017}
}
```

