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
- **Step 1: Creating Data Sets**
The new data set is downloaded from the Authers given link wich need to preprocess. (Compressed: 408MB Extracted :2,4GB)
```
wget https://s3.amazonaws.com/code2seq/datasets/java-med.tar.gz
tar -xvzf java-med.tar.gz
source preprocess.sh
```
#### OR
Download the preprocess data from the Authers given link which contain training, test and validation datasets
```
wget https://s3.amazonaws.com/code2vec/data/java14m_data.tar.gz
tar -xvzf java14m_data.tar.gz
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


# Delta

