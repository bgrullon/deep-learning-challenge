# deep-learning-challenge

## Overview
#### The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. With your knowledge of machine learning and neural networks, you’ll use the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.

## Final Deep NN Model
![finalmodel](https://github.com/bgrullon/deep-learning-challenge/assets/45550119/e2f47ac1-9f2d-439f-b6df-f431b4a0d13e)

## Results

### Data Preprocessing

- What variable(s) are the target(s) for your model?
  - `IS_SUCCESSFUL` was the Target Variable.
    
- What variable(s) are the features for your model?
  - NAME — Identification columns
  - APPLICATION_TYPE — Alphabet Soup application type
  - AFFILIATION — Affiliated sector of industry
  - CLASSIFICATION — Government organization classification
  - USE_CASE — Use case for funding
  - ORGANIZATION — Organization type
  - STATUS — Active status
  - INCOME_AMT — Income classification
  - SPECIAL_CONSIDERATIONS — Special considerations for application
  - ASK_AMT — Funding amount requested
    
- What variable(s) should be removed from the input data because they are neither targets nor features?
  - EIN and NAME were the first columns removed but trying to get over 75% accuracy was difficult due to overfitting. Adding back in `NAME` helped get the model over 75% accuaracy due to adding more data.
    
### Compiling, Training, and Evaluating the Model
- How many neurons, layers, and activation functions did you select for your neural network model, and why?
  - At first I started with 2 hidden layers, 80 neurons on the first and 30 neurons on the second. I also used `relu` activation function for both hidden layers since it is usually a great activation function to start with, especially after scaling. 

- Were you able to achieve the target model performance?
  - No, With my first model I only go a `val_accuracy` of 73%.
    
- What steps did you take in your attempts to increase model performance?
  - I added in more data since my model was overfitting. I could tell because increasing the `epochs` would eventually make my testing data perform worse than the training data. I added in the `NAME` column during EDA which added over 19k columns worth of data to use for training. I then created a function to build a my model to use in the keras tuner called `RandomSearch()`. In the function I added in regularization L2 to help with overfitting, as well as early stopping which would stop the model fit early if `val_accuracy` showed degration. I then imported `Adam` so that i can try a few different learning rates while using the keras tuner, as well as 3 different activation functions: `relu`, `tanh`, and `sigmoid`. Lastly I added a third layer to help with all the extra data.
    
## Summary
#### Overall, without tuning, the model was over 70% accuracy. Fine tuning the model helped push the accuracy over 75% by not removing so much data during EDA, and adding methods like regularization and early stopping to prevent overfitting. This allowed me to increase trails on the tuner, as well as over all epochs to get a good accuracy.

#### PreTuned Acc
![image2](https://github.com/bgrullon/deep-learning-challenge/assets/45550119/261ddfab-9264-426c-af7b-de4c2f4e081e)

#### Tuned Acc
![image1](https://github.com/bgrullon/deep-learning-challenge/assets/45550119/dc7224e4-0e5a-427c-a2dc-3d86b19a1d19)

### Other Methods
##### If I had to use other models, I would probably use a logistic regression model or a pipeline with different models like RandomForest and XGboost. I have not testing this but I believe I could get as good accuarcy or the same without needing to add in `NAME` by fine tuning a classifier/Esemble model. This would allow for an easier model to maintain and would be more cost effective than using a Neural Network.






