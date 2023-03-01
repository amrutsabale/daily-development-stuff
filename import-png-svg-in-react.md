If you use webpack, you can do this by creating a custom types file.

Create a file named custom.d.ts with the following content:
````
declare module '*.png';
declare module '*.svg';
````

Add the custom.d.ts to tsconfig.json as below

````
 "include": ["custom.d.ts"],
````

Now you can import images like this and use with img tag
````
import SampleIcon from './weather-icons/sample.svg';
<img src={SampleIcon}/>
````
