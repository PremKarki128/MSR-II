# MSR-II/III

# Metadata
## A reproducation as part of MSR course ar MSR course 2020/21 at UniKo, CS department, SoftLang Team
### Machine Learning Based Recommendation of Method Names: How Far Are We.
### [DBLP link:https://dblp.org/rec/conf/kbse/JiangLJ19.html]( https://dblp.org/rec/conf/kbse/JiangLJ19.html)

# Requirements
## Hardware:
### Requirement define by Auther
```
- For preprocessing the Data: Multicore System is required 
- System with GPU is recommended but CPU also fine.
```
### Used System 
- Core i5-7300HQ Quad-Core Prozessor
- 8GB RAM
- NVIDIA GeForce GTX 1050Ti Graphic
## Software:
### Requirements Define by Auther
Ubuntu System:
  - Python version 3.5 or newer 
  - TensorFlow version 1.5 or newer 
  - For GPU system : cuDNN version 0.7 or latest

### Used System
 - Windows Subsystem for Linux 20.04 on Window 10
 - Python Version: 3.8.5
 - TensorFlow Version: 2.4.1


# Process
Initial Step: Clone the repository 
```
git clone https://github.com/PremKarki128/MSR-II
cd MSR-II/Process
```


**Note:Acknowledgement for reproduction test** 
```
For observing how it works better to escape the preprocessing and training a model which is going to take a 
lot of time, so you can start from the Evaluation steps after downloading the preprocess datasets. 
```
- **Step 1: Creating Data Sets**
The new data set is downloaded from the Authers given link wich need to preprocess. (Compressed: 408MB Extracted :2,4GB)
```
wget https://s3.amazonaws.com/code2seq/datasets/java-med.tar.gz
tar -xvzf java-med.tar.gz
source preprocess.sh
```
#### OR
̴~~_Download the preprocess data from the Authers given link which contain training, test and validation datasets(compressed:6.2GB Extracted: 32GB)~~_
```
wget https://s3.amazonaws.com/code2vec/data/java14m_data.tar.gz
tar -xvzf java14m_data.tar.gz
```
Download java-Small size dataset (compressed: 366MB, extracted 1.9GB) 
```
wget https://s3.amazonaws.com/code2vec/data/java-small_data.tar.gz
tar -xvzf java-small_data.tar.gz
```
- **Step 2: Training a Model**
For training the model from initial level we need to edit the file common.py to configuration of hyper-parameters and train.sh file to point the right preprocess "java14m" data set then need to run train.sh script.
```
source train.sh
```
#### OR
Download the Authers trained model(1.4GB) which is trainined a model for 8epochs on dat
```
wget https://s3.amazonaws.com/code2vec/model/java14m_model.tar.gz
tar -xvzf java14m_model.tar.gz
```

- **Step 3: Evaluating the Model**
After the training we can use the test datasets to check how the model is functioning. While evaluating "log.txt" is written which contain the example and predicted results. To evaluate Run 
```
python3 code2vec.py --load models/java14_model/saved_model_iter8 --test data/java14m/java14m.test.c2v
```

- **Step 4: Manual Examination**
Load the model by the following comman, follow the instruction and edit the input.java and enter the java method or code snippet and examine the model's prediction.
```
python3 code2vec.py --load models/java14_model/saved_model_iter8 --predict
```
# Data
Source of the data:  downloaded from the Authers provided Link
#### INPUT DATA
- [java-med](https://s3.amazonaws.com/code2seq/datasets/java-med.tar.gz) consists of three categories of test, training and validation data with numerious files and folder
- [java14m_data](https://s3.amazonaws.com/code2vec/data/java14m_data.tar.gz) consit of dictionaries, test, train and validation datasets with C2V file system.
#### temporary Data
- java-med.train.raw.txt, java-med.val.raw.txt and java-med.test.raw.txt file is created during the preprocessing which is deleted if the complete the process without the distribunce and bug free.
#### Output Data
- My_dataset.test,  My_dataset.train,  My_dataset.val and  My_dataset.dict is created with the C2V file formate after running the preprocess.sh inside the folder Data/my_dataset.
- log.txt is created during the evaluation of the process wich consist of methods name and prediction my the train model.
<center style="padding: 40px"><img width="70%" src="https://github.com/PremKarki128/MSR-II/blob/master/Process/Image/orginalVspredic.png" title="Log file of the Evaluation" /><img width="70%" src="https://github.com/PremKarki128/MSR-II/blob/master/Process/Image/evaluationfinal.png" title="Log data of the Evaluation process" /></center>

# Delta
The reproduction of whole paper is large and tedious projects which is not fesible for my using hardware and time frame. I had reproduced the Evaluated Approach only. The Evaluated Approach is based on the Mechine Learning based recommendation of methods name Code2vec. The process of reproduction is started with the cloning the repository [Method-Name-Recommendation/HeMa, 2019](https://github.com/Method-Name-Recommendation/HeMa) which is created by the Authers for reproduction procedure. The some of the package which are required are also clone from the Authers resources of the the code2vec:"A neural network for learning distributed representations of code" which is available [github repository](https://github.com/tech-srl/code2vec) 

### Process Delta:
The replication process almost flow the complete process of the paper in the Evaluated Approach. Although we try to preprocess the data java-med by runing preprocess.py, got the error after running for more than 10 hours. Extraction of the paths of the file for test and validation data is completed about an hour but for training floder execute for more then 9 hours and terminate with the error message "Cat: Write error: Broken pipe". Training of the model take about 15 hours and the size of the model is very large and not possible to share by using the internet network.The size of the 8 epochs train model performed by the Auther is 1.4 GB which took 17 minute to evalute the test dataset with the **precision: 0.659, recall:0.531 and F1 0.588 score.**

### Data Delta
The two source of data [java-med](https://s3.amazonaws.com/code2seq/datasets/java-med.tar.gz) and [java14m_data](https://s3.amazonaws.com/code2vec/data/java14m_data.tar.gz) is used which is provided by the Auther. The java-med is not preprocess which we tried to process but we were not able to completed produce the final result due to some bug and hardware failier. The java14m_data is preprocess data which is used for the training and evaluation approach of the models. 

### Problem Delta:
- I am not able to estimate complexity  of the problem domain of the reproduction of the technical parts of the paper and claim the reproduction task alone which make me more difficult to figure out the problem and bug in the process and coding and took longer time than the estimate and only able to complete the Evaluated Approach.
- The hardware required for the task is not enough due to which I need to terminate the preprocessing task after runnig for the more than 10 hours without the results.
- The training processing took more than required time  and terminate without complition.
<center style="padding: 40px"><img width="70%" src="https://github.com/PremKarki128/MSR-II/blob/master/Process/Image/ErrorResult2.png" title="Error occure due to hardware failier" /> <img width="70%" src="https://github.com/PremKarki128/MSR-II/blob/master/Process/Image/ErrorTraingdata.png" title="Error occure due to core dumped" /></center>



