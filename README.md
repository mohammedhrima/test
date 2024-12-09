# how to publish a npm package

```bash
    npm init -y
```

```json
    {
      "name": "test-server",
      "version": "1.0.0",
      "description": "A simple web server",
      "main": "server.js",
      "bin": {
        "test-server": "server.js"
      },
      "dependencies": {
        "express": "^4.21.2"
      }
    }
```

```bash
    npm install express
    touch server.js
```

```js // server.js
#!/usr/bin/env node

const express = require("express");
const { program } = require("commander");

program.option("-p, --port <number>", "Port to run the server", "3000").parse(process.argv);

const options = program.opts();
const app = express();
const port = parseInt(options.port, 10);

app.get("/", (req, res) => {
  res.send("Hello from Hrima Server!");
});

app.listen(port, () => {
  console.log(`Hrima Server is running at http://localhost:${port}`);
});

```

```bash
    chmod +x server.js
    npm link
    test-server
```

```bash
    npm login
    npm publish
```

```bash
    npm install -g test-server
    test-server
```

```bash
    npm uninstall -g test-server
```
