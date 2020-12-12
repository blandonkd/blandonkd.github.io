## Welcome to my portfolio!

My name is Keifer Blandon, and I am a cloud engineer for a small company in the Pacific Northwest. I am now in the capstone for my computer science degree with a specialization in software engineering. Since starting this program, I have been exposed to a wide swath of concepts and subjects and have been afforded the opportunity to add many tools to both my personal, and professional, toolbox. While much of the university curriculum is geared toward introduction to concepts rather than in-depth skill-building, I have been able to further pursue many of these foundational concepts and develop them into skills that I could be proud of. This portfolio serves as a visual exhibition of some of my work in a simple, yet concise, showcase. As it stands now, I am not a software engineer, in title, nor do I believe I will be in the future. However, having transitioned into the cloud computing environment, I am able to marry the skillet that I have built here within the structure of Southern New Hampshire University with my cloud-bases skillset that I have built within the industry to focus on cloud devops.

While there is little to no direct group collaboration required by the university, many of my classmates and I have unofficially collaborated on a multitude of large assignments throughout our coursework. We have been able to identify how our skillsets and backgrounds compliment each other’s and were often able to overcome many issues without instructor intervention. Our interactions were all done remotely via the provided course tools within our learning environment, mostly consisting of semi-public forum-based communication. While this level of interactions is rarely required by the course curriculum, the benefits that I and my fellow students gained in both knowledge and networking could not be understated. A prominent example of this is during one of our courses that we had to develop a no-SQL database using MongoDB and made calls to the database utilizing a RestAPI that we built. Our curriculum material had a myriad of typos and errors which rendered the material unusable. With collaboration between ourselves, we managed to completely ignore the provided material and not only overcome the task, but also gained valuable insight into how the database and the API worked together to help with future troubleshooting.

One of the recurring themes throughout the computer science coursework is being put into a scenario where stakeholders are either requesting a product or requesting information about a product that we provide. In the case of requests for information, I have answered official requests for information (RFIs) and have created reports to showcase what I can provide as well as attempt to reconcile their request with what I have the ability to provide. On the product side, I have worked on many occasions with development rubrics or product requirements that a client has given us to meet. An example here was that I developed a mobile application for a weight-tracking application. There was a very robust set of product requirements that we had to meet, but the overall theme and layout of the product was left to our own creativity. This was a valuable experience for me as it taught me that I can have high ambitions for how I would like my product to turn out, but when restricted by schedule and the requirements of the stakeholder, I was forced to trim back some of my ambition to be able to meet the requirements for the product. 
	
As I alluded to previously, the curriculum introduces us to a variety of concepts on a surface level, and part of that is the different ways that code can be structured but still maintain the same overall function. This overarching concept is often referred to as data structures and algorithms. The main point that is driven home consistently is that there are enumerable ways to structure data. Some are more efficient than others while some are secure while others are not. We can use pre-built algorithms that have been debugged and are widely used throughout the industry, or we can elect to build it ourselves from scratch. One of the most important takeaways from this is that there is no one-size-fits-all answer to how your code should be structured. There are many industry standards and best practices that help to create an arena in which to operate, but those are subject to the organization for which you work or the standards that must be met by the software. This is exemplified in my weather station project where I elected to use a basic JSON format for my data collection, a CanvasJS API for the dashboard and a loop system for the main Python file. Every one of those decisions could have been altered and different language or structure could have been used, but it was my decision to use the ones that I did.

This same mentality can be applied to the overall software engineering aspect of my work. The beautify of software is that it affords a lot of personalization while still adhering to a standard or product requirement. The software I or my team creates may meet the standard our client has set for the end product, but the product itself will always have a bit of personality that is specific to me or my team. All of that being said, software engineering is not just about building software from nothing, it also applies to product improvement. These improvements can come in the form of security, efficiency, file size, or really any structure or structures that can be bettered in some way. I have found that in my personal software journey, that I build software that at the time seems to be the pinnacle of my achievement, but later, as my skills improve, I look back and see the many different ways in which my software is lacking and be better.

Databases are, in my opinion, one of the more straightforward concepts that I have learned in my time at SNHU. With databases our choice of database comes down to two major options, they being SQL or no-SQL. The choice of which one to use is completely dependent on the application, the supporting software, the desired API, and even just personal preference. In my coursework I had the opportunity to work with both SQL and no-SQL databases and both had their own pros and cons. As stated previously, I and my classmates had to work with a MongoDB database being called with a RestAPI that we built, but prior to that I had worked on a normal SQL database with a very straightforward structure and build. 

The last major concept that we covered throughout my time in my computer science degree was security. Security in software, or IT in general, is such a broad-reaching and complex subject that there are entire degrees and fields of work dedicated to mastering its complexities. To that end, this university curriculum could only scratch the surface of what cybersecurity entails with the limited time we have together. Even with that being said, the curriculum does do a great job of introducing us to the major fundamental ideologies and best practices to at least not be blind to the world of security. In this capacity I have learned many of the major standards that apply to a typical code project, whether they be pointer control, memory allocation and management, or variable instantiation and control. While I am not, nor do I claim to be, an expert in cybersecurity, the simple fact that I am aware of my great shortcomings in this capacity allow me to be cognizant, if nothing else, of where my code is potentially vulnerable. I would hope that as I continue to build my skills in software development that my understanding and application of coding security practices grows in tandem.
	
Finally, we are down to the opus of this site. Below is a project that I have been working on over the last couple of months to not only showcase my skillset, but to also provide a useful device to use in my home. The project is explained in the different sections below, but the overall concept is that this device is a weather station. The device is built on a Raspberry Pi board using a GrovePi attachment along with its sensors. The main program is written in Python while the database is stored in JSON and the display module is written in HTML. The core file, written in python, is a personal showcase of my decision-making with regard to the language I chose, the data and algorithm structure I elected to use, along with certain design decisions that could have been different had somebody with a different skillset or imagination could have made. Here I can show my comfort in writing in Python along with various libraries, including the GrovePi library, to accomplish a task in the physical world. For exhibition of my database, I elected to use a no-SQL database style due to its flexibility and minimal upkeep requirements in tandem with its ability to be called by various APIs without much fuss. Finally, I have an added HTML dashboard that displays the collected data from the project into a convenient and aesthetically pleasing layout that is simple yet functional. This project not only showcases my ability to work in different part of a stack, but also shows how I can work within a multitude of languages and have them all work together. Along with my language support, this also shows that I can work in both the back end and the front end of a project. As it stands, this is only the current iteration of my project. Up until now it has gone through a fair number of changes and revisions along with some experimentation, and I will likely continue that trend as I add or remove functionality to implement this device into my house.

### My Weather Station Project

This project is a very functional device that records the ambient temperature and humidity and, utilizing an LED light array, qualitatively indicates various conditions. Additionally, the device also collects this temperature and humidty data and is displayed in a web browser for quantitative data analysis. The project is written in Python for the main source file, stores information by use of a JSON-based database in a separate file for data collection, and outputs a visual representation to a web browser by way of an HTML script. The project is not overly complicated, but its functionality is really what I was aiming for. For a full code review of this project, please head on over to my YouTube page (link below) where I break down this project and its functionality and some explanation of improvements I made on the road to get to this final, polished version. 

[Code Review](https://www.youtube.com/watch?v=3PjhI__jI1g&feature=youtu.be&ab_channel=KeiferBlandon)

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
The dashboard is an HTML file utilizing the CanvasJS API. This dashboard takes the outputted data that is collected in JSON and outputs it to a web browser showing two different graphs. The first graph is temperature over time and the second is humidity over time. For this layout I used a line chart and mapped the time-stamp value to the X axis and either temperature or humidy to the Y axis. Below is an example of the output seen on a web browser.

![Dashboard Example](https://github.com/blandonkd/blandonkd.github.io/blob/main/DashboardExample.png)

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
