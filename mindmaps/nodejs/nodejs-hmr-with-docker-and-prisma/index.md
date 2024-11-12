---
title: Node.js Docker <br/>development environment <br/>with hot code reloading
markmap: 
  colorFreezeLevel: 2 
  collapsed: false
  nodeMinHeight: 30
  # maxWidth: 300
  initialExpandLevel: 2
---

## Dev- Starter Kit advanced(with Prisma, Docker, HMR )
- Project structure diagram
  - ```sh
      project/
        ├── app/
        │   └── server.js
        ├── prisma/
        │   └── migrations  
        │     └── schema.prisma  
        ├── .env   
        ├── docker-compose.yml
        └── package.json
    ```
- Create project basic code 
  - `project/app/server.js` 
    - ```js
        const express = require('express');
        const { PrismaClient } = require('@prisma/client');

        const prisma = new PrismaClient();
        const app = express();

        // Use JSON parsing
        app.use(express.json());

        // CORS headers
        app.use((req, res, next) => {
          res.setHeader('Access-Control-Allow-Origin', '*');
          res.setHeader('Access-Control-Allow-Methods', 'GET, POST, PUT, DELETE');
          res.setHeader('Access-Control-Allow-Headers', 'Content-Type, Authorization');
          next();
        });

        // Test API route with error handling
        app.get('/test', (req, res, next) => {
          try {
            res.status(200).json({ message: 'Success..3!' });
          } catch (err) {
            next(err);
          }
        });

        // Get all users
        app.get('/users', async (req, res, next) => {
          try {
            const users = await prisma.user.findMany();
            res.status(200).json(users);
          } catch (err) {
            next(err);
          }
        });

        // Get user by ID
        app.get('/users/:id', async (req, res, next) => {
          try {
            const user = await prisma.user.findUnique({
              where: { id: Number(req.params.id) },
            });
            res.status(200).json(user);
          } catch (err) {
            next(err);
          }
        });

        // Create user
        app.post('/users', async (req, res, next) => {
          try {
            const user = await prisma.user.create({
              data: { ...req.body },
            });
            res.status(201).json(user);
          } catch (err) {
            next(err);
          }
        });

        // Update user
        app.put('/users/:id', async (req, res, next) => {
          try {
            const user = await prisma.user.update({
              where: { id: Number(req.params.id) },
              data: { ...req.body },
            });
            res.status(200).json(user);
          } catch (err) {
            next(err);
          }
        });

        // Delete user
        app.delete('/users/:id', async (req, res, next) => {
          try {
            const user = await prisma.user.delete({
              where: { id: Number(req.params.id) },
            });
            res.status(200).json(user);
          } catch (err) {
            next(err);
          }
        });

        // Start server
        const PORT = process.env.PORT || 1234;
        app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
      ```
  - `project/prisma/migrations/schema.prisma` 
    - ```js
        generator client {
          provider = "prisma-client-js"
        }

        datasource db {
          provider = "postgresql"
          url      = env("DATABASE_URL")
        }

        //User with id as int autoincrement, name as string, email as string
        model User {
          id    Int    @id @default(autoincrement())
          name  String
          email String
        } 
      ```



  - `project/.env` 
    - ```sh
        DATABASE_URL="postgresql://postgres:postgres@db:5432/postgres"
      ```
  - `docker-compose.yml` 
    - ```sh
        # version: '3.9'
        services:
          app:
            image: node:18
            working_dir: /usr/src/app
            volumes:
              - .:/usr/src/app  # Mounts the project for hot reloading
              - nodemodules:/usr/src/app/node_modules  # Named volume for node_modules
            environment:
              - NODE_ENV=development
            #command: bash -c "npm install && npm run dev"
            command: bash -c "npm install && npx prisma generate && npm run dev"
            ports:
              - "1234:1234"  # Maps container port to localhost
            depends_on:
              - db  # Ensures db service starts before app

          db:
            container_name: pgdb
            image: postgres:12
            restart: always
            environment:
              POSTGRES_USER: postgres
              POSTGRES_PASSWORD: postgres
              POSTGRES_DB: postgres
            ports:
              - "5432:5432"  # Expose PostgreSQL port
            volumes:
              - pgdata:/var/lib/postgresql/data  # Persist data in a named volume

        volumes:
          nodemodules:
            driver: local
          pgdata:
            driver: local
      ```
  - `package.json` 
    - ```sh
        {
          "name": "docker-hot-reload-example",
          "version": "1.0.0",
          "main": "app/server.js",
          "scripts": {
            "dev": "nodemon app/server.js"
          },
          "dependencies": {
            "express": "^4.17.1",
            "@prisma/client": "^4.0.0" 
          },
          "devDependencies": {
            "nodemon": "^2.0.22"
          }
        }
      ```
  - running 
    - ```sh 
        docker ps -a
        docker exec -it pgdb psql -U postgres
        \dt
        docker exec -it backend npx prisma migrate dev --name init
      ```

- Run the setup  
  - Build the `backend` image:
    - ```sh
        docker compose build
      ```
  - Start the `backend` container:
    - ```sh 
        docker compose up -d backend
      ```
  - Check if the container is running:
    - ```sh 
        docker ps -a
      ```

  - Check database 
    - ```sh 
        docker exec -it pgdb psql -U postgres
        \dt
      ```
  - Make migration 
    - ```sh 
        docker exec -it backend npx prisma migrate dev --name init
      ```
    - ```sh 
        docker exec -it pgdb psql -U postgres
        \dt
      ```
