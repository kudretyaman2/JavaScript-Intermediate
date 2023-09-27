# JavaScript-Intermediate
Week 1 Day 1-Day 5

JAVASCRIPT INTERMEDIATE
WEEK1
DAY1-DAY5

POPUPS WINDOW METHOD 

•	A popup window is one of the oldest methods to show additional document to user.
•	Basically you just run: window.open(‘https://javascript.info/’) and it will run a new window  with a given URL.
•	It is difficult to use the popups on mobile phones since they don’t have simultaneously windows.
•	But there are still some parts that use the popups just like Facebook because:
o	Popup is a separate window with its java script environment.  You can open popup with an untrusted part its still safe.
o	Very easy to open popup 
o	Popup can navigate the URL and send message to an opener window.
Window.open
	Window.open(URL, name, params): Is the syntax to open a popup.
o	URL: is the one that is going to load into the window.
o	NAME: each window has a name, if the name already exists  the popup  will open on that existing window  otherwise  new window  will open. 
o	PARAMS:The configuration string for the new window. It contains settings, delimited by a comma. There must be no spaces in params, for instance: width:200,height=100.
o	Position: left/ top are numeric coordinates of the window top-left corner on the screen. Window cannot be positioned offscreen.
o	Width and height there is a limit on minimal width/height, so it’s impossible to create an invisible window.
Window features:
o	Menu bar: shows or hides the browser menu on the new window.
o	Toolbar: shows or hides the browser navigation bar (back, forward, reload etc) on the new window.
o	Location: shows or hides the URL field in the new window. FF and IE don’t allow to hide it by default.
o	Status: shows or hides the status bar. Again, most browsers force it to show.
o	Resizable: allows to disable the resize for the new window. Not recommended.
o	Scrollbar: allows to disable the scrollbars for the new window. Not recommended
Accessing popups from windows:
	The open call returns a reference to the new window.
	It can be used to manipulate its properties, change location and even more.
	In this example, we generate popup content from JavaScript:
•	Let newWin = window.open(“about:blank”, “hello”, “width=200,height=200”)’.

newWin.document.write(“Hello, world!”).
	And here we modify the contents after loading
•	Let newWindow = open(‘/’, ‘example’, ‘width=300,height=300’)
newWindow.focus();
Alert(newWin.location.href); // (*) about:blank, loading hasn’t started yet
newWindow.onload = function() {
 Let html = `<div style=”font-size:30px”>Welcome!</div>`;
 newWindow.document.body.insertAdjacentHTML(‘afterbegin’, html);
Let newWindow = open (‘/’, ‘example’, ‘width=300,height=300’)
newWindow.focus();
Alert (newWin.location.href); // (*) about:blank, loading hasn’t started yet
newWindow.onload = function () {
  Let html = `<div style=”font-size:30px”>Welcome! </div>`;
  newWindow.document.body.insertAdjacentHTML(‘afterbegin’, html);

};
	Windows may freely access content of each other only if they come from the same origin (the same protocol://domain:port).
	Otherwise, e.g., if the main window is from site.com, and the popup from gmail.com, that’s impossible for user safety reasons.
Accessing window from popup:
•	A popup may access the “opener” window as well using window.opener reference.
•	If you run the code below, it replaces the opener (current) window content with “Test”: let newWin = window.open(“about:blank”, “hello”, “width=200,height=200”);

newWin.document. write (

  “<script>window.opener.document.body.innerHTML = ‘Test’<\/script>”

);
So, the connection between the windows is bidirectional: the main window and the popup have a reference to each other.
Closing a popup:
•	To close a window: win.close().
•	To check if a window is closed: win.closed.
•	Technically, the close () method is available for any window.
•	But window.close() is ignored by most browsers if window is not created with window.open(). Only work on the popup
•	This code loads and then closes the window:
Let newWindow = open(‘/’, ‘example’, ‘width=300,height=300’);

newWindow.onload = function() {

  newWindow.close();

  alert(newWindow.closed); // true

};
Scrolling and resizing: 
There are methods that are used to move/resize the window:
Win.moveBy(x,y):
	Move the window to relative to the current position x pixel to right and y pixel down.
	Negative values are allowed (to move left/up)
Win.moveTo(x,y):
	Move the window to coordinates (x, y) on the screen.
Win.resixeBy(width, height):
	Resize the window by given width/height relative to the current size. 
	Negative values are allowed.
Win.resizeTo(width, height):
•	Resize the window to a given size.
•	There is a window.onresize event
Only popups:
•	We use them to prevent the abuse, they are usually bloc ked by the browser.
•	They work on popups that are reliable that have no additional tabs.
No minification/maximization:
•	JS has no way to minify or maximize a window
•	The move/resize method does not work for maximized/minimized windows.
Scrolling a window:
•	We discussed the window scrolling I the previous chapter, to add on the previous one  we have:
o	Win.scrollBy(x,y): Scroll the window x pixels right and y down relative the current scroll. Negative values are allowed.

o	Win.scrollTo(x,y): we scroll a  window  to a given coordinates(x,y)

o	Elem.scrollintoView(top=true): scroll the window to make the elem show up on  top by default or at the button can include elem.scrollintoView(false)

Focus/Blur on a window:
	Theoretically, there are window.focus() and window.blur() methods to focus and unfocus on a window.
	Focus or blur events they allow to focus a window and catch the moment when the visitor switched elsewhere.
	When the user unfocus on the window it brings it back  to focus, the intention is to lock the user  within the window.
 Things can be done:
	When we open a popup, it is might be a good idea to run a newWindow.focus() on it. 
	For some operating software or browsers, it ensures that the user is in the new window now.
	To track when a user visited the web app, we can use the  window.onfocus/onblur.
	Allows to suspend or resume the page activities, animinations.
Cross- window communication:
Same Origin:
	There are some URLs that have the  same origin, if they have the same protocol, domain and port.
	Example:
o	http://site.com
o	http://site.com/
o	http://site.com/my/page.html
	These below does not have the same origin:
o	http://www.site.com (another domain: www.matters)
o	http://site.org (another domain: .orgmatters)
o	https://site.com (another protocol: https)
o	http://site.com:8080 (another port: 8080)
	The “Same Origin” policy  state that:
o	If  we have a reference to another window, a popup created by window,open or window inside <iframe>, and that window comes from the same origin, we have a full  access to that window
o	But if it comes from another origin then we cannot access the  content of that window
o	We can change the location, but we cannot  read the location.
In Action: iFrame:
	The <iframe> it hosts its separate embedded window, with its own separate document and widow subject.
Properties to use:
•	iframe.contentWindow to get the window inside the <iframe>.
•	iframe.contentDocument to get the document inside the <iframe>, короткий аналог iframe.contentWindow.document.
•	when  we access something inside the embedded window, the browser checks if the iframe has the same origin.
•	If is that so the access denied.
Window on subdomains:Document.Domain
	By defining, two URLs with different domains have different origins.
	But if the sites  share the same second-level domain,  example(john.site.com and peter.site.com) we can make the browser ignore that difference.
	So that they can be treated as if they come from same origin, for the purpose of cross window communication
	To make that  work each code should run document. Domain=('site.com’)
Iframe: wrong document pitfall:
	when an iframe comes from the same origin, and we may access its document, there is a pitfall.
	It is not related to cross-domain things, but important to know.
	 an iframe immediately has a document. But that document is different from the one that loads into it.
	We should not work with the document of a not-yet-loaded iframe, because that is the wrong document.
	. If we set any event handlers on it, they will be ignored.
	The right document is at the place when iframe.onload triggers. 
	But it only triggers when the whole iframe with all resources is loaded.
Collection: window.frames:
	The other way to get the  window object for<iframe> is to get it from the named collectionwindow.frames.
o	By numbers: window.frames[0] – the window object for the first frame in the document.
o	By name:  window.frames.iframeName – the window object for the frame withname="iframeName".
Example:
 
	An iframe may have other iframes inside. The corresponding window objects form a hierarchy.
	Navigation link:
o	window.frames – the collection of “children” windows (for nested frames).
o	window.parent – the reference to the “parent” (outer) window.
o	window.top – the reference to the topmost parent window.
Example:
 
The “SandBox” Iframe Attribute:
•	The sandbox attribute in iframes is used to apply restrictions to prevent the execution of untrusted code. By default, the sandbox attribute applies a set of restrictions to the iframe, treating it as if it comes from a different origin. However, these restrictions can be relaxed by providing a space-separated list of restrictions that should not be applied.
•	The following limitations can be applied using the sandbox attributeallow-same-origin: By default, the sandbox attribute enforces the "different origin" policy for the iframe, even if its src points to the same site. This option removes that feature and allows the iframe to be treated as if it comes from the same origin.
•	allow-top-navigation: This allows the iframe to change the parent's location. Without this restriction, the iframe is not allowed to navigate the parent's window.
•	allow-forms: This allows the submission of forms from the iframe. Without this restriction, the iframe is not allowed to submit forms.
•	allow-scripts: This allows the execution of scripts from the iframe. Without this restriction, the iframe is not allowed to run scripts.
•	allow-popups: This allows the iframe to open popups using the window.open method. Without this restriction, the iframe is not allowed to open popups.
•	When using the sandbox attribute, an empty value (sandbox="") applies the strictest limitations possible, while a space-delimited list of specific restrictions lifts those limitations.
•	It is important to note that the purpose of the sandbox attribute is to add restrictions and cannot remove them. Therefore, it cannot relax same-origin restrictions if the iframe comes from another origin.
•	For more information and examples, you can refer to the JavaScript.info example provided in the search results.
Cross-window messaging:

•	The postMessage interface allows windows from different origins to communicate with each other safely, bypassing the "Same Origin" policy. It consists of two parts: postMessage and onmessage.
•	postMessage: The sending window calls the postMessage method of the receiving window to send a message. It takes two arguments:
•	data: The data to be sent, which can be any object. Complex objects need to be stringified using JSON.stringify for compatibility with older browsers.
•	targetOrigin: Specifies the origin of the target window, ensuring that the message is only received by windows from that origin. This is a safety measure to prevent sending sensitive data to unintended recipients. If targetOrigin is set to "*", the check is bypassed.
•	onmessage: The receiving window must have an event handler for the message event to process incoming messages. The event object triggered by the message event has the following properties:
•	data: The data received from the postMessage call.
•	origin: The origin of the sending window.
•	source: A reference to the sending window, allowing for immediate responses using source.postMessage(...).
•	To assign the event handler, addEventListener should be used instead of window.onmessage.
•	Overall, the postMessage interface provides a secure way for windows from different origins to exchange information by agreeing on and calling corresponding JavaScript functions. The communication is synchronous and faster than setTimeout(...,0).
The clickjacking attack:
	Clickjacking attack allows an evil page to click on a “victim site” on behalf of the visitor.
	Clickjacking is a technique where attackers trick users into clicking on something they did not intend to. 
	They do this by overlaying a hidden button or link on top of a harmless-looking element on a website.
	 When the user tries to click on the harmless-looking element, they click on the hidden button or link, which can lead to unintended actions like liking a post or following someone on social media.
	The trick only works with mouse clicks or taps on mobile devices.
	 Redirecting keyboard input is more difficult because if the attacker hides a text field, the user will not see what they are typing, causing them to stop entering information.
	In simple terms, clickjacking is a way for bad actors to make you click on things you did not mean to, but it usually does not affect typing or entering information with the keyboard.
Old school defenses(weak):
•	Clickjacking is a technique used to trick users into clicking on something without their knowledge.
•	One defense against clickjacking is called "framebusting," which involves using JavaScript to prevent a webpage from being opened in a frame.
•	However, framebusting is not a foolproof defense, as there are ways to bypass it. 
•	Some methods to bypass framebusting include blocking top-navigation and using the sandbox attribute in iframes.
•	These techniques allow the attacker to manipulate the user's interaction with the webpage, potentially leading to clickjacking attacks.
X-frame-options:
	To defend against clickjacking attacks, one common approach is to use the X-Frame-Options header. This header can be set on the server-side and has three possible values: DENY, SAMEORIGIN, and ALLOW-FROM.
	DENY: This value ensures that the page is never displayed inside a frame.
	SAMEORIGIN: With this value, the page is allowed to be displayed inside a frame only if the parent document comes from the same origin.
	ALLOW-FROM: This value allows the page to be displayed inside a frame if the parent document is from the specified domain.
	It is important to note that the X-Frame-Options header must be sent as an HTTP header and cannot be set using the HTML <meta> tag.
	By using the X-Frame-Options header, websites can prevent their pages from being loaded in frames and mitigate clickjacking attacks. However, it is worth mentioning that the X-Frame-Options header has limitations and there are other techniques and headers that can be used in conjunction with it to provide stronger protection.
Samesite cookies attribute:
	These cookies  also prevent  clickjacking attacks.
	Cookies with this kind of attribute only sent to a website if it opened directly not via a frame.
	If the site, such as Facebook, had samesite attribute on its authentication cookie, like this: Set-Cookie: authorization=secret; samesite
	Such cookies wouldn’t be sent when face book is  open in, I frame  from another site, so the  attack would fail.
	Semasite  cookies would not have an effect if the  cookie e were not used, in that manner  other websites are allowed to show our public
ArrayBuffer and Binary Arrays:
Array Buffer:
•	is an array of bytes it represents a fixed-length binary buffer data. It is used to hold a raw binary data.
•	In simple terms the ArrayBuffer is a memory area it has no clue just a  raw sequence of bytes stored in  it.
•	Please note that  a buffer is not an array of  something.
This is how we create an array buffer:
 <!DOCTYPE html>
<script>
"Use strict";

let buffer = new ArrayBuffer(16); // create a buffer of length 16
alert(buffer.byteLength); // 16
</script>

The output will be : sixteen
•	In the  above  example  we are  just locating the contiguous memory area of 16 bytes
•	ArrayBuffer has nothing in  common with an array
•	The ArrayBuffer :
o	Has a  fixed length  do not increase or decrease.
o	Takes the  exactly much space in the memory.
o	To manipulate the  ArrayByffer  we use View object/,  does not use index.
•	The  view m object does not  store anything on its own
Example : 
o	Uint8Array- e ach byte is treated as a separate number,  with values from 8 to255, it is called 8-bytes unsigned integer
o	Uint16Array-  treats every 2 bytes as an integer,  with values from 0  to 65535. Is called 16-bit unsigned integer.
o	Uint32Array- every 4 bytes  as integer, with values from 04294967295, they are 32-bit unsigned integer
o	Float64Array- every 8 bytes as a  floating-point number with values from  5.0x10-324 to 1.8x10/308
	So, the binary data in an ArrayBuffer of 16 bytes can be represented as 16 tiny numbers, or 8 bigger numbers (with 2-bytes each) or 4 even bigger (with 4 bytes each)  or the 2 floating point values with high precesion(8 bytes each)

Example on the table below:

 

ArrayBuffer is the core object, the root of everything, the raw binary data.
Below is an example on how to use “view”:

<!DOCTYPE html>
<script>
  'Use strict';

  let buffer = new ArrayBuffer(16); // create a buffer of length 16

  let view = new Uint32Array(buffer); // treat buffer as a sequence of 32-bit integers

  alert(Uint32Array.BYTES_PER_ELEMENT); // 4 bytes per integer

  alert(view.length); // 4, it stores that many integers
  alert(view.byteLength); // 16, the size in bytes

  // let's write a value
  view[0] = 123456;

  // iterate over values
  for (let num of view) {
    alert(num); // 123456, then 0, 0, 0 (4 values total)
  }
</script>

TypedArray:

	They behave like regular arrays they have indexes and are alterable.
	They provide a  way to handle binary data as  efficiently as arrays work in C.
	Are raw memory, they can be passed directly into any function without converting the data.
	They are faster than normal arrays.

There are 5 variants of arguments;
 
	. If an ArrayBuffer argument is supplied, the view is created over it. We used that syntax already.
	We can also provide byteOffset to  start  from(0 by default) and the  length( till the end of buffer by default) then the view will cover only a part of the buffer.
	 If an Array, or any array-like object is given, it creates a typed array of the same length and copies the content.
	We can use this to pre- fill the  array  with data:
<!DOCTYPE html>
<script>
"Use strict";

let arr = new Uint8Array([0, 1, 2, 3]);
alert( arr.length ); // 4, created binary array of the same length
alert( arr[1] ); // 1, filled with 4 bytes (unsigned 8-bit integers) with given values
</script>
	If another TypedArray is supplied, it does the same: creates a typed array of the same length and copies values. Values are converted to the new type in the process, if needed.
<!DOCTYPE html>
<script>
"Use strict";

let arr16 = new Uint16Array([1, 1000]);
let arr8 = new Uint8Array(arr16);
alert( arr8[0] ); // 1
alert( arr8[1] ); // 232, tried to copy 1000, but can't fit 1000 into 8 bits (explanations below)
</script>
	For a numeric argument length – creates the typed array to contain that many elements. Its byte length will be length multiplied by the number of bytes in a single item TypedArray.BYTES_PER_ELEMENT:
<!DOCTYPE html>
<script>
"Use strict";

let arr = new Uint16Array(4); // create typed array for 4 integers
alert( Uint16Array.BYTES_PER_ELEMENT ); // 2 bytes per integer
alert( arr.byteLength ); // 8 (size in bytes)
</script>
	We can create typedArray without mentioning ArrayBuffer.
	But the view can not exist  without  an underlying ArrayBuffer,  so it gets created  automatically.
	There are properties needed to access the ArrayBuffer:
o	Arr.Buffer-references the ArrayBuffer.
o	Arr.byteLength- the length of the ArrayBuffer.
	We can always move from one  view to another:
 
Below is the list of TypedArrays:
•	Uint8Array, Uint16Array, Uint32Array – for integer numbers of 8, 16 and 32 bits.
o	Uint8ClampedArray – for 8-bit integers, “clamps” them on assignment (see below).
•	Int8Array, Int16Array, Int32Array – for signed integer numbers (can be negative).
•	Float32Array, Float64Array – for signed floating-point numbers of 32 and 64 bits.
Out-Of-Bounds behaviour:
	it happens when a program or code attempts to access a memory location or an element in a data structure outside of the valid or allocated range.
	  For instance, let’s try to put 256 into Uint8Array
	In binary form, 256 is 100000000 (9 bits), but Uint8Array only provides 8 bits per value, which makes the available range from 0 to 255.
	For bigger numbers, only the rightmost (less significant) 8 bits are stored, and the rest is cut off:
 
	We get zero
	For 257, the binary form is 100000001 (9 bits), the rightmost 8 get stored, so we will have 1 in the array:
 
In other case the number 2^8 is saved
Here is the demo example:
<!DOCTYPE html>
<script>
"Use strict";

let uint8array = new Uint8Array(16);

let num = 256;
alert(num.toString(2)); // 100000000 (binary representation)

uint8array[0] = 256;
uint8array[1] = 257;

alert(uint8array[0]); // 0
alert(uint8array[1]); // 1
</script>
	Uint8ClampedArray is special in this aspect, its behavior is different. It saves 255 for any number that is greater than 255, and 0 for any negative number. That behavior is useful for image processing.
TypedArray method:
	TypedArray has regular Array methods, with notable exceptions.
	We can iterate, map, slieslice, find, reduce etc.
There are things we can’t do through:
	No splice: we can’t “delete” a value because typed arrays are views on buffer and are fixed contiguous area of memory.  Can just assign to zero
	No concat method.
There are two additional methods:
	arr.set(fromArr, [offset]) copies all elements from fromArr to the arr, starting at position offset (0 by default).
	arr.subarray([begin, end]) creates a new view of the same type from begin to end (exclusive). 
	 That’s similar to slice method (that’s also supported) but doesn’t copy anything – just creates a new view, to operate on the given piece of data.
	Allow  us to copy typed  arrays, mix them, create new arrays from existing ones  and so on.
DataView:
	Is a special super=flexible “untyped” view over ArrayBuffer.
	It allows accessing the data on any offset in any format
o	For typed arrays, the constructor dictates what the format is. The whole array is supposed to be uniform. The i-th number is arr[i].
o	With DataView we access the data with methods like .getUint8(i) or .getUint16(i). We choose the format at method call time instead of the construction time.
	Syntax:
 
	buffer – the underlying ArrayBuffer. Unlike typed arrays, DataView doesn’t create a buffer on its own. We need to have it ready.
	byteOffset – the starting byte position of the view (by default 0).
	byteLength – the byte length of the view (by default till the end of buffer).
<!DOCTYPE html>
<script>
"Use strict";

// binary array of 4 bytes, all have the maximal value 255
let buffer = new Uint8Array([255, 255, 255, 255]).buffer;

let dataView = new DataView(buffer);

// get 8-bit number at offset 0
alert( dataView.getUint8(0) ); // 255

// now get 16-bit number at offset 0, it consists of 2 bytes, together interpreted as 65535
alert( dataView.getUint16(0) ); // 65535 (biggest 16-bit unsigned int)

// get 32-bit number at offset 0
alert( dataView.getUint32(0) ); // 4294967295 (biggest 32-bit unsigned int)

dataView.setUint32(0, 0); // set 4-byte number to zero, thus setting all bytes to 0
</script>
	DataView is great when we store mixed-format data in the same buffer. E.g we store a sequence of pairs (16-bit integer, 32-bit float). Then DataView allows to access them easily.
















