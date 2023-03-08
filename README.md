# Technical Documentation for Customizing React Folder Structure
<ul><li>React is JS library for building user interface</li>
<li>Single Page Application</li></ul>


# Creating React Application
To create react application, use <code>npx create-react-app</code> command in the command prompt. 
<pre><code>npx create-react-app appName 
cd appName
npm start</code></pre>
After <code>npm start</code> command, the application loads at <b><i>localhost:3000</i></b>.


# Customize
To customize react application to our likings, we use <code>npm run eject</code> command and install <i>@babel/preset-react</i> and <i>@babel/preset-env</i> package as <i>dev</i> dependency.
<pre><code>npx create-react-app appName 
cd appName
npm run eject
npm i -D @babel/preset-react @babel/preset-env</pre></code>

 
I would like to add <b>css, js</b> and <b>data</b> folders in <i><b>public</b></i> folder and keep all the files relating to them in those folders.

I would also like to create a new folder called <b>views</b> and move my <b><i>index.html</i></b> file here.
  
<br/>
Now follow the below steps to implement the necessary changes:
<br/>
Go to:
<pre>config -> paths.js -> module.exports -> appHtml</pre>

Change <i>appHtml</i> value from,
 
<code>resolveApp('public/index.html')</code> to <code>resolveApp('views/index.html')</code>
<br/>
<b>In package.json:</b>

<i>Under babel</i>:

Change,
<pre>
"presets": [
      "react-app"
    ]</pre>
to 
<pre>
"presets": [
      "@babel/preset-env",
     ["@babel/preset-react", {"runtime": "automatic"}]
  ]
</pre>
<br/>
<b>In webpack.config.js:</b>

<ol><li> <pre>ctrl+F -> appSrc -> go to 4th of 5th selection </pre> ie.
Just below <i>// Process application JS with Babel.
 // The preset includes JSX, Flow, TypeScript, and some ESnext features.</i> comment, 
 
Change,

<code>include: path.appSrc</code>
to
<code>include: [paths.appSrc, paths.appPublic]</code></li>

<li> <pre>ctrl+F -> ModuleScopePlugin -> comment the field</pre>
</li></ol>

