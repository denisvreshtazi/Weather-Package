# ☀️ Weather-Package (`sunnyday-calcetto`)

> A lightweight Python package that wraps the **OpenWeatherMap API** to fetch current and 12-hour forecast data, by **city name** or **lat/lon coordinates**.

[![PyPI](https://img.shields.io/badge/PyPI-sunnyday--calcetto-blue)](https://pypi.org/project/sunnyday-calcetto/)
[![Python](https://img.shields.io/badge/python-3.6%2B-yellow)]()
[![Status](https://img.shields.io/badge/status-published-success)]()

---

## 📌 Overview

`sunnyday-calcetto` was my **first published Python package on PyPI**. It exposes a single `Weather` class that talks to OpenWeatherMap's `5 day / 3 hour forecast` endpoint and returns clean, ready-to-use data structures — useful for small weather widgets, CLI tools, or learning how Python packaging works.

🔗 **PyPI:** https://pypi.org/project/sunnyday-calcetto/

## 🚀 Installation

```bash
pip install sunnyday-calcetto
```

## 🔑 Prerequisites

- An OpenWeatherMap API key — get one for free at [openweathermap.org](https://openweathermap.org)
- Note: newly issued keys can take a few minutes to a few hours to activate

## 💻 Usage

### Create a `Weather` object — by city
```python
from sunnyday import Weather

weather = Weather(apikey='YOUR_API_KEY', city='Vlore')
```

### Or by coordinates
```python
weather = Weather(apikey='YOUR_API_KEY', lat=40, lon=-4)
```

### Fetch forecast data
```python
# Full 12-hour forecast (raw API response)
weather.next_12h()

# Simplified forecast (datetime, temperature, sky condition)
weather.next_12h_simplified()
```

### Render sky-condition icons
The simplified output returns OpenWeatherMap icon codes (e.g. `10d`). Build the image URL like so:
```
http://openweathermap.org/img/wn/{icon_code}@2x.png
```

## 🧱 Architecture

```
┌──────────────────┐     HTTPS     ┌─────────────────────────┐
│  Weather class   │ ────────────▶ │ OpenWeatherMap REST API │
│  (sunnyday-      │ ◀──────────── │ /data/2.5/forecast      │
│   calcetto)      │     JSON      └─────────────────────────┘
└──────────────────┘
        │
        ├── next_12h()              → full 4-step forecast (3h resolution)
        └── next_12h_simplified()   → [(time, temp, sky), ...]
```

## 📝 Notes

- The package name on PyPI is `sunnyday-calcetto`; the import name is `sunnyday`.
- Each forecast step covers a **3-hour window**, so `next_12h()` returns 4 data points.
- Be mindful of OpenWeatherMap's free-tier rate limit (60 calls/min, 1M calls/month).

## 👤 Author

**Denis Vreshtazi** — [GitHub](https://github.com/denisvreshtazi)

## 📜 License

MIT
