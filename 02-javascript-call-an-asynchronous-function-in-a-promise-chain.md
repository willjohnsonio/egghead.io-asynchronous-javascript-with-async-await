[Video Link](https://egghead.io/lessons/javascript-call-an-asynchronous-function-in-a-promise-chain)

# 02. Call an Asynchronous Function in a Promise Chain

In this video let's refactor the program so the function only retrieves the user and then returns it the caller, who can decide what to do with it

First, replace the ```<console.log>``` statements with ```<return user;>```.

```javascript
async function showGitHubUser(handle){
const url = `https://api.github.com/users/${handle}`;
const response = await fetch(url);
const user = await response.json();
return user;
}
```

**When an aync function is called it returns a promise**

When an aync function returns a value the promise will be resolved with that value.

For us the promise will be resolved with the user with just recived from the GitHub API.

Hovering over the function call in VS Code. It shows that the async funtion does return a promise.

We can build a promise chain using the ```<.then>``` method and use the result to log the name and location inside of the ```<.then>```.

```javascript
showGetHubUser("mariusshulz")
    .then(user => {
        console.log(user.name);
        console.log(user.location);
    })
```



In the video there is a function that reaches out to the GitHub to get a specific user using the ```<fetch>``` keyword. When the information comes back it parses the body as JSON.

Then the function logs the users name and location to the console.

```javascript
function showGitHubUser(handle) {
    const url = `https://api.github.com/users/${handle}`;
    fetch(url)
        .then(response => response.json())
        .then(user => {
            console.log(user.name);
            console.log(user.location);
        });
}
```
Let's convert our regualr function into an asynchronous function with the ```<async>``` and ```<await>``` keywords

**To make this function asynchronous add the async keyword before the function keyword**

Next we'll use the await operator to pause and wait until the ```<fetch>``` call is done.

```javascript
async function showGitHubUser(handle){
const url = `https://api.github.com/users/${handle}`;
await fetch(url);
}
```
**The await operator takes a promise then pauses the function until the promise is settled**

If the promise is rejected, the ```<await>``` operator will throw a rejected value. If the promise is resloved, the ```<await>``` operator will take the promise and we can store in a variable.

```javascript
const response = await fetch(url);
```

Then we want to convert the ```<response>``` to JSON. The ```<.json>``` method returns a promise as well. So we'll use the ```<await>``` operator again to wait to wait until the promise is settled.

```javascript
const user = await response.json();
```
Our function looks like it runs on order from top to bottom. No more promise chains. This makes it a lot easier to understand.

```javascript
async function showGitHubUser(handle){
const url = `https://api.github.com/users/${handle}`;
const response = await fetch(url);
const user = await response.json();
console.log(user.name);
console.log(user.location);
}
```



# Resources
[.then MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then)




