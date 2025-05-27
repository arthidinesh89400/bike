
# Smart Bike Project

## Description
This Python project is part of a smart bike system focused on controlling the bike's lights using a Raspberry Pi.

## Features
- Light control via GPIO
- Simple command line interface
- Can be extended with sensors or automation

## Usage
Run the script:

```bash
python3 lights_control.py
# lights_control.py

import RPi.GPIO as GPIO
import time

LIGHT_PIN = 18

def setup():
    GPIO.setmode(GPIO.BCM)
    GPIO.setup(LIGHT_PIN, GPIO.OUT)

def turn_on():
    GPIO.output(LIGHT_PIN, GPIO.HIGH)
    print("Lights ON")

def turn_off():
    GPIO.output(LIGHT_PIN, GPIO.LOW)
    print("Lights OFF")

try:
    setup()
    while True:
        user_input = input("Type 'on' or 'off': ").strip().lower()
        if user_input == 'on':
            turn_on()
        elif user_input == 'off':
            turn_off()
        else:
            print("Invalid input")
except KeyboardInterrupt:
    GPIO.cleanup()
    print("Program stopped")
