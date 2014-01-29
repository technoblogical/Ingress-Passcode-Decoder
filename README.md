Ingress-Passcode-Decoder
========================

This is some JavaScript that turns Ingress passcodes into something usable to get supplies in the game.<br/>
by <a href='https://plus.google.com/104536213394512642005?rel=author'>Chris Walker</a><br/>

This is some jQuery/JavaScript that I wrote to turn the Ingress Passcodes into the Passcodes that you use to get supplies to the game.

##How Does This Thing Work?
Well, It's a webpage and pretty simple one at that. You open it in your browser. It is not supported in Internet Explorer 9 or before. <a href="http://decodeingress.me/2014/01/28/passcode-decoding-walkthrough-0001-1/" target="_blank">You can read the whole thing here</a>. It talks about the whole thing, and explains a little bit about. Really, it's pretty nerdy and I only understand half of it myself. But hey, any excuse to write some JavaScript, right?

###Directions...
1. Download the code
2. Stick into a webpage
3. Open the web page
4. Consume all media associated with a game that pull you away from all those you hold dear for a poorly visible alpha-numeric code that you wouldn't really notice if you were a casual viewer.
5. Closely inspect that media 53 more times just to make sure you didn't miss that code.
6. Do you stink? When was the last time you took a shower. Or shaved. Maybe you should do that. What time is it?
7. Jeez. It's daylight out. Have I been up all night? Well, at least I can go to the park now to play more Ingress.

####License
Copyright (c) 2013 Chris Walker

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.


<img src='https://lh6.googleusercontent.com/-NoJxB98RGC8/UMDEznmPTiI/AAAAAAAAAcQ/cfDucT8eu4A/s800/squinty.jpg'><br/>
<img src='https://lh6.googleusercontent.com/-g7q_OQGsehU/Uug7ID5J_EI/AAAAAAAAKIs/jPm4pB8Caps/s400/Ingress-Passcode-Decoder.PNG'>

		<!-- This should turn the Ingress passcode 'xDZt4Ovws5urijtwcDKn' into '6GBY2HENRYZ8O7W' which is usable to get items-->
		<form>
			<div>Put in the data here:<br/><input type="text" id="originalCode"></div> <!--SECRET CODE GOES HERE-->
			<div>Get the data from here:<br/><input type="text" id="newCode"></div> <!--SECRET OUTPUT APPEARS HERE-->
		</form>
		<div id='button' style='background:#888;width:150px;color:#fff;text-align:center;border:2px outset #888;'>Run that sucka!</div>
	</body>
	<script type='text/javascript'> //Begin JavaScript Now!
	 $('#button').click(function(){ //When clicked...
	 	var thingInNeed = $('#originalCode').val();//get the value of the first box
	 	thingInNeed = thingInNeed.split('');//Splits all the letters into an array
	 	var numberCounter=0; //We need a counter
	 	$(thingInNeed).each(function(){ //run through the the elements (or letters) of the array
	 		switch(true){ //Hey it's a switch statement. We always use true, right? Because we want the stuff below to be true.
	 			case (/^[a-z]+$/.test(thingInNeed[numberCounter])): //This regex scans the letter to see if it's lowercase.
	 				thingInNeed[numberCounter]=thingInNeed[numberCounter].toUpperCase();//if it is, it's true and runs this stuff
	 				break; //end the switch statement.
	 			case (/^[A-Z]+$/.test(thingInNeed[numberCounter])): //Same deal but uppercase letters
	 				thingInNeed[numberCounter]=thingInNeed[numberCounter].toLowerCase(); //Switch those to lower case
	 				break; 
	 			default: //Usually there's a default option. I think default required, but doesn't HAVE to do anything.
	 		}
	 		numberCounter++; //increment the number counter so we can move on to the next letter in the array.
	 	}); //End the each statement.
	 	thingInNeed = thingInNeed.reverse(); //Flip it!
	 	thingInNeed=thingInNeed.join(''); // Join it!
	 	thingInNeed = window.atob(thingInNeed);// Rub it down! Oh no, this just does the conversion to Base64 encoding.
	 	$('#newCode').val(thingInNeed); //Plugs it into the second box so the user can see it.
	 }); //This is the end of that 'When clicked...'
	</script> <!-- This is the end of the JavaScript -->