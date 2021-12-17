[![NuGet Package](https://img.shields.io/nuget/v/Weather.NET.svg?logo=nuget&logoColor=white&&style=for-the-badge&colorB=green)](https://www.nuget.org/packages/Weather.NET)

# Weather.NET
A simple .NET library that uses OpenWeatherMap API to get the weather of different places and cities. Supports both synchronous and asynchronous methods.

- [Nuget Package](https://www.nuget.org/packages/Weather.NET)
- [Repository](https://github.com/EloyEspinosa/Weather.NET)
- [Official Page](https://eloyespinosa.github.io/Weather.NET/)
- [Documentation](https://eloyespinosa.github.io/Weather.NET/docs/)
- [Tutorial](https://eloyespinosa.github.io/Weather.NET/tutorial)
- [Examples](https://eloyespinosa.github.io/Weather.NET/examples/)

## Example
```c#
using System;
using Weather.NET;
using Weather.NET.Enums;
using Weather.NET.Models.WeatherModel;

...

WeatherClient client = new WeatherClient("Your API key");

// Gets a forecast of the London weather asynchronously, using the city name.
List<WeatherModel> forecasts = await client.GetForecastAsync("London", 8, Measurement.Metric, Language.Spanish);
Console.WriteLine(forecasts[7].Weather[0].Description);

// Gets the current temperature of New York synchronously, using the ZIP Code.
WeatherModel currentWeather = client.GetCurrentWeather("10001", "US", measurement: Measurement.Imperial);
Console.WriteLine(currentWeather.Main.Temperature);

// Gets maps of the entire world.
client.DownloadWeatherMap("temperatureMap.png", MapLayer.Temperature, 0, 0, 0);
await client.DownloadWeatherMapAsync("pressureMap.png", MapLayer.Pressure, 0, 0, 0);
...
```

## Version 1.1.1
- Now the ZIP Code needs to be a string instead of a long, to account for different ZIP formats in different countries.
- Now the Weather.NET logo looks normal.
