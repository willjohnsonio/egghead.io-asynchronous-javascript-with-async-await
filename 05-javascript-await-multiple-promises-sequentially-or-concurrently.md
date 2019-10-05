[Video Link](https://egghead.io/lessons/javascript-await-multiple-promises-sequentially-or-concurrently)

# 05. Await Multiple Promises Sequentially or Concurrently

**The await keyword can used to get promises one after another or at the same time**

In the video we'll make two request to the GitHub API. We'll load a user's profile and a list of their respositories. The easy way to this would be to make two HTTP request one after the other.

When both responses return we can log the users name and the amount of repositories to the console.

```javascript
async function showUserAndRepos(handle) {
    const user = await fetchFromGitHub(`/users/${handles}`);
    const repos = await fetchFromGitHub(`/users/${handle}/repos`);
}
```
The problem with the program right now is that each request is happening one at a time instead of both running at the same time. The first request has to finish before the next one can begin. This can cause performance issues. If each requests takes half a second then waiting on one to finish would use up 1 second.

**Like boiling eggs for breakfast you wouldn't cook one at a time, you boil them all at the same time**

Let's remove the ```<await>``` operator and rename the variable by adding Promise to the end of the variable name. Now were the storing the promise in the variables, instead of the results.

```javascript
async function showUserAndRepos(handle) {
    const userPromise = fetchFromGitHub(`/users/${handles}`);
    const reposPromise = fetchFromGitHub(`/users/${handle}/repos`);
}
```
We can add ```<const user>``` and ```<const repos>``` and assign them to ```<await>``` userPromise and reposPromise 

```javascript
const user = await userPromise;
const repos = await reposPromise;
```

Now both request are going out at the same time and we are waiting for them both to return. The slower of the two determines how long the entire process takes, and we lose the performance loss of waiting for them one at a time.



# Resources
[try...catch MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch)




