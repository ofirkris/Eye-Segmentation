# RITnet
Demonstration of the winning model for Facebook OpenEDS semantic segmentation challenge, which achieves a highly accurate (95.3%) within a limited size (0.98 MB).

If you use this code, please cite:

@INPROCEEDINGS{chaudhary2019ritnet,
author={A. K. {Chaudhary} and R. {Kothari} and M. {Acharya} and S. {Dangi} and N. {Nair} and R. {Bailey} and C. {Kanan} and G. {Diaz} and J. B. {Pelz}},
booktitle={2019 IEEE/CVF International Conference on Computer Vision Workshop (ICCVW)},
title={RITnet: Real-time Semantic Segmentation of the Eye for Gaze Tracking},
year={2019},
volume={},
number={},
pages={3698-3702},
keywords={Semantics;Image segmentation;Computational modeling;Iris;Robustness;Convolution;Real-time systems},
doi={10.1109/ICCVW.2019.00568},
ISSN={2473-9936},
month={Oct},}
Instructions:

python train.py —help

To train the model with densenet model:

python train.py —model densenet —expname FINAL —bs 8 —useGPU True —dataset Semantic_Segmentation_Dataset/

To test the result:

python test.py —model densenet —load best_model.pkl —bs 4 —dataset Semantic_Segmentation_Dataset/

Contents in the zip folder
best_model.pkl :: Our final model (potential winner model) which contains all the weights in Float32 format (Number of Parameters 248900).
requirements.txt :: Includes all the necessary packages for the source code to run
environment.yml :: List of all packages and version of one of our system in which the code was run successfully.
dataset.py ::Data loader and augmentation
train.py ::Train code
test.py ::Test code
densenet.py ::Model code
utils.py ::List of utility files
opt.py ::List of arguments for argparser
models.py ::List of all models
starburst_black.png:: A fixed structured pattern (with translation) used on train images to handle cases such as multiple reflections.(Train Image: 000000240768.png)
Starburst generation from train image 000000240768.pdf ::Procedure how starburst pattern is generated
The requirements.txt file contains all the packages necessary for the code to run. We have also included an environment.yml file to recreate the conda environment we used.

We have submitted two models from this version of code:

Epoch: 151 Validation accuracy: 95.7780 Test accuracy: 95.276 (Potential Winner Model: Last Submission)
Epoch: 117 Validation accuracy: 95.7023 Test accuracy: 95.159 (Our Second Last Submission)
We could reach upto Epoch: 240 Validation accuracy: 95.7820 Test accuracy:NA (Not submitted: result after the deadline)

The dataset.py contains data loader, preprocessing and post processing step Required Preprocessing for all images (test, train and validation set).

Gamma correction by a factor of 0.8
local Contrast limited adaptive histogram equalization algorithm with clipLimit=1.5, tileGridSize=(8,8)
Normalization [Mean 0.5, std=0.5]
Train Image Augmentation Procedure Followed (Not Required during test)

Random horizontal flip with 50% probability.
Starburst pattern augmentation with 20% probability.
Random length lines (1 to 9) augmentation around a random center with 20% probability.
Gaussian blur with kernel size (7,7) and random sigma (2 to 7) with 20% probability.
