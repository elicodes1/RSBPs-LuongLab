# Raspberry Pi Pico Multi-Channel Temperature Logger

A low-power, multi-channel temperature data logger built on MicroPython. This project reads up to five NTC thermistors (via an HW-178 multiplexer), monitors battery voltage, and writes time-tagged (or elapsed-time) readings to a microSD card. It uses a DS3231 RTC for accurate timing, a push-button to start logging, and an LED for status indicators. Deep-sleep between cycles maximizes battery life, with an automatic shutdown at a configurable low-SOC threshold.

## Features
- **5-channel thermistor measurements** with per-sensor calibration offsets  
- **Battery voltage & SOC monitoring** via ADC + resistor divider  
- **DS3231 RTC** for timestamping (or elapsed-time counter mode)  
- **microSD logging** in CSV format with flexible headers  
- **Start button & LED** blink codes for user feedback  
- **Deep-sleep scheduling** between readings (configurable interval)  
- **Low-battery shutdown** to protect your pack  

## Hardware
- Raspberry Pi Pico  
- HW-178 analog multiplexer  
- 5× NTC thermistors + pull-up resistors  
- DS3231 RTC module (I²C on GP14/GP15)  
- microSD card breakout (SPI on GP10–13)  
- Push-button (GP16) & LED (GP20)  
- 18650 battery pack + 10 kΩ/10 kΩ divider  

## Getting Started
1. **Clone this repo** to your Pico’s filesystem.  
2. **Edit `main.py`** to set your desired `LOG_INTERVAL`, `NUM_THERM`, and `LOW_SOC_LIMIT`.  
3. **Wire up** the thermistors, multiplexer, RTC, SD card, button, LED, and battery divider as per the pin comments.  
4. **Press the start button** after power-on; the LED will flash 5× and begin logging.  
5. **Retrieve `log.csv`** from the `/sd` folder to analyze your temperature and battery data.  

---

Feel free to tweak any constants in the “USER CONFIG” section at the top of `main.py`. Enjoy precise, off-grid temperature monitoring!  
