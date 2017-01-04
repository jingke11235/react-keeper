# React-Flex-Router
  A routing library of React, but more than router.  
  React-Router is a great product, we learned a lot from it. But we truely faced many problems that React-Router doesn't resolve in real using, especially in mobile APPs.  
  We did a lot to let React-Flex-Router fit mobile APPs, such as `Pages Cache`, `Scroll Memory`.  
  We add small component support, to let you project fit more flexible WEB or mobile APPs.  
  We create a lot of flexible ways, so you can config the router more simplely.   
  And more...
## Docs
  [Route Component](docs/Route.md)         - (How to config route component)    
  [Link Component](docs/Link.md)           - (How to config Link component)  
  [Filter](docs/Filter.md)                 - (How to use filters)  
  [FlexComponent](docs/FlexComponent.md)   - (How to config path of route)  
  [RouteMapping](docs/RouteMapping.md)     - (How to config path of route)  

## Usage
  ```
  npm install react-flex-router --save-dev
  ```

## Features

* ***Extensible route***

  You can add route components ***anywhere,anytime***.
  ```javascript
  const App = ()=> {
    return (
      <HashRouter>
        <div>
          <Route lock component={ Home } path="/"/>
          <Route component={ Products } path="/products"/>
        </div>
      </HashRouter>
    )
  }

  const Products = ()=> {
    return (
      <div>
        <Route component={ ScienceProducts } path="/sci" />
        <Route component={ DailiUseProducts } path="/dai" />
      </div>
    )
  }

  ReactDOM.render(<App/>, document.getElementById('root'))
  ```

* ***Pages Cache***
  1. Use `cache` tag to lock a page.
  3. Use `CacheLink` Component to hold a will-unmount's page when open a new page.

* ***Memory of scroll position***

  Remember the scroll positions of every page, for scrolling to same position when back to a page.

* ***Add FlexComponent's frame***

  Flexible web projects will need a lot of small and flexible components(Such as: float login panel, changeable advert, popup dialogs, and so on), which will be added to document ***anywhere,anytime***, it's high-cost without `FlexComponent's frame`.

* ***Supports loading components dynamicly***

  Load a component dynamicly when it's route matches.

* ***Supports enter(and leave) filters***
  * `Enter filters`, filters run before a route mount succeed, such as : login's check.
  * `Leave filters`, filters run before a route unmount succeed, such as : unsubmited form data.

* ***Pretty flexible***
  * `index` tag : Index page of a module.
  * `miss` tag : When miss match.
  * `lock` tag : Lock a page for preventing to unmount after it mounted.
  * `muiltiple` tag : For muiltiple matching's need.
  ```javascript
  <HashRouter>
    <div>

      <Route lock component={ Home } path="/"/>

      <Route component={ Products } path="/products" enterFilter={ loginFilter }>
        <Route index component={Enterprise} path="/ep"/>
        <Route miss component={ NotFound }/>
        <Route component={ Detail } path="/item/:id" time={new Date().toLocaleString()}/>
      </Route>

      <Route muiltiple component={ Home }  path="/products">
        <Route index component={ ProductNav }/>
      </Route>

    </div>
  </HashRouter>
  ```
* ***Supports rendering in server side***

## Install
  ```
  npm install react-flex-router --save-dev

  npm install
  ```

## Usage
  App.js
  ```javascript
  import React, { Component } from 'react'
  import ReactDOM from 'react-dom'
  import { HashRouter, Route } from 'react-flex-router'
  import User from './User'
  // other import

  class App extends Component {
    render(){
      return (
        <HashRouter>
          <div>

            <Route lock component={ Home } path="/"/>

            <Route component={ Products } path="/products" enterFilter={ loginFilter }>
              <Route index component={Enterprise} path="/ep"/>
              <Route miss component={ NotFound }/>
              <Route component={ Detail } path="/item/:id" time={new Date().toLocaleString()}/>
            </Route>

            <Route muiltiple component={ User }  path="/user"/>

          </div>
        </HashRouter>
      )
    }
  }

  ReactDOM.render(<App/>, document.getElementById('root'))  
  ```
  User.js
  ```javascript
  import React, { Component } from 'react'
  import { Link, Route } from 'react-flex-router' 
  // other import

  export default class User extends Component {
    render(){
      return (
        <div>
          <ul>
            <Link to='/info'>Info</Link>
            <Link to='/edit'>Edit</Link>
          </ul>

          <div>
            <Route index component={ UserInfo } path='/info'/>
            <Route component={ UserInfoEdit } path='/edit'/>
          </div>
        </div>
      )
    }
  }
  ```

## Contributors 
  * ***Clone Project***
  ```
  git clone git@github.com:vifird/react-flex-router.git

  cd react-flex-router

  npm install
  ```
  
  * ***Run Example***
  ```
  npm run example
  ```
  Then open `http://127.0.0.1:8600`
