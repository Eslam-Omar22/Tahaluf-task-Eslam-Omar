# Tahaluf-task-Eslam-Omar

This Reposatory contains the 2 parts of the task

**The first one was:** 
To clone the repository of YoloX, and test their models to try and
reproduce their results.
I achived that by finetuning the Medium model on a custom dron dataset and all the results are attached in the notbook.

**The second part was:**:
To build a classifier for clothing articles.
The first thing I did was to find a proper dataset for the task and I found a good one on Kaggle: https://www.kaggle.com/datasets/agrigorev/clothing-dataset-full/versions/1 

**Approach**
1- Data Exporation 
The data set has 20 classes for the clothes with more than 5400 image 
After exploring the data I came up with some conclusions:
* The data had some corrupted images which I had to remove before training
* The dataset had Huge calss imbalance and some classes barely existed
* Actually this data is not good enough to show the skills but it was the only valid dataset that i could find 

2- Data preprocessing and preparation
* Mapping the image names to their pathes in the data
* Encode the labels of the class into One-Hot-Encoding Format
* I used Keras DataLoaderto load and augment the data from the dataframe and avoid any OOM erros
* Train test split step, to train and evaluate the model


3-Model Choice and Training:
* I tried several models at the begining like VGG16, ResNet50 and XceptionNet but eventually I decided to stick to VGG16 since it's much lighter than the other 2 and the results were so close between them 
* The first model I trianed was using the traing dataset for 15 epochs but it was overfitting as expected
I spent some time fine-tuning the hyper-parameters but it seemed that the data wasn't helping me at all
* I have also tried training the model again using Kfold Cross-validataion with 4 folds to try to genaralize more on the small classes and predict them well 
* I Have also tried class weighting in the training phase but also didn't solve the issue-as expected-
* The last thing that I did that I removed all calsses that are adding noise to the dataset which have samples less than 100 and retrained the model using kfold cross validataion and it improved and genralized well 

4- Model Evaluation 
* After training I evaluated the model using the Unseen testset to get good intution about the model performance
* I used the F1 score and confusion matrix to evaluate the model, and since the data was imbalnced I had to use the weighted F1 score in my evaluation.

Eventually this was the best that I could achive using this limited and noisy dataset,I've visited several approaches but this is the maximum that we can achieve using this data 
It was a fun task but the data had a second opinion :D 

The  total Flops and MAACs are reported in the notebook
