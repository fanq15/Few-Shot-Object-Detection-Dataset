# Few-Shot-Object-Detection-Dataset

## NEWS!
**Detectron2 based FSOD is released in a data-limited task toolbox [FewX](https://github.com/fanq15/FewX)! It can reach 12.0 AP on MS COCO (full-way 10-shot on voc subset).**

## Updates:
- `detectron2` based FSOD is released in a data-limited toolbox [FewX](https://github.com/fanq15/FewX)! It can reach **12.0 AP** on MS COCO (full-way 10-shot on voc subset)! (09/08/2020)
- The original code is released in [fanq15/FSOD-code](https://github.com/fanq15/FSOD-code)! (13/05/2020)
- Please forget the `detectron2` based code. I will directly release the original code recently. Very sorry for the late code release. All kinds of pressures are driving me crazy! (10/05/2020)
- The original code is based on an unofficial mask rcnn framework. It is too slow, and I am trying to transfer the code to the newest `detectron2` framework. The code is still under debugging... I only plan to release the detectron2 based code. (30/04/2020)
- The dataset is rearranged to MS COCO format for ease of use and the Baidu Driver download link is provided! (07/03/2020)
- Now I have time to process the data and code. The data will be rearranged to VOC or COCO format for the ease of use. And the Baidu Driver download link will be provided. The code will be transfered to the detectron2 framework. The data part will be done in two weeks. The code part is expected to be done before this April. (07/03/2020)

## Introduction:

  Few-Shot Object Detection Dataset (FSOD) is a high-diverse dataset specifically designed for few-shot object detection and intrinsically designed to evaluate thegenerality of a model on novel categories. 
  
  ![](https://github.com/fanq15/Few-Shot-Object-Detection-Dataset/raw/master/demo.jpg)
  
  To build this dataset, we first summarize a label system from ImageNet and OpenImage. By merging the leaf labels in their original label trees, group those of same semantics, such as the ice bear and polar bear, to one category, and remove some semantics that does not belong to any leaf categories. Then, we remove the images with bad labeling quality and those with boxes of improper size. We remove boxes smaller than 0.05% of image size which is usually in bad visual quality and unsuitable to serve as support examples. 

  We follow the few-shot learning principle to split our data into the training set and test set whose categories has no overlap. We construct the training set with categories in MS COCO Dataset and ImageNet Dataset in case researchers need a pretraining stage. We then split the test set which contains 200 categories by choosing those with the largest distance with existing training categories, where the distance calculates the shortest path that connects the senses of two phrase in the is-a taxonomy. The remaining categories are merged into the training set that in total contains 800 categories. In all, we construct a dataset of 1000 categories with very clear category split for training and testing, where 531 categories come from ImageNet Dataset and 469 from Open Image Dataset.


## Download FSOD:

  Download the images and annotations from [Google Driver](https://drive.google.com/drive/folders/1XXADD7GvW8M_xzgFpHfudYDYtKtDgZGM?usp=sharing) or [Baidu Driver](https://pan.baidu.com/s/1sfJWw-OnjAjRZTj797gl9A) (the passcode for Baidu Driver is: `wnj8`).

## FSOD Dataset Format and Usage:

  The FSOD dataset is in MS COCO format (under debug), so place the FSOD dataset as the COCO dataset. And you can use the FSOD dataset like COCO dataset.
  
  Put the FSOD dataset as the following structure:
  ```
  YOUR_PATH
      └── your code dir
            ├── your code
            ├── ...
            │ 
            └── datasets
                  ├──── fsod
                  |       ├── annotations
                  │       │       ├── fsod_train.json
                  │       │       └── fsod_test.json
                  │       └── images
                  │             ├── part_1
                  │             └── part_2
                  │ 
                  ├──── coco
                  |       ├── annotations
                  │       │       ├── instances_train2017.json
                  │       │       └── instances_val2017.json
                  │       └── images
                  │ 
                  └── other datasets
  ```  
## Dataset Summary:


|  | Train | Test |
| ---------- | :-----------:  | :-----------: |
|No. Class | 800 | 200 |
|No. Image | 52350 | 14152 |
|No. Box | 147489 | 35102 |
|Avg No. Box / Img  | 2.82 | 2.48 |
|Min No. Img / Cls  | 22 | 30 |
|Max No. Img / Cls  | 208 | 199 |
|Avg No. Img / Cls  | 75.65 | 74.31 |
|Box Size | [6, 6828] | [13, 4605] |
|Box Area Ratio | [0.0009, 1] | [0.0009, 1] |
|Box W/H Ratio | [0.0216, 89] | [0.0199, 51.5] |
    
## Contact:

  This dataset is maintained by Qi Fan (HKUST, fanqithu@gmail.com), Wei Zhuo (Tencent, wei.zhuowx@gmail.com) and Yu-Wing Tai (Tencent, yuwingtai@tencent.com) 

## Citation

  If you use this dataset in your research, please cite this [paper](https://arxiv.org/pdf/1908.01998v1.pdf).

  ```
  @inproceedings{fan2020fsod,
    title={Few-Shot Object Detection with Attention-RPN and Multi-Relation Detector},
    author={Fan, Qi and Zhuo, Wei and Tang, Chi-Keung and Tai, Yu-Wing},
    booktitle={CVPR},
    year={2020}
  }
  ```
