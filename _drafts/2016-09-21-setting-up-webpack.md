---
---
# Setting up Webpack

Here's what I did starting out.

Create a directory (I called mine `redux-learn`).  `cd` into the new directory and run

    npm init

Hit enter to accept the defaults and save the file.  You can always change it later.  This will create a `package.json` file for you.  It's important to have this in place before installing everything so that the `--save-dev` will add things to it for you.  Otherwise you'll have to search the web for how to manually populate it, or reinstall everything with npm after creating the file (which is what I did).

    npm install babel-core babel-loader babel-cli jshint jshint-loader node-libs-browser babel-preset-es2015 babel-preset-stage-2 webpack redux-devtools --save-dev

    npm install --save redux

    npm install -g webpack-dev-server

I also created a webpack.config.js in the directory that looks like this:

    module.exports = {
    entry: ['./global.js', './app.js'],
    output: {
    filename: 'bundle.js'
    },
    module: {
    loaders: [
     {
       test: /\.(es6|js)$/,
       exclude: /node_modules/,
       loader: 'babel-loader',
       query: {
         presets: ['es2015', 'stage-2']
       }
     }
    ]
    },
    resolve: {
    extensions: ['', '.js', '.es6']
    },
    watch: true
    }

This is admittedly a bit more than I need just to test out and make sure webpack and babel are running, but I'll need more of it going forward.  A lot of the initial setup is from [this tutorial](https://medium.com/@dabit3/beginner-s-guide-to-webpack-b1f1a3638460#.9g3uyx146).

After fiddling around with the webpack config a bit and trying to get the webpack dev server running I found I'd accidentally hit Ctrl-Z rather than Ctrl-C and lost the process.  Happily, this mistake led me to research how to find and kill the process if need be:

    ps aux | grep node

    kill -9 PID

via [this SO answer](http://stackoverflow.com/a/4247759)
