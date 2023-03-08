# Technical-Documentation
•	React is JS library for building user interface.
•	Single Page Application


CREATING REACT APPLICATION
To create react application in node-js, use create-react-app command. 
npx create-react-app appName 
<pre><code>cd appName
npm start</code></pre>
After npm start command, the application gets starts at localhost:3000.


CUSTOMIZING
To customize react application to our likings, we use eject command and install @babel/preset-react package as dev dependency.
npx create-react-app appName 
cd appName
npm run eject
npm i -D @babel/preset-react @babel/preset-env

 
Add css, js, data folder in public folder and keep all the files relating to it in those folders.

Create a new folder called views and move index.html file from public folder to this newly created folder.
  
Now follow the below steps to customize the react application:

	config -> paths.js -> module.exports -> appHtml
Change appHtml value from,
 
resolveApp('public/index.html') 
to 
resolveApp('views/index.html')

	In package.json:

under babel :
Change,
"presets": [
      "react-app"
    ]
to
"presets": [
      "@babel/preset-env",
     ["@babel/preset-react", {"runtime": "automatic"}]
  ]

	In webpack.config.js:

1. ctrl+F -> appSrc -> go to 4th of 5th selection ie.
Just below "// Process application JS with Babel.
 // The preset includes JSX, Flow, TypeScript, and some ESnext features." comment, change,

include: path.appSrc
to
include: [paths.appSrc, paths.appPublic]

2. ctrl+F -> ModuleScopePlugin -> comment the field


