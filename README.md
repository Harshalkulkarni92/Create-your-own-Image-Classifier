# Create-your-own-Image-Classifier
Deep Learning

## Image Classifier

Going forward, AI algorithms will be incorporated into more and more everyday applications. For example, you might want to include an 
image classifier in a smartphone app. To do this, you'd use a deep learning model trained on hundreds of thousands of images as part of 
the overall application architecture. A large part of software development in the future will be using these types of models as common 
parts of applications.

In this project, you'll train an image classifier to recognize different species of flowers. You can imagine using something like this 
in a phone app that tells you the name of the flower your camera is looking at. In practice, you'd train this classifier, then export it 
for use in your application. We'll be using this dataset of 102 flower categories.

Its an attempt to build an application that can be trained on any set of labelled images. Here your network will 
be learning about flowers and end up as a command line application. 

## Prerequisties 

The Code is written in Python 3.6.5 . 
Additional Packages that are required are: Numpy, Pandas, MatplotLib, Pytorch, PIL and json.
In order to intall Pytorch head over to the Pytorch site select your specs and follow the instructions given.

## Command Line Argument

•  Train a new network on a data set with train.py
    Basic Usage : python train.py data_directory
    Prints out current epoch, training loss, validation loss, and validation accuracy as the netowrk trains
    Options:
    
              Set direcotry to save checkpoints: python train.py data_dor --save_dir save_directory
              Choose arcitecture (alexnet, densenet121 or vgg16 available): pytnon train.py data_dir --arch "vgg19"
              Set hyperparameters: python train.py data_dir --learning_rate 0.001 --hidden_layer1 120 --epochs 20
              Use GPU for training: python train.py data_dir --gpu gpu
              
•  Predict flower name from an image with predict.py along with the probability of that name. 
   That is you'll pass in a single image /path/to/image and return the flower name and class probability

     Basic usage: python predict.py /path/to/image checkpoint
     Options:
        Return top K most likely classes: python predict.py input checkpoint ---top_k 3
        Use a mapping of categories to real names: python predict.py input checkpoint --category_names cat_To_name.json
        Use GPU for inference: python predict.py input checkpoint --gpu
  
 
## GPU

• As the network makes use of a sophisticated deep convolutional neural network the training process is impossible to be done by a 
common laptop. In order to train your models to your local machine you have three options

  1. Cuda -- If you have an NVIDIA GPU then you can install CUDA from here. With Cuda you will be able to train your model however 
     the process will still be time consuming
  2. Cloud Services -- There are many paid cloud services that let you train your models like AWS or Google Cloud
  3. Coogle Colab -- Google Colab gives you free access to a tesla K80 GPU for 12 hours at a time. Once 12 hours have ellapsed you 
     can just reload and continue! The only limitation is that you have to upload the data to Google Drive and if the dataset is massive you may run out of space.

However, once a model is trained then a normal CPU can be used for the predict.py file and you will have an answer within some seconds.

## JSON 

In order for the network to print out the name of the flower a .json file is required. By using a .json file the data can be sorted 
into folders with numbers and those numbers will correspond to specific names specified in the .json file. The json file is not in the 
repository. 

## Data and the json file

The data used specifically for this assignemnt are a flower database are not provided in the repository  as it's larger than what github
allows. Nevertheless, feel free to create your own databases and train the model on them to use with your own projects. The structure 
of your data should be the following:
  • The data need to comprised of 3 folders, test, train and validate. Generally the proportions should be 70% training 10% validate 
   and 20% test.
  • Inside the train, test and validate folders there should be folders bearing a specific number which corresponds to a specific 
    category, clarified in the json file. For example if we have the image a.jpj and it is a rose it could be in a path like 
    this /test/5/a.jpg and json file would be like this {...5:"rose",...}. Make sure to include a lot of photos of your 
    catagories (more than 10) with different angles and different lighting conditions in order for the network to generalize better.
    
    
## Hyperparameters

As you can see you have a wide selection of hyperparameters available and you can get even more by making small modifications to the 
code. Thus it may seem overly complicated to choose the right ones especially if the training needs at least 15 minutes to be completed.
So here are some hints:

  • By increasing the number of epochs the accuracy of the network on the training set gets better and better however be careful because
    if you pick a large number of epochs the network won't generalize well, that is to say it will have high accuracy on the training 
    image and low accuracy on the test images. Eg: training for 12 epochs training accuracy: 85% Test accuracy: 82%. Training for 30 
    epochs training accuracy 95% test accuracy 50%.
  • A big learning rate guarantees that the network will converge fast to a small error but it will constantly overshot
  • A small learning rate guarantees that the network will reach greater accuracies but the learning process will take longerò
  • Densenet121 works best for images but the training process takes significantly longer than alexnet or vgg19
  
  
## Pre-Trained Network

The checkpoint.pth file contains the information of a network trained to recognise 102 different species of flowers. 
It has been trained with specific hyperparameters thus if you don't set them right the network will fail. In order to have a prediction
for an image located in the path /path/to/image using my pretrained model you can simply type python predict.py /path/to/image checkpoint.pth
This file is not present in the repository.



