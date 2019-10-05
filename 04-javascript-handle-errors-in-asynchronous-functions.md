[Video Link](https://egghead.io/lessons/javascript-handle-errors-in-asynchronous-functions)

# 04. Handle Errors in Asynchronous Functions

The ```<fetchGitHubUser>`` function get the GitHub API and loads the user we request.

What if the user we want to load doesn't exist? 

If we console.log the response object we assigned to user we get a object with two properties message and documentaton. 

```javascript
fetchGitHubUser('idontexist') {
    .then(user => {
        console.log(user);
    })
}
```
**Our fetchGitHubUser function always returns a promise**

We want to reject this promise with the error message 

Let's store the return value of the JSON function in a variable we'll call body

```javascript
const body = await response.json();
```
The lets place and if/else statement inside of our ```<fetchGitHubUser>`` function. If status code isn't 200 we'll throw an Error(). We want to pass the message property that we get from body.

```javascript
if (response.status !== 200)
    throw Error(body.message);

    return body
```
Now add a ```<.catch()>``` method to our promise chain when we call the ```<fetchGitHubUser>``` function and log err.message to the console.

```javascript
fetchGitHubUser('idonotexist')
    .then(user => {
        console.log(user);
    })
    .catch(err => {
        console.log(`Error: ${err.message}`);
    });
```

**An async function will always return a rejected promise when we have an error**

This also why we can write a ```<.catch>``` method to handle the rejected promise.

**With async & await we can use try and catch statements**

We can't do this with plain promises because the call back funtion is ran asynchronously 

Let's change our promise chain into an async function. Inside of the function we'll put a try...catch statement.

```javascript
async function showGitHubUser(handle) {
    try {

    } catch (err) {

    }
}
```

We'll try to load the user and store in a variable called user. If getting the user succeeds we will console.log the name and the location.

```javascript
async function showGitHubUser(handle) {
    try {
        const user = await fetchGitHubUser(handle);
        console.log(user.name);
        console.log(user.location);
    } catch (err) {

    }
}
```
The ```<await>``` operator will wait until the promise is settled, if recjected it will throw an error. If something goes wrong we will run the code inside of the catch block. We'll just console.log the error message.

# Resources
[try...catch MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch)




