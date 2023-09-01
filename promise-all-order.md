Promise.all aggregates all resolved values with an array corresponding to the input order of the original Promises.

However, I would like to point out, that the order is only preserved on the client side!

To the developer, it looks like the Promises were fulfilled in order but in reality, the Promises are processed at different speeds. 
This is important to know when you work with a remote backend because the backend might receive your Promises in a different order.

Here is an example that demonstrates the issue by using timeouts:

Promise.all
````
const myPromises = [
  new Promise((resolve) => setTimeout(() => {resolve('A (slow)'); console.log('A (slow)')}, 1000)),
  new Promise((resolve) => setTimeout(() => {resolve('B (slower)'); console.log('B (slower)')}, 2000)),
  new Promise((resolve) => setTimeout(() => {resolve('C (fast)'); console.log('C (fast)')}, 10))
];

Promise.all(myPromises).then(console.log)
````
Expand snippet
In the code shown above, three Promises (A, B, C) are given to Promise.all. The three Promises execute at different speeds (C being the fastest and B being the slowest). That's why the console.log statements of the Promises show up in this order:
````
C (fast) 
A (slow)
B (slower)
````
If the Promises are AJAX calls, then a remote backend will receive these values in this order. But on the client side Promise.all ensures that the results are ordered according to the original positions of the myPromises array. That's why the final result is:
````
['A (slow)', 'B (slower)', 'C (fast)']
````
