# SSD_ResNet_Pytorch
[SSD](https://arxiv.org/pdf/1512.02325.pdf): Single Shot MultiBox Detector

This is a repositories that replaced the primary network(VGG) in an SSD paper with Resnet.

# Getting Started
Download git and dataset
```Shell
git clone https://github.com/cjf8899/SSD_ResNet_Pytorch.git

cd SSD_ResNet_Pytorch

wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCtrainval_06-Nov-2007.tar
tar xvf VOCtrainval_06-Nov-2007.tar
mv ./VOCdevkit ./VOCtrainval2007

wget http://host.robots.ox.ac.uk/pascal/VOC/voc2012/VOCtrainval_11-May-2012.tar
tar xvf VOCtrainval_11-May-2012.tar
mv ./VOCdevkit ./VOCtrainval2012

wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCtest_06-Nov-2007.tar
tar xvf VOCtest_06-Nov-2007.tar
mv ./VOCdevkit ./VOCtest2007
```

the structures would like
```
~/VOCtrainval2007/
    -- VOC2007
~/VOCtrainval2012/
    -- VOC2012  
~/VOCtest2007/
    -- VOC2007  
```
#Train
pre-train [VGG](https://s3.amazonaws.com/amdegroot-models/vgg16_reducedfc.pth) weights

pre-train [ResNet18](https://download.pytorch.org/models/resnet18-5c106cde.pth) weights

```
mkdir weights
cd weights
wget https://s3.amazonaws.com/amdegroot-models/vgg16_reducedfc.pth
wget https://download.pytorch.org/models/resnet18-5c106cde.pth
```

#Results

|              Implementation              |     mAP     |
| :--------------------------------------: | :---------: |
| ssd paper |    77.2    |
|    this repo - VGG   | 78.9 |
|    this repo - ResNet18   | 70.1 |

The ssd paper used Xavier after the base network(VGG), but did not use Xavier because this repo used relu.
