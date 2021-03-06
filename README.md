# CMPUT566-Project - A Study of Image Classification ML Algorithms, Including a Custom Implementation of CNNs

This repository contains the code for my final project for the UAlberta course CMPUT 466/566 Machine Learning. Three algorithms are analysed in the context of image classification, 
- K-Nearest Neighbours 
- Softmax Regression
- Convolutional Neural Network.

For the non-triviality component of the project, I have also implemented CNN layers from scratch. Thus, there are actually two models for the 3rd algorithm, one built using the PyTorch implementation and the other from the custom implementation. 

A version of the project report has been uplaoded to this repository, however the final version is the one submitted through eClass.  

## Organization

### Classification Algorithms
`classifiers` contains python files for each image classification algorithm considered. To run any of these files, for example the k-nearest neighbours algorithm, run the follwing command from the base directory,

```
python3 -m classifiers.KNN
```

For training both the PyTorch and custom CNN models, I have used the `running_with_GPU.ipynb` notebook to use the GPU provided by Google Colab. 

The custom implementation of CNN layers can be found in `./classifiers/custom_CNN_utils/layers.py`. The forward and backward passes of 5 different layers have been implemented from scratch as AutoGrad functions, and then these functions have been wrapped inside PyTorch modules so that the same API can be used to train both the PyTorch CNN and the custom CNN. 
The implemented layers are the ones commonly used in CNNs, and are the following,
- Affine 
- Convolutional
- ReLU Activation
- Batch Normalization
- Dropout.

**Other algorithms:**
Apart from the three algorithms under consideration that were studied in-depth and included in the report, I also initially tested out some other algorithms, namely SVM and Decision trees, which did not make it into the report. This is because only three models were required as per the project instructions. Still, the python scripts for both of these can be found in the `./classifiers/other_classifiers` directory. 
Also, a trivial baseline (random guessing) has also been included in the python file `./classifiers/trivial.py`.


### Saved Models
On this repository, the directories within `./saved_models` contain `.txt` files listing the validation set accuracies for different choices of hyperparameters. These files were obtained during the hyperparameter tuning phase of each model.

The models I trained and whose accuracies are quoted in the accompanying project report can be downlaoded from this [google drive link](https://drive.google.com/drive/folders/1DFSq8fYcm0zlDnGwbsVPN2esuh-hLncc?usp=sharing). If you wish to run the code with these trained models rather than training once again, 
1. Download the files (they're quite large),
2. Store them in their corresponding directories within `./saved_models`,
3. Alter the `values_calculated` flag within the appropriate classifier python file (set to True),
4. Run the classifier python file.



### Dataset
The dataset under consideration in this project is CIFAR-10. It can be downloaded by running the `download_cifar.sh` script. Running this script will save the dataset inside the `./dataset` directory.
The python file `data.py` contains utility code for loading and preprocessing the dataset. This code is implicitly called from the classifier python files.


### Evaluation
`metrics.py` contains common utility code for evaluating the performance of all ML models. 


### Miscellaneous
`consts.py` contains constants used across all python files, to ensure consistency in naming, locations, etc. 
`./plots` contains some plots obtained during hyperparameter tuning that are also included in the project report. 

