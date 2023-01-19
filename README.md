# Weather-Package

My first package
Check it out:
https://pypi.org/project/sunnyday-calcetto/


        Create a WEather object, taking as an input an apikey, a city name or lan and let coordinates.

        Package use example:
        # Create a Weather object using the city name:
        # The apikey below is not guaranteed to work.
        # Get your own apikey from openweathermap.org.
        # And wait a couple of hours for the apikey to get activated
        # The apikey could be activated even within minutes

        >>> weather = Weather(apikey='c4bcb6957g9e0b1ae584263c62fb5d3b', city='Vlore')

        # Using latitude and longitude coordinates
        >>> weather = Weather(apikey='c4bcb6957g9e0b1ae584263c62fb5d3b', lat=40, lon= -4)

        # Get complete weather data for the next 12 hours
        >>> weather.next_12h()

        # Simplified data for the next 12h
        >>> weather.next_12h_simplified()
