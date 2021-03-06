# NodeJS Promise

### A Brief Into

Due to the nature of the internet, it is likely that when you make a request to some external resource out in the world, it is not definitive when the request you send will be responded to, if you get a response at all. Because of this non-deterministic nature, we need the ability for modern programs to make these requests asynchronously which enables other operations to occur while we await a response. This behavior is formally handled though a promise. 

Now that we generally know what a promise is and why we want it, let’s begin to look into some of the details starting with what sort of guarantees using a promise comes with. One of the most common things to see associated with a promise is a `.then()` callback. These callbacks come with the guarantee that they will not be invoked until after the original event has run its course, which allows for failure or success. This again allows you as the developer to write code out of the box that handles the cases failure and success cases alike in an elegant way. Another awesome feature of the `.then()` callback is it allows for chaining.

### Chaining Callbacks

The chaining of callbacks gives us a nice interface to handle more complicated cases like you will see below: 

```node
callSomeAPI("GET", "/")
    .then((response) => {
        return something;
    })
    .then((test) => {
        return test;
    })
```
An important thing to note is that each `.then()` needs to return something if you want it to be available in the subsequent callback.

If you want to handle errors generally, NodeJS provides a `.catch()`
Call back. This is a nice practice to follow but may lead to issues if you forget it is in place and have questions about why something is not working as you would expect. 

### Promise States

Given the nature of a promise, there are three possible states that it can be in: pending, fulfilled, or rejected. These are pretty straightforward so there’s no need to dive into the details but here is a quick diagram that highlights much of the detail. 

![Source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise](https://user-images.githubusercontent.com/35577566/116013793-cf112300-a5e6-11eb-934e-aca42f6c40f5.png) 

* Source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise


### Wrapping Up a Promise

Much like a try/catch block in many languages, promises allow for a `.finally()` callback which enables us to run some code at the very end of the promise exchange, regardless of the ending state of that promise.


### Life Without Promises 

You may be thinking as we have gone through these examples, "this all seems very straightforward and such, but why do we need promises to start?" The two main reasons are that it enables us to group our asynchronous code together nicely and also that it allows us to avoid deeply nested code. Without promises, your code would end up looking like:

```node
function bad_exmaple() {
	do_something () {
        	do_something_else () {
            		etc () {
                		etc.
            		}
        	}
    	}
}

```
but with even more complexity. This problem has been generally referred to as: https://en.wikipedia.org/wiki/Pyramid_of_doom_(programming) and is something that if it can be avoided, should be avoided.

### Learn More About Promises

The definitive place for learning about promises and finding more example of them is: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises
Here you will learn more about the technical details of a Promise, find links to examples, and understand where Promises are used in the context of web applications.
