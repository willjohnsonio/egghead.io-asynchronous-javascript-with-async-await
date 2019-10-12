[Video Link](https://egghead.io/lessons/javascript-await-multiple-promises-concurrently-with-promise-all)

# 06. Await Multiple Promises Concurrently with Promise.all()

This video shows us how to await more than one async operations using Promise.all().

**Promise.all accepts a collection of promises and retuns one promise**

In the video examples we'll  make two GitHub API calls. One for the name and one for the repos.

We'll pass those two requests as an array into ```<Promise.all()>```. We'll put the results in a varible called ```<results>```.We will use ```<await>``` on ```<Promise.all()>```.

**The order of the index number is the same as the order of the promises in the array**

So user is index 0 and repos is index 1.

Let's refactor and destructure the array we passed in Promise.all(). 

```javascript
async function showUserAndRepos(handle) {
    const[user, repos] = await Promise.all([
        fetchFromGitHub(`/users/${handle}`),
        fetchFromGitHub(`/users/${handle}/repos`)
    ]);
}
```
**Remember the order of the Promises we pass into Promise.all() controls the order of resulting values in the array**

Promise.all() works in any iterables

**If any of the passed-in promises is rejected, the return promise is instantly rejected.** 

Promise.all won't for every passed in promise to be resolved.

# Resources
[Promise.all](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)




