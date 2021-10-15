# eva7 Assignment Pytorch 2.5

Data Generation Strategy: 
1. Initially an array of 60000 integers (call it R_train) is randomly generated and fixed as the training data set
2. A custom data loader is used which combines the MNIST data and the R_train to generate the data and the label
3. Here data is in two parts a.) a MNIST image and b.) an integer from R_train
4. Here label is in two parts a.) a MNIST label b.) a 'SUM' label for each integer in R_train . The SUM label is the summation of MNIST label and the integer itself
5. Similar strategy is followed for making the test data set (call it R_test) with 10000 randomly generated integers

Data Representation :
1. Each integer in R_train belongs to one of 10 classes (0-9) and is one hot encoded. The label for each integer data in R_train is again an integer but belonging to one of 18 classes (sum of mnist and integer from R_train)
2. The label is one hot encoded

Combining the inputs : 
1. The images from MNIST are fed into the network as 2D data. The images go through a standard piple line of CNNs untill flattened before feeding to a Fully Connected (FC) layer. The out put of this FC layer is a 100 dimension array.
2. The integer from R_train is one hot encoded with a 10 dimension array (an integer belongs to one of 10 classes)
3. The 100 dimension array from MNIST and 10 dimension one hot encoded array is concatenated into 110 dimension array
4. This 110 dimension array is passed to a Multilayer Perceptron (MLP) Network with two hidden layers of 200 and 50 nodes
5. The output of this MLP network is a 29 dimension array
6. This 29 dimension array is split in 10 dimension array for predicting MNIST class and 19 dimension array for predicting SUM class

Evaluation of Results:
1. The network is trained over 10 epochs and tested over R_test dataset having 10000 integers and MNIST images for each epoch. 

Loss function Used:
1. A negative log likelihood loss is seperately calculated for MNIST and SUM. Since the network needs to perform well on both MNIST and SUM, both the sum is added and the sum of loss is backpropagated

Training on GPU :
Training has been done on GPU

Results for 10 epochs :

Epoch 1 :
1. MNIST loss=0.13151748478412628 SUM loss=2.334129571914673 batch_id=468: 100%
2. Test set: Average MNIST loss: 0.1669, Accuracy: 9526/10000 (95%)
3. Test set: Average SUM loss: 2.3467, Accuracy: 1181/10000 (12%)

Epoch 2 :
1. MNIST loss=0.13226385414600372 SUM loss=1.6017498970031738 batch_id=468: 100%
2. Test set: Average MNIST loss: 0.0683, Accuracy: 9819/10000 (98%)
3. Test set: Average SUM loss: 1.4576, Accuracy: 4284/10000 (43%)

Epoch 3 :
1. MNIST loss=0.04307926073670387 SUM loss=0.9536581039428711 batch_id=468: 100%
2. Test set: Average MNIST loss: 0.0352, Accuracy: 9894/10000 (99%)
3. Test set: Average SUM loss: 0.8700, Accuracy: 6945/10000 (69%)

Epoch 4 :
MNIST loss=0.04952253773808479 SUM loss=0.37748631834983826 batch_id=468: 100%
Test set: Average MNIST loss: 0.0285, Accuracy: 9915/10000 (99%)
Test set: Average SUM loss: 0.4081, Accuracy: 9361/10000 (94%)

Epoch 5 :
1. MNIST loss=0.09310784935951233 SUM loss=0.1534867137670517 batch_id=468: 100%
2. Test set: Average MNIST loss: 0.0295, Accuracy: 9910/10000 (99%)
3. Test set: Average SUM loss: 0.1465, Accuracy: 9789/10000 (98%)

Epoch 6 :
1. MNIST loss=0.09910460561513901 SUM loss=0.21645613014698029 batch_id=468: 100%
2. Test set: Average MNIST loss: 0.0246, Accuracy: 9931/10000 (99%)
3. Test set: Average SUM loss: 0.0850, Accuracy: 9851/10000 (99%)

Epoch 7 :
1. MNIST loss=0.010061712004244328 SUM loss=0.06789124757051468 batch_id=468: 100%
2. Test set: Average MNIST loss: 0.0251, Accuracy: 9930/10000 (99%)
3. Test set: Average SUM loss: 0.0795, Accuracy: 9866/10000 (99%)

Epoch 8 :
1. MNIST loss=0.011025783605873585 SUM loss=0.025114253163337708 batch_id=468: 100%
2. Test set: Average MNIST loss: 0.0251, Accuracy: 9933/10000 (99%)
3. Test set: Average SUM loss: 0.0734, Accuracy: 9882/10000 (99%)

Epoch 9 :
1. MNIST loss=0.001581490971148014 SUM loss=0.009856115095317364 batch_id=468: 100%
2. Test set: Average MNIST loss: 0.0229, Accuracy: 9930/10000 (99%)
3. Test set: Average SUM loss: 0.0583, Accuracy: 9893/10000 (99%)

Epoch 10 :
1. MNIST loss=0.000775829132180661 SUM loss=0.009833535179495811 batch_id=468: 100%
2. Test set: Average MNIST loss: 0.0228, Accuracy: 9944/10000 (99%)
3. Test set: Average SUM loss: 0.0577, Accuracy: 9904/10000 (99%)
