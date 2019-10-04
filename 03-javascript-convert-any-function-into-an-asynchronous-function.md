[Video Link](https://egghead.io/lessons/javascript-convert-any-function-into-an-asynchronous-function)

# 03. Convert Any Function into an Asynchronous Function

**JavaScript allows you to change any function to an async function**

In the lesson we used a function declaration now lets change it to a function expression

Cut  the function name then create a variable with the ```<const>``` keyword, then paste the function name we just cut.

```javascript
const fetchGitHubUser = async function(handle) {
    const url = `https://api.github.com/users/${handle}`;
    const response = await fetch(url);
    return await response.json();
}
```
Now we have changed it to an async function expression. 

We can also use the async keyword with arrow functions as well, by remove the ```<function>``` keyword and add a 'fat arrow' before the function block.

```javascript
const fetchGitHubUser = async (handle) => {
    const url = `https://api.github.com/users/${handle}`;
    const response = await faetch(url);
    return await response.json();
}
```
**The async keyword works with all function types**

Marius like to use function declarations to take advantage of function hoisting.

Here is a good use use case for an async function expression. 

**The await keyword can only be used inside of async fucntions** 

We can't use it at the top level, that would be invalid syntax.

```javascript
const user = await fetchGitHubUser("mariusschulz");
    console.log(user.name);
    console.log(user.location);
```
It needs an async function wrapper around these lines. This will put the await function inside of an async function. We'll use a IIFE(Immediatly Invoked Function Expression) for this.

```javascript
(async function() ) {
const user = await fetchGitHubUser("mariusschulz");
    console.log(user.name);
    console.log(user.location);
})();
```
Let's use an async class method.Let's create a class called ```<GitHubApiClient>```, then create a method called ```<fetchUser>```. In the method put the code from our async function.

Now all we have to do is put the async keyword before the method to make it asynchoronous.

```javascript
class GitHubApiClient {
    async fetchUser(handle) {
      const url = `https://api.github.com/users/${handle}`;
      const response = await fetch(url);
      return await response.json();
    }
}
```
The same syntax can be used for object literals

Now we can create a new instance of the class, and assign it to the client variable and using client.fetchUser we'll call the method(function) to fetch the data.

```javascript
(async function() ) {
    const client = new GitHubApiClient();
    const user = await client.fetchUser("mariusschulz");
    console.log(user.name);
    console.log(user.location);
})();
```

# Resources
[IIFE MDN](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)




