# Neural_Network_Charity_Analysis
## Overview
A funding association Alphabet Soup is considering whether client organizations they funded would be successful if making new investments on them. To predict the successfulness of its fundation, a binary classifier was created with machine learning and neural network. For this purpose, more than 34,000 organizations funding history record were retrieved to build the neural network model. The model building including following steps:
- Preprocess data for a Nneural network model.
- Compile, train, evaluate the model and save the model weights.
- Optimize the model.


## Result
### Data Preprocessing
- Dataset 
   ![application_df_dataset](https://user-images.githubusercontent.com/105877888/193479397-4c2bc777-f207-4497-a121-c174f0c38fe6.png) 
    ```
    EIN and NAME-------------------------------- Identification columns
    APPLICATION_TYPE---------------------------- Alphabet Soup application type
    AFFILIATION -------------------------------- Affiliated sector of industry
    CLASSIFICATION ----------------------------- Government organization classification
    USE_CASE ----------------------------------- Use case for funding
    ORGANIZATION ------------------------------- Organization type
    STATUS ------------------------------------- Active status
    INCOME_AMT --------------------------------- Income classification
    SPECIAL_CONSIDERATIONS --------------------- Special consideration for application
    ASK_AMT ------------------------------------ Funding amount requested
    IS_SUCCESSFUL ------------------------------ Was the money used effectively
    ```

- Target variable: 
  **IS_SUCCESSFUL**.
  It stands for whether the applicants were successful or not.
  Binary values: **1**-successful, **0**-unsuccessful. 
- Unrelated variables:
  **EIN** and **NAME**.
  These are ID columns, can be removed from the input data.
- Features: 
  **APPLICATION_TYPE**, **AFFILIATION**, **CLASSIFICATION**, **USE_CASE**, **ORGANIZATION**, **STATUS**, **INCOME_AMT**, 
  **SPECIAL_CONSIDERATIONS**, **ASK_AMT**. These variables potentionally affect applicant's use of funds.
  - Categorical features:
    - **APPLICATION_TYPE** ----->  17 unique values, bucketing into 9. Then encoded.
    - **AFFILIATION** -----> 6 unique values, Encoded.
    - **CLASSIFICATION** -----> 17 unique values, bucketing into 6. Then encoded.
    - **USE_CASE** -----> 5 unique values, Encoded.
    - **ORGANIZATION** -----> 4 unique values, Encoded.
    - **INCOME_AMT** -----> 9 unique values, Encoded.
    - **SPECIAL_CONSIDERATIONS** -----> 2 unique values, binary variable, Y / N.

 - Numerical features:   
    - **STATUS**                     binary varibale. 1 / 0.
    - **ASK_AMT**                    continuous values.
    
 - Split data into training data and testing data.
 - Feature scaling
   Use standard scaler to scale the data to make sure all the feature contributes approximately proportionately to the final distance. 

### Compiling, Training, and Evaluating the Model
- Create Neural Network Model
  Input layer: 44 trained sample features.
  First hidden layer: 80 neurons. Activation function:Relu.
  Second hidden layer: 30 neurons. Activation function:Relu.
  output layer: 1 target varible. Binary classification.
  epochs: 50 
  
  ![Model Summary](https://user-images.githubusercontent.com/105877888/193480994-e3e74314-8d84-49dd-8a97-4507880137d6.png)
  
- Save callback files:
  The model's weights were saved by every 5 epochs.
  
  ![callback](https://user-images.githubusercontent.com/105877888/193481297-a27080f8-1011-49cd-8492-6b574748ad1f.png)

- Model Loss and Accuracy:

  ![Screen Shot 2022-10-02 at 4 33 02 PM](https://user-images.githubusercontent.com/105877888/193481263-19fdc30d-c93a-4b9c-ae4a-cd113e89b32c.png)
 
### Model Optimization
- Target model performance: **75%** 

- Proprocessing Optimization Attempts: 
   - Rebucketing **APPLICATION_TYPE** and **CLASSIFICATION**.[Considering getting more data back for precision.]
   - Keep only active **STATUS**. [Considering only active status affect future funding.]
   - Bucketing **AFFILIATION**. [Considering AFFILIATION column is not normal distributed. Data is heavily skewed.]
   - Binning **ASK_AMT**. [Considering over three quaters of requesting amount is 5000, and others are scatter over 5000 in a wide range.]
   - Changing **INCOME_AMT** to numeric data. [Considering to get more numerical features.]

   The accuracy of first epochs are as follows:
   ```
     Proprocessing Optimization Attempts: 
   - original: loss: 0.5701 - accuracy: 0.7221 
   - bucketing application_accounts < 100: loss: 0.5694 - accuracy: 0.7227 √
   - bucketing classification_counts < 150: loss: 0.5708 - accuracy: 0.7220 X
   - bucketing classification_counts < 500: loss: 0.5728 - accuracy: 0.7203 X
   - filtering active status: loss: 0.6929 - accuracy: 0.5582 X
   - bucketing affiliation_counts < 50: loss: 0.5705 - accuracy: 0.7206 X
   - binning and encoding ASK_AMT: loss: 0.5727 - accuracy: 0.7195 X
   - changing INCOME_AMT to numeric data: loss: 0.5727 - accuracy: 0.7232 √
   ```
  
- Proprocessing Optimization Attempts: 
   - Adding one more hidden layer. [Considering to allow neurons to train on activated input values for deep learning.]
   - Using a different activation function. [Considering tanh function expands the data range between -1 and 1.]
   - Adding neurons. [Considering to get more information from input data.]
   - Changing batch size. [Considering to get more information from input data.]
   - Adding additional epochs. [Considering to scan more or less samples for each epoch.]

   The accuracy of first epochs are as follows:
   ```
   Model Optimization Attempts: 
   - adding hidden layer: loss: 0.5726 - accuracy: 0.7238 √
   - changing activation function to tanh: loss: 0.5685 - accuracy: 0.7243 √
   - adding neurons to hidden layers: loss: 0.5704 - accuracy: 0.7250 √
   - decreasing batch size: loss: 0.5744 - accuracy: 0.7222 X
   - increasing batch size: loss: 0.5433 - accuracy: 0.7392 √
   - adding epochs: loss: 0.5438 - accuracy: 0.7398 √
   ```  
- Final model performance

  ![Final accuracy](https://user-images.githubusercontent.com/105877888/193483480-b5b4ea3a-966f-48b6-ae51-490f7a22e6d5.png)

## Summary
- Unfortunately, target was not achieved. Even if final model performance slightly improved. The loss and accruary was unstable. 
- Most of columns are not in normal distribution. Standard Scaler is not the best choice to do feature scaling.
- Hyperparameter need to be determined and finetuned.
- Since raw data are labeled data, output of the model is a class, this can be considered as a supervised learning classification problem. There are over 34000 applicants in record, which is a large dataset. But only have 10 features. It is more suitable to work with random forest algorithm. Comparing to neural network, random forest saves time and codes. It also have a big advantage on ranking the importance of features.

