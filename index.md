## Welcome to my portfolio!

This page is an amalgamation of my work throughout my coursework at Southern New Hampshire University.

### My Weather Station Project
To showcase my work, I have below the source code for the weather station that I built using a Raspberry Pi 3, a GrovePi hat, along with various sensors, and all written in Python 3.

```python
# Author:           Keifer Blandon
# Institution:      Southern New Hampshire University
# Last Updated:     29 Nov 2020
# Class:            CS499 Computer Science Capstone

import time
import math
import json
import grovepi
from grovepi import *

# The Grove Temperature & Humidity Sensor Pro is connected to digital port D6
# SIG,NC,VCC,GND
sensor_temp_hum = 6

# Grove Base Kit comes with the blue temp/humidity sensor.
sensor_color_blue = 0    # The Blue colored sensor.

# Grove LEDs connected to digital ports D2, D3, and D4
led_red = 2
led_blue = 3
led_green = 4

# Grove Light Sensor connected to analog port A0
# SIG,NC,VCC,GND
sensor_light = 0

# Turn on LED once sensor exceeds threshold resistance
# The threshold should be adjusted over time to account for shadows or similar
# The number 30 is mostly arbitrary just to lower sensitivity
threshold = 30

# Make a generic counter for allowing data over time collection
time_stamp = 0

grovepi.pinMode(sensor_light,"INPUT")
grovepi.pinMode(led_red,"OUTPUT")
time.sleep(1)

#Establishes JSON and JSON array
outputData = {}
outputData = []

while True:
    try:
        # Get sensor value
        sensor_value = grovepi.analogRead(sensor_light)
        # Calculate resistance of sensor in K
        resistance = (float)(1023 - sensor_value) * 10 / sensor_value

        # This project uses the blue colored sensor.
        # The first parameter is the port, the second parameter is the type of sensor.
        [temp,humidity] = grovepi.dht(sensor_temp_hum,sensor_color_blue)

        # Conversion of temperature from celcius to fahrenheit
        temp = (temp * 9/5) + 32

        # Do not record data when it is dark out
        # Interrupt loop to keep busy while dark out so no data is recorded
        while resistance > threshold:
                # Get sensor value again
                sensor_value = grovepi.analogRead(sensor_light)
                # Calculate resistance of sensor in K again to perform loop check
                resistance = (float)(1023 - sensor_value) * 10 / sensor_value
                time.sleep(1)


        if math.isnan(temp) == False and math.isnan(humidity) == False:
            # Prints current time stamp
            print(time_stamp)
            #Prints temp/humidity to console as well for comparision and troubleshooting
            print("temp = %.02f F humidity =%.02f%%"%(temp, humidity))

        #Light up only green LED if conditions are met
        if 60.0 < temp < 85.0 and humidity < 80.0:
        # Send HIGH to switch on green LED and LOW to red and blue
            grovepi.digitalWrite(led_green, 1)
            grovepi.digitalWrite(led_blue, 0)
            grovepi.digitalWrite(led_red, 0)

        #Light up only blue LED if conditions are met
        elif 85.0 < temp < 95.0 and humidity < 80.0:
            #Send HIGH to switch on blue LED and LOW to green and red
            grovepi.digitalWrite(led_green, 0)
            grovepi.digitalWrite(led_blue, 1)
            grovepi.digitalWrite(led_red, 0)

        #Light up only red LED if conditions are met
        elif temp > 85.0:
            #Send HIGH to switch on red LED and LOW to green and blue
            grovepi.digitalWrite(led_green, 0)
            grovepi.digitalWrite(led_blue, 0)
            grovepi.digitalWrite(led_red, 1)

        #Light up green and blue LEDs if conditions are met
        elif humidity > 80.0:
        #Send HIGH to switch on blue and green LEDs and LOW to red
            grovepi.digitalWrite(led_green, 1)
            grovepi.digitalWrite(led_blue, 1)
            grovepi.digitalWrite(led_red, 0)

        else:
        # Send LOW to switch off all LEDs
            grovepi.digitalWrite(led_green,0)
            grovepi.digitalWrite(led_blue, 0)
            grovepi.digitalWrite(led_red, 0)

        # Prints sensor value and resistance to terminal for analysis and troubleshooting
        print("sensor_value = %d resistance = %.2f" %(sensor_value,  resistance))
        time.sleep(1.0)

        # Output data to JSON file
        # Formatted for use in dashboard HTML file
        outputData.append([
            time_stamp,
			temp,
            humidity
            ])

        # Defines output file and directs JSON output
        with open('outputData.json', 'w') as outfile:
                json.dump(outputData, outfile)

        # Sleep for 5 seconds to space data collection
        time.sleep(5)

        # Increment time stamp for next iteration
        time_stamp = time_stamp + 1

    # Turn all LEDs off before stopping
    except KeyboardInterrupt:
        digitalWrite(led_red,0)
        digitalWrite(led_blue,0)
        digitalWrite(led_green,0)
        break

    # Print "Error" if communication error encountered
    except IOError:
        print ("Error")
```
