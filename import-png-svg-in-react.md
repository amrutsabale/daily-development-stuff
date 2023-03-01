If you use webpack, you can do this by creating a custom types file.

Create a file named custom.d.ts with the following content:
````
declare module '*.png';
````

Add the custom.d.ts to tsconfig.json as below

````
 "include": ["custom.d.ts"],
````

Now you can import images like this and use with img tag
````
import SampleIcon from './weather-icons/sample.png';
<img src={SampleIcon}/>
````

note: this wont work with svg icons. you can do 2 things -
  1. Create React component with svg ad use it
  2. host svg icon on remote cloud and use image urls in img tag
