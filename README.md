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
  **SPECIAL_CONSIDERATIONS**, **ASK_AMT**. These are potentionally affect applicant's use of funds.
  - Categorical features:
    - **APPLICATION_TYPE**           17 unique values, bucketing into 9. Then encoded.
    - **AFFILIATION**                6 unique values, Encoded.
    - **CLASSIFICATION**.            17 unique values, bucketing into 6. Then encoded.
    - **USE_CASE**                   5 unique values, Encoded.
    - **ORGANIZATION**               4 unique values, Encoded.
    - **INCOME_AMT**                 9 unique values, Encoded.
    - **SPECIAL_CONSIDERATIONS** binary variable, Y / N.

 - Numerical features:   
    - **STATUS**                     binary varibale. 1 / 0.
    - **ASK_AMT**                    continuous values.
    

Compiling, Training, and Evaluating the Model
How many neurons, layers, and activation functions did you select for your neural network model, and why?
Were you able to achieve the target model performance?
What steps did you take to try and increase model performance?



### Create Neural Network Model

Noisy variables are removed from features (2.5 pt)
Additional neurons are added to hidden layers (2.5 pt)
Additional hidden layers are added (5 pt)
The activation function of hidden layers or output layers is changed for optimization (5 pt)
The model's weights are saved every 5 epochs (2.5 pt)
The results are saved to an HDF5 file (2.5 pt)


## Summary
Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and explain your recommendation.
