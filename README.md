# Weather MB API

## API description    
- The Weather MB API allows users to access previously collected weather data for cities located in Manitoba, Canada. Users can request weather data by providing a start date, end date and the name of a city located in Manitoba. The API will return available weather data collected for the specified city based on the dates provided. Data will be divided into specific days that range from the given start date to the given end date. The data returned includes:
    - Average high and low temperatures across the given date range 
    - And for each individual date in the range:
        - Date
        - High and low temperatures 
        - Wind speed 
        - Humidity
        - Pollen levels

## List of endpoints with parameters
- Endpoint: https://api.weather-mb.org/weather
    - Parameters: 
        - **endDate**(string): in YYYY-MM-DD format; restricted to be before or equal to today. If not present, date defaults to current date. Required.
        - **startDate**(string): in YYYY-MM-DD format; restricted to be before or equal to endDate. If not present, date defaults to current date. Required.
        - **city**(string): should be any city/town/village within Manitoba. Required.

## Description of resources
- Returns a list of temperatures at a requested city/town for the specified period of time. 

#### **JSON formatted example**
```
{
    "response": {
        "city": cityName,
        "startDate": startDate("yyyy-mm-dd"),
        "endDate": endDate("yyyy-mm-dd"), 
        "averageHighTemperature": averageHighTemperature(°C),
        "averageLowTemperature": averageLowTemperature(°C),
        "dailyTemperatures":
        [
            {
                "date": date("yyyy-mm-dd"),
                "highTemperature": highTemperature(°C),
                "lowTemperature": lowTemperature(°C),
                "windSpeed": windSpeed(km/h),
                "humidity": humidity(%),
                "pollen": pollenLevel
            },
            ...
        ]
    },
    "status": status
}
```

## Sample request 
````
https://api.weather-mb.org/weather?endDate=2022-11-12&startDate=2022-11-11&city=Winnipeg
````

## Sample response
````
{
    "response": {
            "city": "Winnipeg",
            "startDate": "2022-11-11",
            "endDate": "2022-11-12", 
            "averageHighTemperature": 14,
            "averageLowTemperature": -4,
            "dailyTemperatures":
            [
                {
                    "date": "2022-11-12",
                    "highTemperature": 13,
                    "lowTemperature": -5,
                    "windSpeed": 43,
                    "humidity": 50,
                    "pollen": "Low"
                },
                {
                    "date": "2022-11-11",
                    "highTemperature": 15,
                    "lowTemperature": -3,
                    "windSpeed": 76,
                    "humidity": 80,
                    "pollen": "High"
                }
            ]
    },
    "status": "success"
}

````
