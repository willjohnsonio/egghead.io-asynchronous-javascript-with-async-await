[Video Link](https://egghead.io/lessons/javascript-iterate-asynchronously-with-the-for-await-of-loop)

# 08. Iterate Asynchronously with the for-await-of Loop

We're introduced to a generator function that will display 1,2, and 3 (because of the ```<yield>``` keyword which defines the return value from the generator function).

We'll run a for..of loop to loop over each valued yielded by the generator. We'll console.log each value.

Now let's make this asynchronus by add the async keyword to the ```<someGenerator>``` function. Then inside of the function we add some fake await delays to act as long running operations.

```javascript
async function* someGenerator() {
    await delay(1000);
    yield 1;
    await delay(1000);
    yield 2:
    await delay(1000);
    yield 3;
}
```

We'll create a delay function it will return a promise after resolved after a number milliseconds that we pass to ```<setTimeout>``` in our case 1000.

```javascript
const delay = (ms) => new Prmoise(resolve => {
    setTimeout(resolve, ms);
})
```
Next we'll make the main function asynchronous by adding the async keyword,and add await before the () of the for loop to create the for await...of loop.

Then Marius add a polyfill for the asyncIterator. He also transplies the JavaScript file because his current node version doesn't supper async iteration.

```<someGenerator>``` returns three promises. Our await of loop gets the first promise, wait until ti is resolved then resumes ```<someGenerator>``` and it continues until all promises are resloved.

Marius closes the course by showing a rough process of how the main function that we have been running works. 

## Resources

[iterators and generators MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators)

[for...of loop MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)

[for await...of loop MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for-await...of)