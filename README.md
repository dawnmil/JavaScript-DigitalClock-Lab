#JavaScript Digital Clock Lab

Level: Beginner

Created: June 15, 2016

Author/Instructor: Dawn Milnamow


Tools Required: *Any Text Editor, Google Chrome*


###**Description:** This lab will use concepts covered in the Introduction to JavaScript workshop including variables, operators, strings, objects, and functions. By completing this lab, you will have a fully functioning digital clock running from a html page in your Chrome Browser. 

*Tip: Save your work often.*

###DEPLOY & DEBUG: At any time during this lab, we can check if our code is working and debug within our browser by following the below steps

1. To deploy, right click on the index.html file and select 'Open in Browser'. This needs only to be done once. As you save your changes, simply refresh your browser to see the updated code working in your browser. 
*Note: Right now, we should only see a blank white window*

2. Debugging: It is very common that we have missed a step, have a spelling error, have issue with syntax, or have errors in our overall implementation. If your clock is not appearing as expected, this is a great opportunity to learn how to *debug your code*. Follow these steps to debug:
	
	a. In your Chrome browser, right click anywhere in the window and select 'Inspect'.

	b. Click 'Console'. Here you will see logged errors. An example is provided below:

		Uncaught ReferenceError: hours is not defined  myClock.js:13 
	
		//Based on the example error shown above, I can assume that I have a reference, 'hours', 
		// provided at line 13 in myClock.js that has not been declared as a variable
		// before this line.

	c. After editing your code, save then refresh your browser.

###JavaScript Implementation:  Follow the below steps to build out your functional clock

1. First, we need a function that will start the clock time every time we open the page. 

	a. In myClock.js, create a function called "startMyDigitalClock" which takes no arguments.

	b. In the startMyDigitalClock function statements block, create a variable called "today", and set it equal to a new instance of Date, represented by "new Date()".

	Since we are providing no arguments, new Date() creates a JavaScript Date object for the current date and time according to the time known to the computer where the JavaScript is executed. All Date instances inherit properties and methods from Date.prototype. We will use these methods and properties to build out our startMyDigitalClock function.

			function startMyDigitalClock() {
				var today = new Date(); 
			}

	c. In the startMyDigitalClock function, make three variables to hold the current hours, minutes, and seconds. Use the getter methods of Date on the object we created. Below shows how this is done for hours.

			var currentHours = today.getHours();  
			//date hours are given as 0 - 24


2. To format a 12-hour clock,

	a. Create a new function, checkMeridiem, that will take one input argument, the current hour. In the statements, we check the value passed in and return either AM or PM. See below for how we use the if/else statment for this.

			function meridiemCheck(i) {
				if (i < 12) { return "AM"; }
					else { return "PM"; }
			}

	b.  In the startMyDigitalClock function, add another variable for the meridiem. Set this equal to a call to the meridiemCheck taking the current hours reference we created in Implementation step 1c.

			var meridiem = meridiemCheck(currentHours);

	c. Create another function, convertToTwelveHourClock, which takes one input argument, the current hour. Implement this function to return 12 if the current hour is 0, and shows the correct number for hours 13 and higher.

			function convertToTwelveHourClock(i) {
				if (i === 0) {
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
		//Tells the window to refresh using the startMyDigitalClock function every 1000ms (1s)

	b. Ensure all files are saved. 


###STYLE YOUR CLOCK: Just for fun, lets add the below CSS to see how it changes the look and feel of our clock

1. In your index.html, uncomment ONE of the style sheets by removing '!--' from the start of the tag and removing '--' from the end of the tag.

	Example:
	- Commented-Out Stylesheet:
			<!--link href="./style/scrolling-clouds.css" type="text/css" rel="stylesheet"-->
	- Uncommented:
			<link href="./style/scrolling-clouds.css" type="text/css" rel="stylesheet">

2. Save, and
3. Refresh your browser


The solution to this lab can be found on GitHub:
https://github.com/dawnmil/JavaScript-DigitalClock-Solution




####More Practice with JS:

I hope you enjoyed learning the basics of JavaScript. Here are some ways you can continue learning JavaScript after today:

1. Add to your clock. One way you can practice is simply by expanding upon today's lab. Try adding additional clocks in various time zones, clocks with other date formats, a stop watch, or an alarm clock.

2. Want more JavaScript? Check out the below JavaScript learning tools:

	a. Free JS Tutorials at CodeCademy: https://www.codecademy.com/learn/javascript

	b. Free Animate Drawings using JS at KhanAcademy: https://www.khanacademy.org/computing/computer-programming/programming

	c. Recommended Reading: *JavaScript: The Good Parts*, Douglas Crockford

