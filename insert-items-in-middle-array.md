````
splice(start)
splice(start, deleteCount)
splice(start, deleteCount, item1)
splice(start, deleteCount, item1, item2, itemN)
````

Example. insert a array on 2nd last of b array

````
let b =[44];
let a=[2,3,4];
b.splice(b.length-1,0,...a);
````

Output
````
b= [2,3,4,44];
````
