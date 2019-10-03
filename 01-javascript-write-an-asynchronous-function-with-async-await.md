[Video Link](https://egghead.io/lessons/javascript-write-an-asynchronous-function-with-async-await)

# 01. Write an Asynchronous Function with async/await

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
Let's convert our regualar function into an asynchronous function with the ```<async>``` and ```<await>``` keywords

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
Our function looks like it runs in order from top to bottom. No more promise chains. This makes it a lot easier to understand.

```javascript
async function showGitHubUser(handle){
const url = `https://api.github.com/users/${handle}`;
const response = await fetch(url);
const user = await response.json();
console.log(user.name);
console.log(user.location);
}




# Resources
[async keyword MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)

[await keyword MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)


