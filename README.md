# script_data

# ScriptData Readme
## Task 1
This script fetches intraday data for a given stock symbol using the Alpha Vantage API, converts the data into a Pandas DataFrame, and saves it to a CSV file.

## Code Structure

- `ScriptData` class: Contains the main functionality for fetching and converting intraday data.
- `fetch_intraday_data` method: Fetches the intraday data using the Alpha Vantage API.
- `convert_intraday_data` method: Converts the fetched data into a Pandas DataFrame.
- `__getitem__`, `__setitem__`, and `__contains__` methods: Provide convenient access to DataFrame columns.

## Example Usage

```python
import pandas as pd
from alpha_vantage.timeseries import TimeSeries

# Instantiate ScriptData with your Alpha Vantage API key
api_key = 'YOUR_API_KEY'
data = ScriptData(api_key)

# Fetch and convert intraday data for a specific stock symbol
script = 'AAPL'
data.convert_intraday_data(script)

# Add a timestamp column to the DataFrame
timestamp_column = pd.Timestamp.now() 
data.df.insert(0, 'timestamp', timestamp_column)

# Concatenate desired columns horizontally
concatenated_data = pd.concat([data['timestamp'], data['open'], data['high'], data['low'], data['close'], data['volume']], axis=1)

# Save concatenated data to a CSV file
concatenated_data.to_csv('data.csv', index=False)

# Read the CSV file and print the output data
output_data = pd.read_csv('data.csv')
pd.set_option('display.max_columns', None)
print(output_data)

Make sure to replace 'YOUR_API_KEY' with your actual Alpha Vantage API key.

Requirements
To run this script, you need to have the following dependencies installed:

pandas
alpha_vantage
You can install these dependencies using pip:


pip install pandas alpha_vantage


Additional Information
The script fetches intraday data at 1-minute intervals for the specified stock symbol.
The fetched data is converted into a Pandas DataFrame, and a timestamp column is added.
The concatenated data is saved to a CSV file named 'data.csv'.
The CSV file is then read and displayed on the console.
You can customize the script to fetch data for different stock symbols or time intervals as per your requirements.
Feel free to modify and adapt the script as needed.


Make sure to replace `'YOUR_API_KEY'` with your actual Alpha Vantage API key in the code and provide any additional information or instructions you think would be helpful for users.



