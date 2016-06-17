#JavaScript Digital Clock Lab

Level: Beginner

Created: June 15, 2016

Author/Instructor: Dawn Milnamow


Tools Required: *Sublime Text Editor, Google Chrome*


**Description:** This lab will use concepts covered in the Introduction to JavaScript workshop including variables, functions, strings, etc. By completing this lab, you will have a fully functioning digital clock running from a html page in your Chrome Browser. 

*Tip: Save your work often.*


#####Set-up:  Follow the below steps to set up your project environment

1. First, we need a folder location on our Desktop that we can save all of our dev projects. Create a folder called 'dev'. Inside this folder, create a folder for this project called 'JavaScript-DigitalClock-Lab'.
	
	a. To create a new folder: Right click somewhere on your Desktop, select 'New Folder'.

	b. Type the name of your new folder, 'dev'.

	c. Double click into your 'dev' folder.

	d. Right click anywhere in the folder, select 'New Folder'. Name this folder 'JavaScript-DigitalClock-Lab'. This is your project folder for today's lab where you will be saving all of your work.

2. Open Sublime Text and create a new file named 'index.html'.

	a. Click File, select 'New File'.

	b. Click File, select 'Save As...'

	c. Type 'index.html' into the file name. Select the project folder you created in step 1. Click 'Save'. Note: If you cannot find the folder while initially trying to save, that is okay. Save it to another location where you can find the file. Open the 'JavaScript-DigitalClock-Lab' folder in another window and then click and drag the file into that folder.

3. In your newly created html file, begin typing <html until you see a pop-up "html" and press Enter.

4. After the opening head tag, create a reference to myClock.js, as seen below:
	
			<script type="text/javascript" src="js/myClock.js"></script>

5. After the opening body tag, create a div tag with "clock" as its id, as seen below:

			<div id="clock"></div>

6. Save the changes you have made in index.html. (Ctrl+S or File>Save)

6. Create a new folder within your project folder named 'js'.

7. In Sublime Text, create a new file inside your newly created 'js' folder named "myClock.js".



#####JavaScript Implementation:  Follow the below steps to build out your functional clock

1. First, we need a function that will start the clock time every time we open the page. 

	a. In myClock.js, create a function called "startMyDigitalClock" which takes no arguments.

	b. In the startTime function statements block, create a variable called "today", and set it equal to a new instance of Date, represented by "new Date()".

	Since we are providing no arguments, new Date() creates a JavaScript Date object for the current date and time according to the time known to the computer where the JavaScript is executed. All Date instances inherit properties and methods from Date.prototype. We will use these methods and properties to build out our startTime function.

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
		//Tells the window to refresh using the startMyDigitalClock function every 1000ms (1s)

	b. In the index.html, add to the opening body tag:

		<body onload="startMyDigitalClock()"> 

	c. Ensure all files are saved. 


#####Deploy, Debug, and Prettification!:

1. DEPLOY: Right click on the index.html file and select 'Open in Browser' to see your clock running.

2. DEBUG: It is very common that we have missed a step, have a spelling error, have issue with syntax, or have errors in our overall implementation. If your clock is not appearing as expected, this is a great opportunity to learn how to *debug your code*. Follow these steps to debug:
	
	a. In your Chrome browser, right click anywhere in the window and select 'Inspect'.

	b. Click 'Console'. Here you will see logged errors. An example is provided below:

		Uncaught ReferenceError: hours is not defined  myClock.js:13 
	
		//Based on the error shown above, I can assume that I have a reference, 'hours', 
		// provided at line 13 in myClock.js that has not been declared as a variable
		// before this line.

	c. After editing your code, save then refresh your browser.

3. PRETTIFICATION: To make your clock look a bit flashier than the straight text, we can create a new file, prettifyMyClock.css. Since this is a JavaScript course, you can try out the CSS I created just for fun: 

			body {
    			background-color: white;
			}

			#clock {
			    height: 500px;
			    width: 800px;
			    margin: auto;
			    position: absolute;
			    top: 0; left: 0; bottom: 0; right: 0;
			    font-family: courier, monospace;
			    text-align: center;
			    color: #000066;
			    font-size: 100px;
			    font-weight: bold;
			}

			@keyframes animatedBackground {
			    from { background-position: 0 0; }
			    to { background-position: 100% 0; }
			}

			#animate-area   { 
    			width: 100%; 
   				height: 400px; 
    			background-image: url(http://jqueryplugin.net/wp-content/uploads/2014/07/Cute-Moving-Cloud-animation-with-blue-background-using-css.jpg);
    			background-position: 0px 0px;
    			background-repeat: repeat-x;

   				animation: animatedBackground 40s linear infinite;
			}


The solution to this lab can be found on GitHub:
https://github.com/dawnmil/JavaScript-DigitalClock-Solution




######More Practice with JS:

I hope you enjoyed learning the basics of JavaScript. Here are some ways you can continue learning JavaScript after today:

1. Add to your clock. One way you can practice is simply by expanding upon today's lab. Try adding additional clocks in various time zones, clocks with other date formats, a stop watch, or an alarm clock.

2. Want more JavaScript? Check out the below JavaScript learning tools:

	a. Free JS Tutorials at CodeCademy: https://www.codecademy.com/learn/javascript

	b. Free Animate Drawings using JS at KhanAcademy: https://www.khanacademy.org/computing/computer-programming/programming

	c. Reccommended Reading: *JavaScript: The Good Parts*, Douglas Crockford

