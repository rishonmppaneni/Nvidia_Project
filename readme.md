Skin Cancer Image Classification

This project is an image classification model that classifies skin cancer images into either being benign or malignant.

![add image descrition here](https://getlabtest-assets-prod.s3.amazonaws.com/media/original_images/benign-malignant-tumors-illustration-comparison-56832.webp)
## The Algorithm

I downloaded the skin cancer dataset from Kaggle and the images were classified into 2 distinct categories(malignant and benign). Once I downloaded the dataset, it already contained test and train folders but was missing a validation folder. I took 80% of the images for training, 15% for validation, and 5% for testing. I then used a pretrained resnet-18 model to train my dataset. I was getting a good accuracy of 80% for the training and validation. My model did a good job in predicting the benign images, but it did struggle a little to predict the malignant images. My model did fairly decent and is reliable, however if someone were to use this model, they shouldn't rely on it to be 100% accurate all the time. One should check to see how it is performing from time to time and it can be used for fairly good purposes. 
## Running this project

#Setup
1. Install Jetson Inference
git clone --recursive https://github.com/dusty-nv/jetson-inference
cd jetson-inference
mkdir build
cd build
cmake ../
make
sudo make install
2. Prepare Dataset
Organize images like this:

jetson-inference/python/training/classification/data/recycling_waste-products/
├── train/
│   ├── benign/
│   ├── malignant/
├── val/
└── test/

3. Training
Enable more memory: echo 1 | sudo tee /proc/sys/vm/overcommit_memory
Train the model (I used 55 epochs)
cd jetson-inference
./docker/run.sh
cd python/training/classification
python3 train.py --model-dir=models/finalv1 data/Cancer
Export Model
# Still in docker container:
python3 onnx_export.py --model-dir=models/finalv1
Using the Model
Set Variables



[View a video explanation here](https://windows10spotlight.com/wp-content/uploads/2023/01/81a6e74c8adbf7f55406e8c4b80669d5.jpg)
