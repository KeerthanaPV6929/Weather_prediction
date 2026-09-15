# Weather Prediction App

A simple Python project that fetches real-time weather data using the [OpenWeatherMap API](https://openweathermap.org/api). Users enter a city name, and the script retrieves and displays the current temperature and weather description.

## Files

- **`weather_prediction.py`** — Main script. Prompts the user for a city name, calls the OpenWeatherMap API, and prints the current temperature and weather description.
- **`climate.py`** — Helper script that reads an API key from a local `api_key.txt` file and prompts for a location (work in progress / intended to be merged with the API key handling in the main script).

## Requirements

- Python 3.x
- `requests` library

Install dependencies:
```bash
pip install requests
```

## Setup

1. Sign up for a free API key at [OpenWeatherMap](https://openweathermap.org/api).
2. Create a file named `api_key.txt` in the project directory and paste your API key into it (no quotes, no extra spaces).
3. Update `weather_prediction.py` to read the key from `api_key.txt` instead of using a hardcoded key (see **Security Note** below).

## Usage

```bash
python weather_prediction.py
```

You'll be prompted to enter a city name:
```
Enter a city name: London
```

The script will output the raw API response (formatted JSON) followed by a summary line:
```
The current temperature of the London is 15.3 and it's light rain
```

## Security Note

⚠️ **Important:** The current version of `weather_prediction.py` has the OpenWeatherMap API key hardcoded directly in the source code. This is a security risk if the code is shared or pushed to a public repository (e.g., GitHub).

**Recommended fix:**
- Store your API key in `api_key.txt` (already git-ignored/local) and load it the same way `climate.py` does:
  ```python
  api_key = open('api_key.txt', 'r').read().strip()
  ```
- Never commit `api_key.txt` to version control. Add it to `.gitignore`.
- If this key has already been shared or exposed publicly, regenerate it from your OpenWeatherMap account.

## Possible Improvements

- Merge `climate.py` and `weather_prediction.py` into a single script with proper API key handling.
- Add error handling for invalid city names or failed API requests.
- Support multi-day forecasts instead of just current weather.
- Add unit tests.

## License

This project is provided as-is for personal/educational use.
