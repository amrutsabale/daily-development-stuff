
# How can you sort an array without mutating the original array?
## ES2023 Array Method toSorted():
The toSorted() method of Array instances is the copying version of the sort() method. It returns a new array with the elements sorted in ascending order.
toSorted() method is supported nearly by all browsers and on Node.js version 20+.

## Handle on old node versions:

````
function sortCopy(arr) { 
  return arr.slice(0).sort((a,b)=>a-b);
}
````

````
function sortCopy(arr) { 
  return [...arr].sort((a,b)=>a-b);
}
````

