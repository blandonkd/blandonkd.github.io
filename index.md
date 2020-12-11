## Welcome to my portfolio!

This page is an amalgamation of my work throughout my coursework at Southern New Hampshire University.

### My Weather Station Project

This project is a very functional device that records the ambient temperature and humidity and, utilizing an LED light array, qualitatively indicates various conditions. Additionally, the device also collects this temperature and humidty data and is displayed in a web browser for quantitative data analysis. The project is written in Python for the main source file, stores information by use of a JSON-based database in a separate file for data collection, and outputs a visual representation to a web browser by way of an HTML script. The project is not overly complicated, but its functionality is really what I was aiming for. For a full code review of this project, please head on over to my YouTube page where I break down this project and its functionality and some explanation of improvements I made on the road to get to this final, polished version. 

[CodeReview](https://www.youtube.com/watch?v=3PjhI__jI1g&feature=youtu.be&ab_channel=KeiferBlandon)

#### The Source File
I have below the Python source code for the weather station that I built using a Raspberry Pi 3, a GrovePi hat, along with various sensors, and all written in Python. The overall functionality of the program is that it utilizes one main loop with various nest loops that add additional functionality by way of interrupts or time delays. The device is designed only to collect data during light hours, so an interrupt was written in to effectively keep the device sleeping until the light sensor indicates daylight.

```python
# Author:           Keifer Blandon
# Institution:      Southern New Hampshire University

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

#### The Database
The program written for my RPi project incorporates data storage by way of outputting the collected environmental information to a file, structured in JSON. Below is an example of the output for the database. The data is collected in sets of 3. The first value is the time stamp which is simply a incremental counter. The only purpose for that is to be able to plot the data collected over time, rather than relative to the other data. The second value is the ambient temperature in Fahrenheit and the final value is the ambient humidity in percent.

```json
[[0, 73.4, 48.0], [1, 73.4, 48.0], [2, 73.4, 48.0], [3, 73.4, 48.0], [4, 73.4, 52.0], [5, 73.4, 58.0], [6, 75.2, 57.0], [7, 75.2, 55.0], [8, 75.2, 54.0], [9, 75.2, 81.0], [10, 75.2, 75.0], [11, 75.2, 67.0], [12, 75.2, 64.0], [13, 75.2, 70.0], [14, 75.2, 95.0], [15, 75.2, 80.0], [16, 75.2, 72.0], [17, 75.2, 69.0], [18, 75.2, 66.0], [19, 75.2, 65.0], [20, 75.2, 63.0], [21, 75.2, 61.0]]

```

#### The Dashboard File
The dashboard is an HTML file utilizing the CanvasJS API. This dashboard takes the outputted data that is collected in JSON and outputs it to a web browser showing two different graphs. The first graph is temperature over time and the second is humidity over time. For this layout I used a line chart and mapped the time-stamp value to the X axis and either temperature or humidy to the Y axis. 

```html
<!DOCTYPE HTML>
<html>
<head>
<!--Imports for javascript-->
<script type="text/javascript" src="https://canvasjs.com/assets/script/jquery-1.11.1.min.js"></script>
<script type="text/javascript" src="https://canvasjs.com/assets/script/canvasjs.min.js"></script>
<script type="text/javascript">

window.onload = function () {

// Establish arrays for different data sets
var tempDataPoints = [];
var humDataPoints = [];

// Parse time and temperature data from data file and set to array
$.getJSON("outputData.json", function(data) {  
	$.each(data, function(key, value){
		tempDataPoints.push({x: value[0], y: parseInt(value[1])});
	});
	// Use CanvasJS API
	var chart = new CanvasJS.Chart("chartContainer1",{
		title:{
			text:"Plotting Temperature Over Time"
		},
		// Draw line chart with temperature data array
		data: [{
			type: "line",
			dataPoints : tempDataPoints,
		}]
	});
	chart.render();
});

// Parse time and humidity data from data file and set to array
$.getJSON("outputData.json", function(data) {  
	$.each(data, function(key, value){
		humDataPoints.push({x: value[0], y: parseInt(value[2])});
	});
	// Use CanvasJS API
	var chart = new CanvasJS.Chart("chartContainer2",{
		title:{
			text:"Plotting Humidity Over Time"
		},
		// Draw line chart with humidity data array
		data: [{
			type: "line",
			dataPoints : humDataPoints,
		}]
	});
	chart.render();
});
}
</script>

</head>
<body>
<!-- Div container for temp chart -->
<div id="chartContainer1" style="height: 300px; width: 100%;"></div>
<!-- div container for humidy chart -->
<div id="chartContainer2" style="height: 300px; width: 100%;"></div>
</body>
</html>

```
