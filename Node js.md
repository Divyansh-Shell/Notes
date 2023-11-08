---
tags: 
aliases:
  - Notes
  - Js
  - Ts
  - Node Js
---

#Architecture 

Single Threaded Event Loop

1. Asynchronous Model 
2. Non-Blocking of I/O operations 
3. Components of Node js Architecture 
	1. Requests: Request can be either Blocking or Non Blocking
	2. Node js Server: Requests -> Process -> returns Results 
	3. Event Queue: Store the incoming client Requests and pass them sequentially to event loop
	4. Thread Pool: contans the threads used for performing operations required to process requests 
	6. Event Loop: receives request from the event queue and sends out the response to the clients 
	7. External Resources : 




![[Pasted image 20231031121145.png]]

Requests goes to the event queue 
event queue feeds the request to the event loop sequentially. event loop checks the nature of the request 
if its blocking request it is assigned to the single thread process to complete the task by using the external resources 
if the operation is completed it is sent to the event loop which delivers the response back to the client


Node js Timer 
	 setImmediate()
	 setInterval()
	 setTimeout()
	clearImmediate()
	clearInterval()
	clearTimeout()
		
		console.warm()--> warning message 
		console.error(new Error()) -> Error Message 
	
		
	


```
document.getElementById("Demo").style.display = "block"
Showing the hidden elements changing the display style 

document.getElementById("demo").style.display = "none"


Script tag 

<script>
	document.getElementById("demo").innerHTML = "My First Js";
</script
```

```
document.getElementById("Demo").style.display = "block"
Showing the hidden elements changing the display style 

document.getElementById("demo").style.display = "none"


Script tag 

<script>
	document.getElementById("demo").innerHTML = "My First Js";
</script
```

## Ways of Displaying 

InnerhtmL
```
<!DOCTYPE html>  
<html>  
<body>  
  
<h1>My First Web Page</h1>  
<p>My First Paragraph</p>  
  
<p id="demo"></p>  
  
<script>  
document.getElementById("demo").innerHTML = 5 + 6;  
</script>  
  
</body>  
</html>
```

window.alert()

```
<!DOCTYPE html>  
<html>  
<body>  
  
<h1>My First Web Page</h1>  
<p>My First Paragraph</p>  
  
<p id="demo"></p>  
  
<script>  
document.getElementById("demo").innerHTML = 5 + 6;  
</script>  
  
</body>  
</html>


<!DOCTYPE html>  
<html>  
<body>  
  
<h1>My First Web Page</h1>  
<p>My first paragraph.</p>  
  
<script>  
alert(5 + 6);  
</script>  
  
</body>  
</html>
```


Print 

```
<!DOCTYPE html>  
<html>  
<body>  
  
<button onclick="window.print()">Print this page</button>  
  
</body>  
</html>

```







#let_Keyword 

```
Let kyword cannot be redeclared 
Must be Declared before use 
Let have block scope 
```

Block Scope 
declared inside the scope cannot be used from outside the block 

Let Hoisting 

variables defined with var 


