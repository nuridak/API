# Weather MB API

## GROUP INFO: 
- Group Number: 02
    - Nurida Karimbaeva - [nuridak](https://github.com/nuridak)
    - AL Fahiyan Siyam - [alahiyansiyam](https://github.com/AlFahiyanSiyam)
    - Felix Wedel - [WedelFelix](https://github.com/WedelFelix)
    - Gurman Toor - [GurmanToor](https://github.com/GurmanToor)

## API description    
- API that gets Weather statistics from the Manitoba Weather database. Returns high temperature/low temperature/humidity/wind speed/pollen

## List of endpoints with parameters
 
- GET Weather: returns general weather information for the specified period of time at the specified city/town within Manitoba.
    - Parameters: 
        - endDate: in YYYY-MM-DD format; restricted to be before or equal to today
        - startDate: in YYYY-MM-DD format; restricted to be before or equal to endDate
        - city: should be any city/town/village within Manitoba
    

## Description of resources - formatted as JSON
- Resources: one or two resources
[
    {
        "results":
        {
            "City": cityName,
            "StartDate": startDte,
            "EndDate": endDte, 
            "AverageHighTemperature": HighTemperature,
            "AverageLowTemperature": LowTemperature,
            [
                {
                    "date": date,
                    "HighTemperature": HighTemperature,
                    "LowTemperature": LowTemperature,
                    "WindSpeed": speed,
                    "Humidity": humidity,
                    "Pollen": pollen
                },
                {
                    "date": date,
                    "HighTemperature": HighTemperature,
                    "LowTemperature": LowTemperature,
                    "WindSpeed": speed,
                    "Humidity": humidity,
                    "Pollen": pollen
                },
                ...
            ]
        }
    }
]

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
