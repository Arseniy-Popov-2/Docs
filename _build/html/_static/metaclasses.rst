#### About ###
* Telegram bot with a weather forecast for the day

#### Built with
* deployed to `Heroku` at https://t.me/AMP_TodayWeatherBot
* built with `python-telegram-bot` as a wrapper around Telegram's API
* utilizes `Google Geocoding API` to interpret free-form address input and `OpenWeatherMap API` to obtain weather forecasts
* uses `PostgreSQL` for storing user data like the default/latest addresses and for caching the mapping from free-form
address inputs to geographic localities
* employs `SQLAlchemy` as an ORM
* applies `unittest` as a testing framework and `pyrogram` as Telegram API wrapper for integration testing allowing
to test both the development version (with database and client resets between tests) and the deployed version

#### File structure
- TodayWeatherBot
   - [Pipfile](Pipfile)
   - [Pipfile.lock](Pipfile.lock)
   - [Procfile](Procfile)
   - [README.md](README.md)
   - [config.ini](config.ini)
   - today\_weather
     - [\_\_init\_\_.py](today_weather/__init__.py)
     - [\_\_main\_\_.py](today_weather/__main__.py)
     - [bot.py](today_weather/bot.py)
     - [config.py](today_weather/config.py)
     - [db.py](today_weather/db.py): *utilities to communicate with the database*
     - [handlers.py](today_weather/handlers.py): *handlers to orchestrate the core logic*
     - [models.py](today_weather/models.py): *database models*
     - tests
       - [\_\_init\_\_.py](today_weather/tests/*init*.py)
       - [tests.py](today_weather/tests/tests.py): *tests*
     - utils
       - [\_\_init\_\_.py](today_weather/utils/*init*.py)
       - [geocoding.py](today_weather/utils/geocoding.py): *interpreting address input w/ the Geocoding API*
       - [misc.py](today_weather/utils/misc.py)
       - [owmparser.py](today_weather/utils/owmparser.py): *getting weather forecast w/ the OpenWeatherMap API*
       - [recommend.py](today_weather/utils/recommend.py): *devising a response for the user*