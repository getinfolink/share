
# Node.js - Adding Middleware
![](https://media.licdn.com/dms/image/D4D12AQE7-n46XKs6yA/article-cover_image-shrink_600_2000/0/1678766687037?e=2147483647&v=beta&t=F05a7Xz55kIxOgdtQ3hEG-NfaQl-Yzyzg1zjj47IW1s)



<mark>Middleware functions allow you to handle and modify requests and responses objects, end response cycle and call next middleware.</mark>

<u>Very common example of middleware is cors module.</u> To add CORS support, simply install it, require it and put this line:

```js 
    app.use(cors());
```
<div style="page-break-after: always;"></div>

## Simple Middleware Example
A basic logging middleware that logs the request method and URL for every request:

```js
  const express = require('express');
  const app = express();

  // Simple logging middleware
  app.use((req, res, next) => {
    console.log(`${req.method} ${req.url}`);
    next(); // Passes control to the next middleware function
  });

  app.get('/', (req, res) => {
    res.send('Hello, World!');
  });

  app.listen(3000, () => {
    console.log('Server is running on http://localhost:3000');
  });
```

Here, `app.use()` applies middleware globally to all routes. The `next()` function passes control to the next middleware or route handler.

<div style="page-break-after: always;"></div>

## Advanced Middleware Example
An authentication and authorization middleware, where a token is checked, and permissions are verified.

```js
  const express = require('express');
  const app = express();

  // Token verification middleware
  function authenticateToken(req, res, next) {
    const token = req.header('Authorization');
    
    if (!token) {
      return res.status(401).json({ message: 'Access denied. No token provided.' });
    }

    // Mock token validation
    if (token === 'VALID_TOKEN') {
      req.user = { id: 1, role: 'admin' }; // Mock user information
      next(); // Passes control to the next middleware or route
    } else {
      res.status(403).json({ message: 'Invalid token.' });
    }
  }

  // Authorization middleware for role-based access
  function authorizeRole(role) {
    return (req, res, next) => {
      if (req.user && req.user.role === role) {
        next();
      } else {
        res.status(403).json({ message: 'Forbidden: Access denied. Insufficient permissions.' });
      }
    };
  }

  // Routes with middleware
  app.get('/admin', authenticateToken, authorizeRole('admin'), (req, res) => {
    res.send('Welcome, admin!');
  });

  app.get('/user', authenticateToken, (req, res) => {
    res.send('Welcome, authenticated user!');
  });

  app.listen(3000, () => {
    console.log('Server is running on http://localhost:3000');
  });
```
<div style="page-break-after: always;"></div>


### `user` route testing with Curl  
To test this, use two different curl commands:

#### Without API Key (should be forbidden)

```bash
  curl http://localhost:1234/user
```
This should return `{"message":"Access denied. No token provided."}` with a `403` status.

#### With API Key (should be allowed)
```bash
  curl -H "Authorization: VALID_TOKEN" http://localhost:1234/user
```
This should return `Welcome, authenticated user!`.

<div style="page-break-after: always;"></div>



###  `admin` route testing with Curl
To test this, use two different curl commands:

#### Without API Key (should be forbidden)

```bash
  curl http://localhost:1234/admin
```
This should return `{"message":"Access denied. No token provided."}` with a `403` status.

#### With API Key (should be allowed)
```bash
  curl -H "Authorization: VALID_TOKEN" http://localhost:1234/admin
```
This should return `Welcome, admin!`.


<div style="page-break-after: always;"></div>

![](../../assets/ads/img-001.png)



