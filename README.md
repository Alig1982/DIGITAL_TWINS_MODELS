# DIGITAL_TWINS_MODELS
Simple Example for digital twins model 

import numpy as np
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt

# Simulated historical data (timestamps and failure times)
timestamps = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
failure_times = np.array([10, 12, 13, 16, 18, 20, 22, 25, 27, 30])

# Reshape the data to meet scikit-learn's requirements
timestamps = timestamps.reshape(-1, 1)

# Create a linear regression model
model = LinearRegression()

# Train the model on the historical data
model.fit(timestamps, failure_times)

# Predict failure time for a new timestamp (e.g., timestamp 11)
new_timestamp = np.array([11]).reshape(-1, 1)
predicted_failure_time = model.predict(new_timestamp)

# Plot the historical data and the regression line
plt.scatter(timestamps, failure_times, label='Historical Data')
plt.plot(timestamps, model.predict(timestamps), color='red', label='Regression Line')
plt.scatter(new_timestamp, predicted_failure_time, color='green', label='Predicted Point')
plt.xlabel('Timestamp')
plt.ylabel('Failure Time')
plt.legend()
plt.title('Equipment Failure Time Prediction')
plt.show()

print(f"Predicted failure time at timestamp 11: {predicted_failure_time[0]}")
