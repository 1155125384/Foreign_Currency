## Content

1.  currency_api
    *   get_all_bank_exchange_rate
    *   get_final_rate
2.  forecast

`currency_api` extract the currency exchange rate (against HKD) from bank open data as `get_all_bank_exchange_rate`

`currency_api` analyze the bank open data and generate the best exhcange rates as `get_final_rate`

`forecast` learn the history data via yahoo finance by LSTM model and generate the predicted exchange rate 

## Result

A file named `file` will be automatically generated and include following result generate by the backend codes
1.    `exchange_rates_website` 
(from `currency_api`)
2.    `json` 
(including `get_all_bank_exchange_rate`, `get_final_rate`, `forecast`)
3.    `log` 
(including `currency_api`, `get_all_bank_exchange_rate`, `get_final_rate`, `forecast`)

`exchange_rates_website` includes the raw html content from different banks 

`json` includes the generated result in JSON format

`log` includes the process status of the program, it might shows **error** when connect to MongoDB. Please refer to remarks for more information.

You may refer to `sample_file`, where the program execute with 30 mins

## Compile

Please directly run the `main.py` file to test the program. 

The following library is required to install before compile the program:
*   pandas
*   datetime
*   json
*   time
*   os
*   io
*   selenium
*   webdriver_manager
*   ast
*   pymongo
*   locale
*   sklearn
*   keras
*   numpy
*   matplotlib
*   contextlib
*   sys
*   tensorflow

## Remarks

1.  The program is originally designed for connecting to MongoDB and generate the datum in json format as Open API. You may found the following codes I have comment / edit some code related to MongoDB, indicates with `# For Connecting to MongoDB`. Simply please modify in the following sections if you want to connect to MongoDB.
    *   currency_api
        *   constant.py --- to input the assigned mongodb project url
        *   sub_main.py --- uncomment TWO sections
    *   forcast
        *   constant.py --- to input the assigned mongodb project url
        *   sub_main.py --- uncomment the section
2.  Please create two database with two and one collection(s) respectively in your assigned mongodb project.
    *   currency_api (Database 1)
        *   get_all_bank_exchange_rate (Collection 1 in Database 1)
        *   get_final_rate (Collection 2 in Database 1)
    *   forecast (Database 2)
        *   result (Collection 1 in Database 2)
3.  As mentioned, **error** in log file might be found as the code (if you have modified) included upload data to MongoDB and might have no access to the online database.