# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 30/08/24

### AIM:
To perform regular differncing,seasonal adjustment and log transformation on stock data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
developed By : Yohesh Kumar
Reg No. : 212222240118
```
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

file_path = '/mnt/data/Microsoft_Stock.csv'
data = pd.read_csv(file_path)

data = data[['Date', 'Close']]
data.rename(columns={'Close': 'ClosePrice'}, inplace=True)

data['Date'] = pd.to_datetime(data['Date'])
data.set_index('Date', inplace=True)

data['Differenced'] = data['ClosePrice'].diff()
seasonal_period = 30
data['Seasonal_Differenced'] = data['ClosePrice'].diff(seasonal_period)
data['Log_Transformed'] = np.log(data['ClosePrice'])
data.dropna(inplace=True)

columns_to_plot = {
    'Original Data': 'ClosePrice',
    'Regular Differencing': 'Differenced',
    'Seasonal Adjustment': 'Seasonal_Differenced',
    'Log Transformation': 'Log_Transformed'
}

for title, column in columns_to_plot.items():
    plt.figure(figsize=(10, 4))
    plt.plot(data[column], label=title)
    plt.title(title)
    plt.legend()
    plt.show()
    print(f"{title}:\n", data[column].head())

```


### OUTPUT:

#### ORIGINAL DIFFERENCING:
![Screenshot 2024-08-30 094025](https://github.com/user-attachments/assets/b85f54c3-ef34-41e0-a54f-7a5478ca2951)
#### REGULAR DIFFERENCING:
![image](https://github.com/user-attachments/assets/f71a2922-a58e-4717-80fc-a8546dee69bb)
#### SEASONAL ADJUSTMENT:
![image](https://github.com/user-attachments/assets/d47ab85b-a477-4d40-a665-108b769fbc83)
#### LOG TRANSFORMATION:
![image](https://github.com/user-attachments/assets/68c68dfe-67d6-47ac-a1f6-0235a95a0e53)




### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on stock data
