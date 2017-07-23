# React with Hot reload
> Development without refresing the browser

## Why
I love Create-react-app, yet don't know why it still hasn't inplemented [react-hot-loader](https://github.com/gaearon/react-hot-loader/tree/master/docs). so I made this simle repo to show how cool it is.

![2017-07-23 18 32 37](https://user-images.githubusercontent.com/19645990/28503478-8fcb436a-6fd5-11e7-94f5-7bb08bbbdc16.gif)
> no browser refreshing feels so good

## How
```
$ create-react-app <dirname>
$ cd <dirname>
$ npm run eject
$ npm install --save react-hot-loader@next
```
in `config/webpack.config.dev.js` add `'react-hot-loader/patch'`  to entry array
```
  entry: [
     'react-hot-loader/patch',
 ]
```
in `index.js` wrap App component into AppContainer
```js
import { AppContainer } from 'react-hot-loader'

function render(Component) {
  ReactDOM.render(
    <AppContainer>
      <Component />
    </AppContainer>,
    document.getElementById('root')
  )
}

render(App)

if (module.hot) {
  module.hot.accept('./App', () => {
    render(App)
  })
}
```
```
$ npm start
```
and volia
