---
title: Node.js Basic Routing
markmap: 
  colorFreezeLevel: 2 
  collapsed: false
  nodeMinHeight: 30
  # maxWidth: 300
  initialExpandLevel: 2
---

## Initialize the App
- ```js
    const express = require('express');
    const app = express();
  ```


## Define Routes
- Use specific HTTP methods:

- ```js
    app.get('/myPath', (req, res, next) => {})
    app.post('/myPath', (req, res, next) => {})
    app.put('/myPath', (req, res, next) => {})
    app.delete('/myPath', (req, res, next) => {})
  ```

- Apply to all methods for a route:

- ```js
    app.all('/myPath', (req, res, next) => {})
    app.use('/myPath', (req, res, next) => {})
    app.use('*', (req, res, next) => {})  // wildcard for all paths
  ```


## Chaining for a Single Path
- ```js
    app.route('/myPath')
      .get((req, res, next) => {})
      .post((req, res, next) => {})
      .put((req, res, next) => {})
  ```
## Middleware Functions
- Add middleware before the final callback:
- ```js
    app.get('/myPath', myFunction, (req, res, next) => {})
  ```


## Organize Route Handlers
- Store route handlers in separate files for cleaner code:

- ```js
    // other.js
    exports.doSomething = (req, res, next) => { /* do stuff */  };

    // main file
    const other = require('./other.js');
    app.get('/someUri', myFunction, other.doSomething);
  ```
