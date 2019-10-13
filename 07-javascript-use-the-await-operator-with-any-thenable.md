[Video Link](https://egghead.io/lessons/javascript-use-the-await-operator-with-any-thenable)

# 07. Use the await Operator with Any Thenable

**The await operator can be used on more than just promises. It can be used on any thenable**

If if you try to await a non-promise value. The ```<await>``` operstor will change a non-promise into a resloved promise. As if we wrote ```<Promise.resolve(42)>```.

Since await internally creates promises, it can be used with other promise implementations as well.

In the video Marius imports the promise library Bluebird.

```javascript
const Bluebird = require("bluebird");

async function main() {
    console.log("Working ...")
    await Bluebird.delay(2000);
    console.log("Done");
```
Bluebird.delay returns a thenable and since we used the ```<await>``` operator it converts it to a resolved promise.

In our video example the await expression pauses our async main function for 2 seconds then resumes it.
