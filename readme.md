# JSPM Starter-ts

**Warning!** This starter uses JSPM in **beta** version.

A boilerplate for JSPM project. Includes configuration with TypeScript as a transpiler.

Run `npm install && npm start` to install all npm & JSPM dependencies and run the application (uses BrowserSync out of the box).

## How does it work?

### Transpilation
The entry point is `src/main.js` file. In development, the code is transpiled "live" (no need to serve the output files).

However, in `index.html` two scripts are referenced: `dist/build.js` and `dist/build.js.map`. These are the results of production build,
which can be triggered by issuing `npm run jspm:build-prod`. When these files exist, a production (transpiled and concatenated into one large bundle) version is served.

### Installing dependencies
The dependencies should be install via `npm run jspm:install <desired-dependency-name>` or `npm run jspm:install npm:<desired-dependency-name>` (if not found in JSPM registry).
This is a recommended way to do that - this way, JSPM is aware of the existence of dependencies and can correctly locate them while you `import` them into your code.

Example: `npm run jspm:install npm:lodash` to install lodash from npm, but at the same time let JSPM know that you will use that library.

You also need to run `npm run jspm:install` to install all dependencies managed by JSPM (ie. after you delete the `jspm_packages` directory). Please note that it is done
automatically in project's `postinstall` hook.

### Re-initializing JSPM project configuration
You can run `npm run jspm:reinit` to re-initialize jspm project (JSPM will ask questions, eg. about the transpilers you want to use)
