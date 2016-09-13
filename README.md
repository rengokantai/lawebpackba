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
