# Gemini Public API  

## Overview
This script is designed to interact with the Gemini cryptocurrency exchange API to fetch and store data in a local SQLite database. It focuses on retrieving ticker information, order book data, and trade history for different cryptocurrency pairs and saving this information to a database for further analysis or record-keeping.

## Functions
1.  **`create_database()`**:
    
    -   **Purpose**: Initializes a SQLite database named `gemini_data.db` and creates three tables: `Ticker`, `OrderBook`, and `TradeHistory`.
    -   **Tables**:
        -   `Ticker`: Stores the latest bid, ask, and last trade price.
        -   `OrderBook`: Stores the current state of the order book (bids and asks).
        -   `TradeHistory`: Stores historical trade data.
2.  **`fetch_ticker(base_currency='btc', quote_currency='usd')`**:
    
    -   **Purpose**: Fetches the current ticker information for a specified trading pair from Gemini's public API.
    -   **Parameters**:
        -   `base_currency` (default `'btc'`): Base currency of the trading pair.
        -   `quote_currency` (default `'usd'`): Quote currency of the trading pair.
    -   **Returns**: The ticker data as JSON or an error message.
3.  **`fetch_symbols()`**:
    
    -   **Purpose**: Fetches the list of all trading symbols/pairs available on Gemini.
    -   **Returns**: List of symbols as JSON or an error message.
4.  **`fetch_order_book(base_currency='btc', quote_currency='usd')`**:
    
    -   **Purpose**: Retrieves the current order book for a given trading pair.
    -   **Parameters**: Same as `fetch_ticker`.
    -   **Returns**: Order book data as JSON or an error message.
5.  **`fetch_trade_history(base_currency='btc', quote_currency='usd')`**:
    
    -   **Purpose**: Retrieves the trade history for a specific trading pair.
    -   **Parameters**: Same as `fetch_ticker`.
    -   **Returns**: Trade history data as JSON or an error message.
6.  **`save_to_database(data, data_type, base_currency, quote_currency)`**:
    
    -   **Purpose**: Saves the fetched data to the corresponding table in the SQLite database.
    -   **Parameters**:
        -   `data`: Data to be saved (can be ticker, order book, or trade history data).
        -   `data_type`: Type of data ('ticker', 'order_book', or 'trade_history').
        -   `base_currency` and `quote_currency`: Currency pair information.

## Main Execution Flow

-   The script, when run, performs the following steps:
    1.  Creates the necessary database and tables.
    2.  Fetches ticker information for BTC/USD and saves it to the database.
    3.  Fetches order book for BTC/USD and saves it to the database.
    4.  Fetches trade history for BTC/USD and saves it to the database.

## Dependencies

-   **`requests`**: Used to make HTTP requests to the Gemini API.
-   **`json`**: For parsing the JSON responses from the API.
-   **`sqlite3`**: To interact with the SQLite database.

## Usage

To use this script, simply run it in a Python environment with the necessary dependencies installed. It automatically fetches and stores data for the BTC/USD trading pair. You can modify the script to fetch data for other trading pairs by changing the parameters in the `fetch_` functions.

## Examples

### Ticker Table (Limit 5 Row)  
| id | base\_currency | quote\_currency | bid | ask | last | f\_upload\_timestamp |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | btc | usd | 42736.55 | 42740.56 | 42771.09 | 2024-01-14 00:40:48 |
| 2 | btc | usd | 42746.87 | 42746.88 | 42736.9 | 2024-01-14 00:43:55 |
| 3 | btc | usd | 42745.76 | 42749.93 | 42748.63 | 2024-01-14 00:44:41 |
| 4 | btc | usd | 42736.81 | 42740.82 | 42741.36 | 2024-01-14 00:45:32 |
| 5 | btc | usd | 42730.55 | 42733.5 | 42713.26 | 2024-01-14 00:46:04 |

### OrderBook Table (Limit 5 Row)  
| id | base\_currency | quote\_currency | type | price | amount | f\_upload\_timestamp |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | btc | usd | bid | 42734.37 | 0.1181 | 2024-01-14 00:40:49 |
| 2 | btc | usd | bid | 42733.27 | 0.03043 | 2024-01-14 00:40:49 |
| 3 | btc | usd | bid | 42730.83 | 0.27387 | 2024-01-14 00:40:49 |
| 4 | btc | usd | bid | 42728.51 | 0.1181 | 2024-01-14 00:40:49 |
| 5 | btc | usd | bid | 42723.1 | 2.57484 | 2024-01-14 00:40:49 |

### TradeHistory Table (Limit 5 Row)  
| id | base\_currency | quote\_currency | timestamp | tid | price | amount | exchange | type | f\_upload\_timestamp |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | btc | usd | 1705192848 | 2840140822555814 | 42740.06 | 0.04983134 | gemini | buy | 2024-01-14 00:40:50 |
| 2 | btc | usd | 1705192848 | 2840140822555813 | 42737.63 | 0.03043 | gemini | buy | 2024-01-14 00:40:50 |
| 3 | btc | usd | 1705192760 | 2840140822555755 | 42771.09 | 0.00357962 | gemini | buy | 2024-01-14 00:40:50 |
| 4 | btc | usd | 1705192646 | 2840140822555657 | 42761.08 | 0.0001 | gemini | buy | 2024-01-14 00:40:50 |
| 5 | btc | usd | 1705192646 | 2840140822555655 | 42761.08 | 0.0002 | gemini | buy | 2024-01-14 00:40:50 |


  
[Gemini Public API](https://docs.gemini.com/rest-api/#symbols)