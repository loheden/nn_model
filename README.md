# nn_model
A framework built on top of Tensorflow to be able to dynamically create and train NN models 

In case you find any bugs or improvement areas, please feel free to get in touch.

There are 2 main files to use the NN model:
- nn_model_api_with_csv.ipynb: Used to train the model and calculate accuracy and F1 scores with the given train/dev/test sets.
  The second cell of this file (notebook) includes hyper and optimization parameters. 
  It is documented how to use each parameter in the code itself. Depending on NN architecture, hyper parameter values and 
  given csv file structures, this second cell in the notebook may need some updates by the user.
- nn_model_predict.ipynb:  Used to load the pre-trained model and make predictions.

The framework allows anyone to develop his/her own NN implementation as long as following requirements are met.
If there requirements are not met, the user may need to make own updates.
- The NN reads its train/dev/test set data from a csv file (say, consisting of N columns).
- The top row of each csv file is expected to have headers (name of each column).
- Each remaining row of a csv file represents a unique train/dev/test sample.
- Each csv file is expected consist of following columns:
  Column 1: This column is always supposed to be the ID for each train/det/test sample.
  Column 2 to Column (N-1): These columns represent the features for each train/dev/test sample.
  Column N: Refers to the label of each train/dev/test sample.
  
The NN model allows using several techniques to speed up the learning process and also improve learning capabilities of the model.
Beside hyper parameters, major methods the user can activate / deactivate during the training phase are as following:
- All following changes can be done in the second cell of the notebook nn_model_api_with_csv.ipynb.
- The implementation allows the user to provide his/her train/dev/test set data in multiple csv files.
- Learning rate (alpha) is configurable in the constant INITIAL_LEARNING_RATE.
- If needed, the implementation allows using Learning Decay method too, which gradually decreases the value of learning rate alpha.
- Mini batch size and total number of epochs are configurable.
- Defining NN architecture is totally dynamic and configurable. Number of units in each hidden layer or total number of layers
  can easily be changed.
- To enable training of large NNs, dropout method can be activated too. It is possible to set a separate dropout rate for each
  layer.
- Regularization can be activated by changing the value of LAMBD constant.
- Input Normalization is possible to implement if desired.
- Batch Normalization can be triggered if desired.
- If activated, the model is saved periodically which can later be loaded to use in production and make predictions.

