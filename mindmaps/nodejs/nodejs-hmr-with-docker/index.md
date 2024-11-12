---
title: Node.js Docker <br/>development environment <br/>with hot code reloading
markmap: 
  colorFreezeLevel: 2 
  collapsed: false
  nodeMinHeight: 30
  # maxWidth: 300
  initialExpandLevel: 2
---
## <mark>Hot Module Reload (HMR)</mark> is primarily useful in development environments <br/>as it allows you to see changes instantly <br/>in your application without needing a full refresh <br/>or restart. 

## Dev- Starter Kit simple(HMR)
- Project structure  
  - ```sh
      project/
      ├── app/
      │   └── server.js
      ├── docker-compose.yml
      ├── .env
      └── package.json
    ```
- Installation 
  - ```sh
      mkdir project 
      cd project
      npm init -y 
      npm i express 
      npm i --save-dev nodemon 
    ```
- Example project 
  - .env 
    - ```sh
        PORT=1234
        NODE_ENV=development
      ```
  - `app/server.js`
    - ```js
        // app/server.js
        const express = require('express');
        const app = express();
        const PORT = process.env.PORT || 1234;

        app.get('/', (req, res) => {
          res.send('Hello, Docker with hot reloading!');
        });

        app.listen(PORT, () => {
          console.log(`Server running at http://localhost:${PORT}`);
        });
      ```
  - package.json 
    - ```json
        {
          "name": "docker-hot-reload-example",
          "version": "1.0.0",
          "main": "app/server.js",
          "scripts": {
            "dev": "nodemon app/server.js"
          },
          "dependencies": {
            "express": "^4.17.1"
          },
          "devDependencies": {
            "nodemon": "^2.0.22"
          }
        }
      ```
  - docker-compose.yml
    - ```yaml
        version: '3'
          services:
            app:
              image: node:18
              working_dir: /usr/src/app
              volumes:
                - .:/usr/src/app  # Mounts the project for hot reloading
                - nodemodules:/usr/src/app/node_modules  # Uses named volume for node_modules
              environment:
                - NODE_ENV=development
              command: bash -c "npm install && npm run dev"
              ports:
                - "1234:1234"  # Maps container port to localhost

          volumes:
            nodemodules:
              driver: local  # Defines the named volume for node_modules
      ```
  - Build project 
    - ```sh
        docker compose build 
        docker compose up -d 
      ```
