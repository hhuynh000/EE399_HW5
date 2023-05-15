# Time Series State Prediction using Neural Networks
Huy Huynh

## Abstract
Time series data are frequent in the real world as a big portion of the data we collect are through sensors. The page explore the many Neural Network Architecture used to solve state estimation for time series data. The few architectures we are looking at are Feed Foward, LSTM, RNN and Echo State neural networks.

## Introduction
The dynamic system that will be exlored is Lorenz Equation. The time range of the data is 8 second with a time step of 0.01 second, so in total 800 data points. The training data is compose of solving Lorenz Equations for $\rho=10,28,40$. For each $\rho$ value there will be 100 runs using random initial conditions. Similarly, the testing data is compose of solving Lorenz Equation for $\rho=17,35$. Train and test Feed Foward, LSTM, RNN and Echo State neural networks using the data set described.

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
  Figure 1. Feed Foward Neural Networks
</p>

### LSTM Networks
The networks contains two layer, with the first one being the built=in Pytorch LSTM layer using 3 hidden layers with a size of 50 then a fully connected linear layer map 50 dimension output from LSTM into a 3 dimension vector. The network code implementation is shown in the figure below.

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/LSTM.png" width="500"/>
</p>
<p align="center">
  Figure 2. LSTM Neural Networks
</p>

### RNN Networks
The networks contains two layer, with the first one being the built=in Pytorch RNN layer using 3 hidden layers with a size of 50 then a fully connected linear layer map 50 dimension output from LSTM into a 3 dimension vector. The network code implementation is shown in the figure below.

<p align="center">
  <img src="https://github.com/hhuynh000/EE399_HW5/blob/main/resources/LSTM.png" width="500"/>
</p>
<p align="center">
  Figure 3. RNN Neural Networks
</p>
