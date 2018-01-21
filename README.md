# Rua-Dva
Easier way to use dva.js (Inspired by [MirrorJs](https://github.com/mirrorjs/mirror))

[中文介绍](./README-zhCN.md)

## Stable Version: 0.4.1
`yarn add rua-dva@0.4.1`

## What is Dva?
[dvajs/dva](https://github.com/dvajs/dva)

## Features
- `actions` simplifies `dispatch` function  (See usage 1,2,3)
- `dvaLite` provides a lite version of dva  (original dva integrates react router)
- [Under Development] `dvaReactNavigation` provides dva which integrates `React Navigation`

## Todo
- [ ] dvaReactNavigation

## Bootstrap

### Setup
```
// import
import { ruaDva } from 'rua-dva'
 
// create dva
const app = dva({
  extraEnhancers: [],
  onError(e) {
    console.log(e.message);
  },
})
 
// rua
ruaDva(app)
 
// models
app.use(xxx)
...
app.start(xxx)
...
```

### Usage 1
```
// before
...
this.props.dispatch({
  type: 'auth/logout',
})
...
 
// import
import { actions } from 'rua-dva'
 
// now
...
actions.auth.logout()
...
```

### Usage 2

```
// before
...
this.props.dispatch({
  type: 'auth/login',
  payload: {
    username: 'admin',
    password: 'rua and roll',
  }
})
...
 
// import
import { actions } from 'rua-dva'
 
// now
...
actions.auth.login({
  username: 'admin',
  password: 'rua and roll',
})
...
```

### Usage 3

```
// before
...
this.props.dispatch({
  type: 'auth/loginAsync',
  payload: {
    username: 'admin',
    password: 'rua and roll',
  },
  success: () => console.log('yeah~'),
  failure: () => console.log('no~'),
})
...
 
// import
import { actions } from 'rua-dva'
 
// now
...
actions.auth.loginAsync({
  username: 'admin',
  password: 'rua and roll',
}, {
  success: () => console.log('yeah~'),
  failure: () => console.log('no~'),
})
...
