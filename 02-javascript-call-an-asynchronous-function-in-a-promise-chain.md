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

All we are doing with the user is returning it, we can shorten this variable and simply say, ```<Return await response.JSON.>```

```javascript
async function showGitHubUser(handle) {
    const url = `https://api.github.com/users/${handle}`;
    const response = await fetch(url);
    return await response.json();
}

showGitHubUser("mariusschulz")
    .then(user => {
        console.log(user.name);
        console.log(user.location);
    });
```




# Resources
[.then MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then)




