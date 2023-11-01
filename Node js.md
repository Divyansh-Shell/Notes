

console.warm()--> warning message 
console.error(new Error()) -> Error Message 

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
	 
	
