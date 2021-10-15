# eva7
Your code MUST be:
well documented (via readme file on GitHub and comments in the code)
must mention the data representation
must mention your data generation strategy (basically the class/method you are using for random number generation)
must mention how you have combined the two inputs (basically which layer you are combining)
must mention how you are evaluating your results 
must mention "what" results you finally got and how did you evaluate your results
must mention what loss function you picked and why!
training MUST happen on the GPU

Data Generation Strategy: 
1. Initially an array of 60000 integers (call it R_train) is randomly generated and fixed as the training data set
2. A custom data loader is used which combines the MNIST data and the R_train to generate the data and the label
3. Here data is in two parts a.) the MNIST image and b.) the integer from R_train
4. Here label is in two parts a.) the MNIST label b.) the 'SUM' label for each integer in R_train . The SUM label is the summation of MNIST label and the integer itself
5. Similar strategy is followed for making the test data set (call it R_test) with 10000 randomly generated integers

Data Representation :
1. Each integer in R_train belongs to one of 10 classes (0-9) and is one hot encoded. The label for each integer data in R_train is again an integer but belonging to one of 18 classes (sum of mnist and integer from R_train)
2. The label is one hot encoded

Combining the inputs : 
1. The images from MNIST are fed into the network as a 2D data and the Integers from R_train are fed as 1D data (10 bit one hot encoded). The image goes through a standard piple line of CNNs untill flattened before feeding to a Fully Connected layer. Assuming the MNIST label and SUM label are independent of each other for the network, the SUM label is predicted using an extra FC layer. The input to this FC layer is the one hot encoded inout integer

Evaluation of Results:
1. The network is trained over 10 epochs and teested over R_test dataset having 10000 integers and MNIST images. 

Loss function Used:
1. A negative log likelihood loss is seperately calculated for MNIST and SUM. Since the network needs to perform well on both MNIST and SUM, both the sum is added and the sum of loss is backpropagated

Training on GPU :
Training has been done on GPU

Results for 10 epochs :

Epoch 1 :
MNIST loss=0.08297522366046906 SUM loss=2.466980457305908 batch_id=468: 100%|█| 
Test set: Average MNIST loss: 0.0602, Accuracy: 9806/10000 (98%)
Test set: Average SUM loss: 2.4803, Accuracy: 985/10000 (10%)

Epoch 2 : 
MNIST loss=0.0625964105129242 SUM loss=2.3915774822235107 batch_id=468: 100%|█| 
Test set: Average MNIST loss: 0.0319, Accuracy: 9894/10000 (99%)
Test set: Average SUM loss: 2.3591, Accuracy: 1040/10000 (10%)

Epoch 3 :
MNIST loss=0.006198072340339422 SUM loss=2.343538761138916 batch_id=468: 100%|█|
Test set: Average MNIST loss: 0.0330, Accuracy: 9889/10000 (99%)
Test set: Average SUM loss: 2.3308, Accuracy: 1047/10000 (10%)

Epoch 4 :
MNIST loss=0.010398979298770428 SUM loss=2.3249571323394775 batch_id=468: 100%|█
Test set: Average MNIST loss: 0.0352, Accuracy: 9881/10000 (99%)
Test set: Average SUM loss: 2.3202, Accuracy: 1024/10000 (10%)

Epoch 5 :
MNIST loss=0.005175141151994467 SUM loss=2.300950050354004 batch_id=468: 100%|█|
Test set: Average MNIST loss: 0.0332, Accuracy: 9900/10000 (99%)
Test set: Average SUM loss: 2.3167, Accuracy: 1076/10000 (11%)

Epoch 6 :
MNIST loss=0.025918133556842804 SUM loss=2.3093085289001465 batch_id=468: 100%|█
Test set: Average MNIST loss: 0.0282, Accuracy: 9911/10000 (99%)
Test set: Average SUM loss: 2.3151, Accuracy: 1054/10000 (11%)

Epoch 7 : 
MNIST loss=0.018872041255235672 SUM loss=2.3080291748046875 batch_id=468: 100%|█
Test set: Average MNIST loss: 0.0309, Accuracy: 9894/10000 (99%)
Test set: Average SUM loss: 2.3126, Accuracy: 1091/10000 (11%)

Epoch 8 : 
MNIST loss=0.017793577164411545 SUM loss=2.3040051460266113 batch_id=468: 100%|█
Test set: Average MNIST loss: 0.0293, Accuracy: 9924/10000 (99%)
Test set: Average SUM loss: 2.3102, Accuracy: 1116/10000 (11%)

Epoch 9 :
MNIST loss=0.002159718656912446 SUM loss=2.2874672412872314 batch_id=468: 100%|█
Test set: Average MNIST loss: 0.0359, Accuracy: 9892/10000 (99%)
Test set: Average SUM loss: 2.3097, Accuracy: 1065/10000 (11%)

Epoch 10 :
MNIST loss=0.005997654050588608 SUM loss=2.3240864276885986 batch_id=468: 100%|█
Test set: Average MNIST loss: 0.0289, Accuracy: 9909/10000 (99%)
Test set: Average SUM loss: 2.3079, Accuracy: 1079/10000 (11%)
