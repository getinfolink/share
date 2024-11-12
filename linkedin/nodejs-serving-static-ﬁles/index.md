# Serving static ﬁles

When building a webserver with Express it's often required to serve a combination of dynamic content and static ﬁles.

For example, you may have `index.html` and `script.js` which are static ﬁles kept in the ﬁle system.
It is common to use folder named 'public' to have static ﬁles. In this case the folder structure may look like:

```sh 
  project root
    ├── server.js
    ├── package.json
    └── public
      ├── index.html
      └── script.js
```

This is how to conﬁgure Express to serve `static` ﬁles:
```js 
  const express = require('express');
  const app = express();
  app.use(express.static('public'));
```

__Note__: once the folder is conﬁgured, `index.html`, `script.js` and all the ﬁles in the "public" folder will be available in at
the root path (you must not specify `/public/` in the url). This is because, express looks up for the ﬁles relative to the
static folder conﬁgured. You can specify virtual path preﬁx as shown below:

```js 
  app.use('/static', express.static('public'));
```
will make the resources available under the `/static/` preﬁx.


## Multiple folders
It is possible to deﬁne multiple folders at the same time:

```js 
  app.use(express.static('public'));
  app.use(express.static('images'));
  app.use(express.static('files'));
```

When serving the resources Express will examine the folder in deﬁnition order. In case of ﬁles with the same name,
the one in the ﬁrst matching folder will be served.