
# How to run a TypeScript Script
There are several ways to run a TypeScript script. 

## Compile and Run with `tsc` (TypeScript Compiler)
Compile the TypeScript file:
```sh
tsc index.ts
```
This will generate a JavaScript file, typically `index.js`.


Run the generated JavaScript file:
```sh 
node index.js
```

<div style="page-break-after: always;"></div>


## Using ts-node 
Project setup 

```sh 
  npm init -y 
  touch tsconfig.json 
```

tsconfig.json
```json
{
  "compilerOptions": {
    "module": "commonjs",
    "target": "es6",
    "strict": true
  }
} 
```

Make sure you have `ts-node` and `typescript` installed. 
```sh
  npm install ts-node typescript 
```

Run the script 
```sh 
  npx ts-node ./index.ts
  // Or

  ./node_modules/.bin/ts-node index.ts
```

<div style="page-break-after: always;"></div>



## Use `tsx` for Running TypeScript
tsx is a modern, fast alternative to ts-node. It automatically runs TypeScript files without the need for compiling them first.

Install tsx:

```bash
npm install -g tsx
```

Run the TypeScript script:

```bash
tsx index.ts
```

<div style="page-break-after: always;"></div>



## Use `esbuild` to Compile and Run
esbuild is an ultra-fast bundler and compiler. It can also execute TypeScript files.

Install esbuild:

```bash
npm install -g esbuild
```

Run the TypeScript file:

```bash
esbuild index.ts --bundle --outfile=out.js && node out.js
```

This compiles the TypeScript file and outputs a bundled out.js, which is then executed with Node.js.


<div style="page-break-after: always;"></div>



## Using `Babel` with TypeScript
Babel can also be used to `transpile` TypeScript into JavaScript, though it doesn’t check types (it just strips them).

Install Babel along with TypeScript preset:

```bash
npm install --save-dev @babel/core @babel/cli @babel/preset-typescript
```
Create a `.babelrc` file:

```json
{
  "presets": ["@babel/preset-typescript"]
}
```
Then, compile and run the script:

```bash
npx babel index.ts --out-file index.js
node index.js
```
<div style="page-break-after: always;"></div>



## Compile `ts` and run output file 
```sh
  npm i nodemon 
  npm i ts-node 
  nodemon --watch src/**/*.ts --exec 'ts-node'  src/index.ts 

  // --watch : Watches your TypeScript files in the src directory.
  // --exec Runs the TypeScript files using ts-node
  // index.ts: The entry file you want to run.
```
<div style="page-break-after: always;"></div>


![](../../assets/ads/img-001.png)








