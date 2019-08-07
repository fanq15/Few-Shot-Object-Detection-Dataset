# Few-Shot-Object-Detection-Dataset
- **Introduction**:

  Few-Shot Object Detection Dataset (FSOD) is a high-diverse dataset specifically designed for few-shot object detection and intrinsically designed to evaluate thegenerality of a model on novel categories. 
  
  To build this dataset, we first summarize a label system from ImageNet and OpenImage. By merging the leaf labels in their original label trees, group those of same semantics, such as the ice bear and polar bear, to one category, and remove some semantics that does not belong to any leaf categories. Then, we remove the images with bad labeling quality and those with boxes of improper size. We remove boxes smaller than 0.05% of image size which is usually in bad visual quality and unsuitable to serve as support examples. 

  We follow the few-shot learning principle to split our data into the training set and test set whose categories has no overlap. We construct the training set with categories in MS COCO Dataset and ImageNet Dataset in case researchers need a pretraining stage. We then split the test set which contains 200 categories by choosing those with the largest distance with existing training categories, where the distance calculates the shortest path that connects the senses of two phrase in the is-a taxonomy. The remaining categories are merged into the training set that in total contains 800 categories. In all, we construct a dataset of 1000 categories with very clear category split for training and testing, where 531 categories come from ImageNet Dataset and 469 from Open Image Dataset.


- **Download FSOD**:

  Download the images and annotations from [FSOD](https://drive.google.com/drive/folders/1XXADD7GvW8M_xzgFpHfudYDYtKtDgZGM?usp=sharing).

  Make a `YOUR_PATH/fsod/all_images` folder and put the files as the following structure:
  ```
  YOUR_PATH
      ├── code
      │     ├── training scripts
      │     ├── testing scripts
      │     ├── ...
      │ 
      └── fsod
            ├── all_images
            |       ├── fsod_train_df.pkl
            │       ├── fsod_test_df.pkl
            │       ├── part_1
            │       └── part_2
            |
            ├── train_converter.py
            └── test_converter.py
  ```  

- **Dataset Convert**:

  You need to use the `train_converter.py` and `test_converter.py` convert the `pkl` annotatinos files to `json` (Pascal VOC format) by running the following script. 
  
  
  Generate `train.json` in the `fsod` folder:
  ```
  python3 train_converter.py --data_path YOUR_PATH
  ```
  
  
  Generate `test.json` and `val.txt` in the `fsod` folder:
  ```
  python3 test_converter.py --data_path YOUR_PATH
  ```

    
  You need to put the `fsod` folder in the `YOUR_PATH` folder and run your training or testing script in the `YOUR_PATH/code` foler. (It will change the `file_name` in the json to `YOUR_PATH/fsod/all_images/IMAGE_NAME`, and it is actually the path where the code imports the training/testing image.)
  
- **Dataset Summary**:


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
    
- **Contact**:

  This dataset is maintained by Qi Fan (Tencent Youtu Lab, fanq15@gmail.com), Wei Zhuo (Tencent Youtu Lab, wei.zhuowx@gmail.com) and Yu-Wing Tai (Tencent Youtu Lab, yuwingtai@tencent.com) 

## Citation

  If you use this dataset in your research, please cite this paper.

  ```
  @article{fan2019fsod,
    title={Few-Shot Object Detection with Attention-RPN and Multi-Relation Detector},
    author={Fan, Qi and Wei, Zhuo and Tai, Yu-Wing},
    journal={arXiv preprint arXiv:1908.01998},
    year={2019}
  }
  ```
