# EVA5 Session 5 Assignment by Sachin Dangayach

This assignment is based on the concepts of Neural Network Architectural Basics. We have to apply to concepts learnt like transformations, batch normalization, drop outs, learning rate etc. to design the network which can attain required accuracy.

# Constraints.

 The network should be able to attain 99.40% accuracy (shown in continuous 4 epochs) in less than 15 epochs using less than 10K parameters. Process should be described in 4 steps.

## Steps 1: Model Setup
We start with working setup provided as assignment which has got 6.3M parameters and overfitting as the train accuracy reached to almost 99.9% leaving no scope for test accuracy to improve which was around 99.28%.

### A. Target
Setup a lighter model in comparison to the base model and get a fully functional code by following steps -
1. Set Transforms
2. Set Data Loader
3. Explore/Study the data - Perform ETL on Data and be the data Dr.
4. Setup the model architecture
5. Set Training & Test Loop

Explore the dataset.

### B. Results
We take this as base model with 6.3M parameters and improve it to attain a model with following results-
    1. Parameters:1.9M
    2. Best Training Accuracy: 99.57%
    3. Best Test Accuracy: 99.11%

### C. Analysis
1. Reduced the size of model and achieved a working NN model
2. Though the difference between train and test accuracy always maintained the possibility of attaining 99.4% accuracy but model couldn't achieve it even in 20 Epochs.
3. Model didn't overfit but need improvement and thus further reduction in size and techniques like batch normalization should be applied to improve the performance of model

### D. File Name uploaded in Repo
EVA5_S5_NN_Step1.ipynb

--------------------------------------------------------
## Steps 2: Lighter Model with batch normalization to improve the performance

### A. Target
a) Reduce the number of parameters in model. This will result in reduction of model performance as we will keep other things constant.
b) Apply "Batch Normalization" to improve the model efficiency.

### B. Results
    1. Parameters: 10,970
    2. Best Training Accuracy in 15 epochs: 99.80%
    3. Best Test Accuracy in 15 epochs: 99.21%

### C. Analysis
1. After reducing the size of model from 1.9M to 10.9K parameters, the performance dips as expected. Model is under capacity and couldn't reach 99% even in 15 epochs after reaching 98% accuracy in epochs 7
2. Application of batch normalization improved the model performance and model could reach test accuracy above 99% but couldn't meet the constraint of 99.4% in less than 15 epochs
3. Model showed overfitting from 14th epoch onwards making to harder to learn further to achieve the target
4. Regularization should be tried on this model to bring the train/test accuracies down to get the scope of pushing the model to train better and get the desired level of accuracy

### D. File Name
EVA5_S5_NN_Step2.ipynb

--------------------------------------------------------

## Steps 3: Apply Regularization, Replace large size kernel with GAP in sequence

### A. Target
Step 1. Add regularization to push model to learn further. Add the dropout layer at every layer except the last layer.
IF target of 99.4% is not achieved, go to step 2
Step 2. Replace the large size kernel with GAP

### B. Results
Step 1. (Addition of Dropout (10%))
    1. Parameters: 10,970
    2. Best Training Accuracy in 15 epochs:99.20%
    3. Best Test Accuracy in 15 epochs:99.37%
Step 2. (Replace the 7*7 kernel by GAP)
    1. Parameters: 6,070
    2. Best Training Accuracy in 15 epochs:98.44%
    3. Best Test Accuracy in 15 epochs:98.87%

### C. Analysis
Step 1.(Addition of Dropout (10%))
    1. After application of dropout in all allowed layers, model is not overfitting and starts learning better but model couldn't reach to the desired levels of performance even in 20 epochs ( train accuracy = 99.31%, test accuracy = 99.33%).
    2. We need to add capacity to model to make it learn better.
    3. We should add GAP to replace the large 7*7 kernel but it will reduce the capacity also. we can redesign the last layers to get the required learning capacity and performance

Step 2. Replace the large size kernel with GAP
    1. Model is under capacity and hence couldn't learn as expected. We need to add capacity back to the model to make it learn better.
    2. We should give the capacity to model at last layer and do the adjustments to get the model parameters in required limit of under 10K.

### D. File Name
EVA5_S5_NN_Step3.ipynb

--------------------------------------------------------

## Steps 4: Add capacity to model, adjust max pooling location to 5*5 RF, apply transformation to train data set and play with learning rate.

### A. Target
1. Increase the capacity of model to train it better while keeping under 10K parameters achieving 99.40% accuracy in less than 15 epochs.
2. Try to make train dataset similar to test dataset, training more difficult by applying transformations to training dataset
3. Try to find the right combination of learning rates to get the required accuracy in less than 15 epochs

### B. Results
Step1 ( Increase capacity)
    1. Parameters: 9,912
    2. Best Training Accuracy in 15 epochs:99.11%
    3. Best Test Accuracy in 15 epochs:99.20%
Step2 ( Transformations)
    1. Parameters: 9,912
    2. Best Training Accuracy in 15 epochs:99.24%
    3. Best Test Accuracy in 15 epochs:99.49%
Step3 ( Transformations and Adjustment to learning rate)
    1. Parameters: 9,912
    2. Best Training Accuracy in 15 epochs:99.24%
    3. Best Test Accuracy in 15 epochs:99.49%

### C. Analysis
Step1 (Increase capacity):
Model performs better but missing the target. We can try to push it to train better but making the training more difficult by adding random rotations to the images (-7to7) degree.
Step2 and Step 3 (Training dataset transformation and adjustment to learning rate)
We see the train accuracy is lesser than test accuracy as the training dataset is more challenging post transformations and this helps to train the model better. We keep learning rate and 0.1 and bring it down by factor of .1 after every 5 epochs. Model achieves 99.48% in 5th epoch and consistently performs above 99.4% there onwards as adjustment to learning helps in finding correct learning rate to prevent run pass the minima for loss function.

### D. File Name
EVA5_S5_NN_Step4.ipynb
