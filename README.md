<!--
JavaScript Digital Clock Lab

Level: Beginner
Created: June 15, 2016
Author/Instructor: Dawn Milnamow

Tools Required: Sublime Text Editor, Google Chrome


Description: This lab will use concepts covered in the Introduction to JavaScript workshop including variables, functions, strings, etc. By completing this lab, you will have a fully functioning digital clock running from a html page in your Chrome Browser. Tip: Save your work often.


Set-up:
1. Open Sublime Text and create a new file named "index.html".
2. Create a new folder named "js", and in that folder create a file named "myClock.js".

3. In your newly created html file, begin typing <html until you see a pop-up "html" and press Enter.
4. After the <head> tag, create a reference to myClock.js, as seen below:
	
			<script type="text/javascript" src="js/myClock.js"></script>

5. After the <body> tag, create a div tag with "clock" as its id, as seen below:

			<div id="clock"></div>

6. Save.


Implement JavaScript Clock functions:
1. First, we need a function that will start the clock time every time we open the page. Follow the below steps. If needed, you can see how this is done further below.

	a. In myClock.js, create a function called "startMyDigitalClock" which takes no arguments. 
	b. In the startTime function statements block, create a variable called "today", and set it equal to a new instance of Date, represented by "new Date()".

	Since we are providing no arguments, new Date() creates a JavaScript Date object for the current date and time according to the time known to the computer where the JavaScript is executed. All Date instances inherit properties and methods from Date.prototype. We will use these methods and properties to build out our startTime function.


			function startMyDigitalClock() {
				var today = new Date(); 
			}

	c. In the startMyDigitalClock function, make three variables to hold the current hours, minutes, and seconds. Use the getter methods of Date on the object we created. Below shows how this is done for hours.

			var currentHours = today.getHours();  
			//date hours are given as 0 - 24

	d. Add another variable for the meridiem. We will set this equal to a function called meridiemCheck which takes one argument, the current hour. We will implement this function outside of the startMyDigitalClock function.

2. To format a 12-hour clock,

	a. Create a new function, checkMeridiem, that will take one input argument, the current hour. In the statements, we check the value passed in and return either AM or PM. See below for how we use the if/else statment for this.

			function meridiemCheck(i) {
				if (i < 12) { return "AM" }
					else { return "PM" }
			}

	b.  In the startMyDigitalClock function, add another variable for the meridiem. Set this equal to a call to the meridiemCheck taking the current hours reference we created in step 1c.

			var meridiem = meridiemCheck(currentHours);

	c. Create another function, convertToTwelveHourClock, which takes one input argument, the current hour. Implement this function to return 12 if the current hour is 0, and shows the correct number for hours 13 and higher.

			function convertToTwelveHourClock(i) {
				if (i == 0) {
					i = 12;
				} else if (i > 12) {
					i -= 12;
				}
				return i;
			}

	d. In the startMyDigitalClock function, reassign the currentHours variable to equal a call to the convertToTwelveHourClock taking currentHours as the input.

3. To add leading zeros to your clock (01, 02, etc.) hours, minutes and seconds,
	
	a. Create a new function, leadingZeroCheck, which takes one input argument. Implement this function to add a "0" to any input value less than 10, and return this value.

			function leadingZeroCheck(i) {
				if (i < 10) {
					i = "0" + i;
				}
				return i;
			}

	b. In the startMyDigitalClock function, reassign the currentHours, currentMinutes, and currentSeconds reference variables to a call to the leadingZeroCheck. An example for the current minutes is shown below.

			currentMinutes = leadingZeroCheck(currentMinutes);

4. To have the clock displayed in the 00:00:00 AM format we expect,

	a. Create a function, displayClock, which takes 4 input arguments to represent the hour, minute, second, and meridiem.
	In the implementation, we need a reference to the div we created in Set-up step 5.

		function displayClock(hour, min, sec, amPM) {
		var clockDiv = document.getElementById('clock');
		clockDiv.innerHTML = 
		}

		//finish the right side of the equals sign to format 
		//the display correctly using the input arguments

	b. In the startMyDigitalClock function, make a call to the displayClock function taking the appropriate variable references.

5. Make the clock tick, 

	a. In the startMyDigitalClock function, add the following line of code:

		window.setInterval(startMyDigitalClock, 1000);
		//Tells the system to run the startMyDigitalClock function every 1000ms (1s)

	b. In the index.html, add to the opening body tag:

		<body onload="startMyDigitalClock()"> 

	c. Ensure all files are saved. 

	d. Right click on the index.html file and select "Open in Browser" to see your clock running.

-->