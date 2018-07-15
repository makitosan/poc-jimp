# poc-jimp

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

# JIMP
https://github.com/oliver-moran/jimp

# PROBLEM & TWEAKS

## Buffer

On Browser the following error message is displayed.

```
jimp.js?481b:53 Uncaught Error: Node's Buffer() not available
    at Object.eval (jimp.js?481b:53)
    at eval (jimp.js:129)
    at Object../node_modules/jimp/browser/lib/jimp.js (app.js:851)
    at __webpack_require__ (app.js:679)
    at fn (app.js:89)
    at eval (main.js?1c90:7)
    at Object../src/main.js (app.js:1098)
    at __webpack_require__ (app.js:679)
    at fn (app.js:89)
    at Object.0 (app.js:1115)
```

Solution:

https://github.com/oliver-moran/jimp/issues/280

Use 0.2.27 instead

```package.json
    "jimp": "=0.2.27"
```
