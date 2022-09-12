# SageMaker-DeepAR-on-Time-Series-Energy-Consumption

A time series is data collected periodically, over time. Time series forecasting is the task of predicting future data points, given some historical data. It is commonly used in a variety of tasks from weather forecasting, retail and sales forecasting, stock market prediction, and in behavior prediction (such as predicting the flow of car traffic over a day). There is a lot of time series data out there, and recognizing patterns in that data is an active area of machine learning research!

In this notebook, we'll focus on one method for finding time-based patterns: using SageMaker's supervised learning model, [DeepAR](https://docs.aws.amazon.com/sagemaker/latest/dg/deepar.html).

## DeepAR
DeepAR utilizes a recurrent neural network (RNN), which is designed to accept some sequence of data points as historical input and produce a predicted sequence of points. So, how does this model learn?

During training, you'll provide a training dataset (made of several time series) to a DeepAR estimator. The estimator looks at all the training time series and tries to identify similarities across them. It trains by randomly sampling training examples from the training time series.

- Each training example consists of a pair of adjacent context and prediction windows of fixed, predefined lengths.
  - The context_length parameter controls how far in the past the model can see.
  - The prediction_length parameter controls how far in the future predictions can be made.
  - You can find more details, in this [documentation](https://docs.aws.amazon.com/sagemaker/latest/dg/deepar_how-it-works.html).
