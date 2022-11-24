# Webpack & Typescript image import configs
# Setup Webpack file-loader, add declaration.d.ts, and voila!
after spending some time to figure out the solution, this is what I did...
 
## Step 1
ensure that you have installed file-loader as a dev dependency by

```npm install -D file-loader, if you use yarn yarn add -D file-loader```

## Step 2
add the loader corresponding to the file extension in the Webpack rules webpack.config.js, like this
```
module: {
    rules: [
      ...,
      {
        test: /\.(png|jpe?g|gif|jp2|webp)$/,
        loader: 'file-loader',
        options: {
          name: '[name].[ext]',
        },
      },
    ],
  },
```
## Step 3
create an index.d.ts file next to your tsconfig.json file, actually you can name it whatever you want but you have to follow step 4.

Since Webpack now is going to handle several image extensions so you can add other image formats supported by file-loader
````
declare module '*.png';
declare module '*.jpg';
````
## Step 4
go to your tsconfig.json file and add index.d.ts to the include array like this:
````
{
  "compilerOptions": {
    ...,
    "jsx": "react",
    "esModuleInterop": true,
    "target": "ES2020",
    "moduleResolution": "node"
  },
  "exclude": ["node_modules", "**/*.spec.ts", "**/*.test.ts"],
  "include": ["src", "index.d.ts"] /// <-- Like this!!
}
````
be aware that if you haven't defined an include array, typescript by default is going to add all the files on the root folder, if you just define one file and not the file that contains all your code it is not going to compile. I think is a good practice to have all your code within the src folder.

Voila!!
