# Time Series State Prediction using Neural Networks
Huy Huynh

## Abstract
Time series data are frequent in the real world as a big portion of the data we collect are through sensors. The page explore the many Neural Network Architecture used to solve state estimation for time series data. The few architectures we are looking at are Feed Foward, LSTM, RNN and Echo State neural networks.

## Introduction
The dynamic system that will be exlored is Lorenz Equation. The time range of the data is 8 second with a time step of 0.01 second, so in total 800 data points. The training data is compose of solving Lorenz Equations for $\rho=10,28,40$. For each $\rho$ value there will be 100 runs using random initial conditions. Similarly, the testing data is compose of solving Lorenz Equation for $\rho=17,35$. Train and test Feed Foward, LSTM, RNN and Echo State neural networks using the data set described.

The results after solving Lorenz Equations for $\rho=10,28,40$ as the training set is shown in Figure 1-3 below.

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/raw10.png" width="500"/>
</p>
<p align="center">
  Figure 1. Lorenz Equations for $\rho=10$
</p>

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/raw28.png" width="500"/>
</p>
<p align="center">
  Figure 2. Lorenz Equations for $\rho=28$
</p>

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/raw40.png" width="500"/>
</p>
<p align="center">
  Figure 3. Lorenz Equations for $\rho=40$
</p>

The results after solving Lorenz Equations for $\rho=17,35$ as the testing set is shown in Figure 4-5 below.

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/raw17.png" width="500"/>
</p>
<p align="center">
  Figure 4. Lorenz Equations for $\rho=17$
</p>

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/raw35.png" width="500"/>
</p>
<p align="center">
  Figure 5. Lorenz Equations for $\rho=35$
</p>

## Background
In order estimate future points using neural networks, first we must format the data where the input matrix X contains data points from 0 to n-1 time frame and output matrix Y contains data points from 1 to n. Therefore, $Y=F(X)$ Predict the next data point in time given the current data point.

## Implementation
For Feed Foward, LSTM and RNN networks, use mean square error as the loss function and use stochastic gradient descent. Train on data with $\rho=10,28,40$ and for each $\rho$ train for 30 epochs with a learning rate of 0.001 and momentum of 0.9.

### Feed Foward Networks
The networks contains three fully connected layers with input/output dimension of 3->18->72->3, and use ReLU as the activation function in between layers except for the output layer. The network code implementation is shown in the figure below.

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/FFN.png" width="500"/>
</p>
<p align="center">
  Figure 6. Feed Foward Neural Networks
</p>

### LSTM Networks
The networks contains two layer, with the first one being the built=in Pytorch LSTM layer using 3 hidden layers with a size of 50 then a fully connected linear layer map 50 dimension output from LSTM into a 3 dimension vector. The network code implementation is shown in the figure below.

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/LSTM.png" width="500"/>
</p>
<p align="center">
  Figure 7. LSTM Neural Networks
</p>

### RNN Networks
The networks contains two layer, with the first one being the built=in Pytorch RNN layer using 3 hidden layers with a size of 50 then a fully connected linear layer map 50 dimension output from RNN into a 3 dimension vector. The network code implementation is shown in the figure below.

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/RNN.png" width="500"/>
</p>
<p align="center">
  Figure 8. RNN Neural Networks
</p>

### Echo State Networks
Used a echo state networks implementation from this repo (https://github.com/sylvchev/simple_esn). Simple_esn implement a Python class of simple Echo State Network models within the Scikit-learn framework. It is intended to be a fast-and-easy transformation of an input signal in a reservoir of neurons. The regression could be done with any scikit-learn ridge regressor. The code implemention for the Echo State Network is shown in the figure below.

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/esn.png" width="500"/>
</p>
<p align="center">
  Figure 9. Echo State Networks
</p>

## Results
### Feed Foward Networks
The testing means square error on $\rho=17$ data is 0.3879 and on $\rho=35$ is 0.1652. The plotted prediction for $\rho=17, 35$ is shown in figure 10 and 11 respectively below.

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/FNN17.png" width="500"/>
</p>
<p align="center">
  Figure 10. Feed Foward Neural Networks Prediction $\rho=17$
</p>

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/FNN35.png" width="500"/>
</p>
<p align="center">
  Figure 11. Feed Foward Neural Networks Prediction $\rho=35$
</p>

### LMST Networks
The testing means square error on $\rho=17$ data is 142.96 and on $\rho=35$ is 9.256. The plotted prediction for $\rho=17, 35$ is shown in figure 12 and 13 respectively below.

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/LMST17.png" width="500"/>
</p>
<p align="center">
  Figure 12. LMST Neural Networks Prediction $\rho=17$
</p>

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/LMST35.png" width="500"/>
</p>
<p align="center">
  Figure 13. LMST Neural Networks Prediction $\rho=35$
</p>

### RNN Networks
The testing means square error on $\rho=17$ data is 14.25 and on $\rho=35$ is 2.56. The plotted prediction for $\rho=17, 35$ is shown in figure 14 and 15 respectively below.

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/RNN17.png" width="500"/>
</p>
<p align="center">
  Figure 14. RNN Neural Networks Prediction $\rho=17$
</p>

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/RNN35.png" width="500"/>
</p>
<p align="center">
  Figure 15. RNN Neural Networks Prediction $\rho=35$
</p>

### Echo State Networks
The testing means square error on $\rho=17$ data is 1.288 and on $\rho=35$ is 0.418. The plotted prediction for $\rho=17, 35$ is shown in figure 16 and 17 respectively below.

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/ESN17.png" width="500"/>
</p>
<p align="center">
  Figure 16. Echo State Neural Networks Prediction $\rho=17$
</p>

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/ESN35.png" width="500"/>
</p>
<p align="center">
  Figure 17. Echo State Neural Networks Prediction $\rho=35$
</p>

## Conclusion
In conclusion, for this particular training and testing setup the best state predicitor is the Feed Foward Networks in term of mean square error. The Feed Foward Networks testing means square error on $\rho=17$ data is 0.3879 and on $\rho=35$ is 0.1652. For all networks, mean square error is lower when testing on $\rho=35$ data compared to $\rho=17$ data. The reason for the difference could be that as you increase $\rho$ the Lorenz equations converges to the attractors faster, therefore most of the data points is near the attractors and making it easier for the network to predict the next data point. In addition, all the networks prediction mostly capture points near the attractors correctly, while points far away are not close to the ground truth data.
