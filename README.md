# Few-Shot-Object-Detection-Dataset

- **Download FSOD**:

  Download the images and annotations from [FSOD](https://drive.google.com/drive/folders/1XXADD7GvW8M_xzgFpHfudYDYtKtDgZGM?usp=sharing).

  Make a `YOUR_PATH/data/all_images` folder and put the files as the following structure:
  ```
  YOUR_PATH
      ├── code
      │     ├── training scripts
      │     ├── testing scripts
      │     ├── ...
      │ 
      └── data
            ├── all_images
            |       ├── fsod_train_df_v3.pkl
            │       ├── fsod_test_df_v3.pkl
            │       ├── imagenet
            │       └── openimage
            |
            └── train_converter.py
            └── test_converter.py
  ```  

- **Dataset Convert**:

  You need to use the `train_converter.py` and `test_converter.py` convert the `pkl` annotatinos files to `json` (Pascal VOC format) by running the following script. 
  
  
  Generate `train.json` in the `data` folder:
  ```
  python3 train_converter.py --data_path YOUR_PATH
  ```
  
  
  Generate `test.json` and `val.txt` in the `data` folder:
  ```
  python3 test_converter.py --data_path YOUR_PATH
  ```

    
  You need to put the `data` folder in the `YOUR_PATH` folder and run your training or testing script in the `YOUR_PATH/code` foler. (It will change the `file_name` in the json to `YOUR_PATH/data/all_images/IMAGE_NAME`, and it is actually the path where the code imports the training/testing image.)
  
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
