### lawebpackba
####
#####Setting up babel-loader
review syntax
```
module.exports = {
  entry: './src/main.js,
  output:{
    path:'build',
    filename:'bundle.js'
  },
  module:{
    loaders:[
      {
        test:/\.js$/,
        exclude:/(node_modules)/,
        loader:'babel'
      }
    ]
  }
}
```
#####Using presets
```
module.exports = {
  entry: './src/main.js,
  output:{
    path:'build',
    filename:'bundle.js'
  },
  module:{
    loaders:[
      {
        test:/\.js$/,
        exclude:/(node_modules)/,
        loader:'babel',
        query:{
          presets:['es2015']
        }
      }
    ]
  }
}
```
.babelrc
```
{
  'presets':[
    'es2015'
  ]
}

```
install
```
babel-core babel-loader babel-preset-es2015
```
#####coffee
```
npm install coffee-loader
```
####3 webpack and CSS
#####Basic
```
module.exports = {
  entry: './src/main.js,
  output:{
    path:'build',
    filename:'bundle.js'
  },
  module:{
    loaders:[
      {
        test:/\.js$/,
        exclude:/(node_modules)/,
        loader:'babel',
        query:{
          presets:['es2015']
        }
      },
      {
        test:/\.css$/,
        loader:'style-loader!css-loader'
      }
    ]
  }
}
```
#####Transpiling Sass with webpack
```
npm install sass-loader node-sass --save-dev
```
small change
```
{
  test:/\.scss$/,
  loader:'style-loader!css-loader!sass-loader'
}
```
#####Loading images with webpack
```
npm install url-loader file-loader --save-dev
```
add loader
```
{
  test:/\.(png|jpg)$/,
  loader:'url-loader?limit=20000'  //if bigger than 20k ,create url asset
}
```
####4 Code splitting
#####Adding multiple entry points
create bundle respectively
```
var webpack = require('webpack');
var path = require('path');
module.exports = {
  entry:{ 
    a:'./dist/a',
    b:'./dist/b'
  },
  output:{
    path:path.join(__dirname,'build'),
    filename:'[name].bundle.js'
  },
```
#####Using the commons chunk bundle
```
var CommonsChunkPlugin = require('./node_modules/webpack/lib/optimize/CommonsChunkPlugin')
```
Update:
```
module.exports = {
  entry: './src/main.js,
  output:{
    path:'build',
    filename:'bundle.js'
  },
  module:{
    loaders:[
      {
        test:/\.js$/,
        exclude:/(node_modules)/,
        loader:'babel',
        query:{
          presets:['es2015']
        }
      },
      {
        test:/\.css$/,
        loader:'style-loader!css-loader'
      }
    ]
  },
  plugins:[
    new CommonsChunkPlugin('commons','commons.bundle.js')//bundle all
  ]
}
```
#####Bundling vendor files

#### webpack dev server
#####Setting up the webpack-dev-server
```
module.exports = {
  entry: './dist/app.js,
  output:{
    path:'build',
    filename:'bundle.js'
  },
  devServer:{
    inline:true,
    contentBase:'./build',
    port:3000
  },
  module:{
    loaders:[
      {
        test:/\.js$/,
        exclude:/(node_modules)/,
        loader:'babel',
        query:{
          presets:['es2015']
        }
      },
      {
        test:/\.css$/,
        loader:'style-loader!css-loader'
      }
    ]
  }
}
```
