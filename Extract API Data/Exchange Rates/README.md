# Exchange Rates Data Retrieval and Saving

## Description:

This script is designed to retrieve the latest exchange rates for USD and save them in a CSV file. It uses the Fixer API to fetch the data.

### Requirements:

-   Python 3.x
-   Libraries: pandas, requests, python-dotenv
-   An API key for the Fixer API service.

### Script Overview:

1.  **Environment Variables**: The script uses `python-dotenv` to load environment variables. It expects an `.env` file containing the `EXCHANGE_RATES_API_KEY` for the Fixer API.
    
2.  **API Request**: It sends a GET request to the Fixer API's 'latest' endpoint to fetch the latest exchange rates with USD as the base currency.
    
3.  **Response Handling**: The script processes the response from the API, converting it into a JSON object.
    
4.  **Data Processing**: The exchange rates data is converted into a Pandas DataFrame, focusing on the 'rates' column.
    
5.  **Saving Data**: The DataFrame is saved to a CSV file named "exchange_rates_1.csv".

### Usage:

-   Copy `.env_example` and rename it to `.env`
-   Place your Fixer API key into the `.env` file as `EXCHANGE_RATES_API_KEY=your_api_key`.
-   Run the script in a Python environment where the required libraries are installed.
-   The script outputs the response data and saves it in a CSV file in the same directory.
  

### Note:

-   Ensure the API key is kept secure and not exposed in the code.
-   The script only handles successful responses and does not include error handling for failed API requests or issues with the response data.