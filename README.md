# Weather MB API

## API description    
- The Weather MB API allows users to access previously collected weather data for cities located in Manitoba, Canada. Users can request weather data by providing a start date, end date and the name of a city located in Manitoba. The API will return available weather data collected for the specified city based on the dates provided. Data will be divided into specific days that range from the given start date to the given end date. The data returned includes:
    - Average high and low temperatures across the given date range 
    - And for each individual date in the range:
        - High and low temperatures 
        - Wind speed 
        - Humidity
        - Pollen levels

## List of endpoints with parameters
- Endpoint: https://api.weather-mb.org/json
    - Parameters: 
        - **endDate**(string): in YYYY-MM-DD format; restricted to be before or equal to today. If not present, date defaults to current date. Required.
        - **startDate**(string): in YYYY-MM-DD format; restricted to be before or equal to endDate. If not present, date defaults to current date. Required.
        - **city**(string): should be any city/town/village within Manitoba. Required.

## Description of resources
- Returns a list of temperatures at a requested city/town for the specified period of time. 

#### **JSON formatted example**
```
[
    {
        "City": cityName,
        "StartDate": startDate,
        "EndDate": endDate, 
        "AverageHighTemperature": averageHighTemperature,
        "AverageLowTemperature": averageLowTemperature,
        [
            {
                "Date": date,
                "HighTemperature": highTemperature,
                "LowTemperature": lowTemperature,
                "WindSpeed": windSpeed,
                "Humidity": humidity,
                "Pollen": pollen
            },
            ...
        ]
    }
]
```

## Sample request with sample response
https://api.weather-mb.org/json?endDate=2022-11-12&startDate=2022-11-11&city=Winnipeg

[
    {
        "results":
        {
            "City": "Winnipeg",
            "StartDate": "2022-11-11",
            "EndDate": "2022-11-12", 
            "AverageHighTemperature": "14",
            "AverageLowTemperature": "-4",
            [
                {
                    "date": "2022-11-12",
                    "HighTemperature": "13",
                    "LowTemperature": "-5",
                    "WindSpeed": "43",
                    "Humidity": "50%",
                    "Pollen": "Low"
                },
                {
                    "date": "2022-11-11",
                    "HighTemperature": "15",
                    "LowTemperature": "-3",
                    "WindSpeed": "76",
                    "Humidity": "80%",
                    "Pollen": "High"
                }
            ]
        }
    }
]
