# Neural_Network_Charity_Analysis
## Overview
The company requests the ability to accurately predict a successful company for grant investment.  Machine learning using a neural network will be used to train and test identifying features to predict the probability of success for company funded applicants for grants.  Using a dataset including 34000 organizations that have received funding from the company, a binary classifier will train the algorithm that will be used for the predictions. 
## Software
•	Google Colab
•	Python
•	Pandas
•	TensorFlow
•	Sckikit-learn 
## Results
###	Data Preprocessing
o	What variable(s) are considered the target(s) for your model?  

   - The target variable is “IS_SUCCESSFUL”.  

o	What variable(s) are considered to be the features for your model? 

   - The features of the model are APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, ASK_AMT.  

o	What variable(s) are neither targets nor features, and should be removed from the input data?  
    
   - NAME, EIN, INCOME_AMT, STATUS, SPECIAL_CONSIDERATIONS 

###	Compiling, Training, and Evaluating the Model
o	How many neurons, layers, and activation functions did you select for your neural network model, and why?  

   - The initial model was selected to have 80 neurons in the first hidden layer and 30 neurons in the second hidden layer.  The activation for both layers was “RELU”.      
    “RELU” was selected due to the complexity of the features. 

![1stmodel](https://user-images.githubusercontent.com/79231355/126245722-db96ee19-ce52-46d1-b303-cce57aaeaf6e.png)

o	Were you able to achieve the target model performance? 
    
   - No, the best performance achieved was 0.7413 accuracy and 0.5356 loss before optimization. 
        
![initial_accuracy](https://user-images.githubusercontent.com/79231355/126245888-70d77264-694a-4046-aaeb-3618c190d0df.png)

o	What steps did you take to try and increase model performance?
        
   - Removed additional columns- status, special considerations. These columns do not provide essential information for this analysis.  Very few companies have a different   
   status or special considerations.  These columns could be producing bias to the model. 
        
   ![column removal](https://user-images.githubusercontent.com/79231355/126246019-2754b38b-6e7b-4fdb-adf3-44d291a4d748.png)
          
   - Inspected income amount column and removed.  It was determined that income amount could introduce bias or unnecessary complexity into the model due to the exceptionally         large number without income reported to the company.   Performing a new bin procedure could produce results that include this feature, however, there are 3 times as many 
    reporting 0 in this category as all other bins combined.  
    
   ![INCOME_AMT](https://user-images.githubusercontent.com/79231355/126246061-354931c5-2db5-4737-ba6c-f3840c2e7e75.png)

   - Inspect and bin ASK_AMT- due to the large number of unique values, ASK_AMT values were binned to improve the model.  
    
   ![ASK_AMT](https://user-images.githubusercontent.com/79231355/126246079-d1f21771-9401-44e1-8245-eb22946f5518.png)

   - Add more neurons to hidden layer-   The neurons were changed to 100 neurons on layer 1 and 50 neurons on layer 2 to improve the learning of the model in the optimization.       With the number of features and the size of the dataset, more neurons should be beneficial to the model.  
    
   ![more_neurons](https://user-images.githubusercontent.com/79231355/126246116-51de9ddd-95fb-4809-994b-5e27a7141617.png)
   
   ![neuron_accuracy](https://user-images.githubusercontent.com/79231355/126246399-ecec65d8-18a2-44ee-a4d8-0cd325cf7e52.png)

   - Add more hidden layers-  a third hidden layer was added with 50 neurons. 
    
   ![add_hidden_layers](https://user-images.githubusercontent.com/79231355/126246133-13a3f658-2d7a-4057-84d7-aa92e1d78465.png)
   
   ![hidden_layer_accuracy](https://user-images.githubusercontent.com/79231355/126246411-c890e730-9703-487f-a408-e52da9dbcb80.png)

   - Changed activation function to “sigmoid” for all layers. 
    
   ![change_activation_function](https://user-images.githubusercontent.com/79231355/126246148-deb86041-88cc-4490-90dc-384b5d28bbd2.png)

   ![activation_function_accuracy](https://user-images.githubusercontent.com/79231355/126246422-4d644aa1-5cdc-43db-9ce9-75b41ab49fe1.png)

## Summary
Optimization of this model was not achieved.  In fact, the model was less accurate after all optimization steps were taken.  Additional optimization should be performed to create a best fit model.  An auto-optimization tool using sequential and keras tuner could be useful to help determine which activation function would best fit this data set.  
Using this model to make predictions on the success of business with which the company should invest should be limited as the model does not fit the dataset well.  
