<h1 align="center">TypeScript Basics & Basic Types</h1>

### Overview of the Section
* **[Using "Watch Mode"](#watch-mode)**
* **[Compiling the Entire Project / Multiple Files](#tsc-init)**

### <a name="watch-mode">Using "Watch Mode"</a>

``tsc app.js -w`` is used with the TypeScript Compiler (tsc) to transpile TypeScript code into JavaScript. 

In summary, ``tsc app.js -w`` is a command that tells the TypeScript Compiler to watch for changes in the ``app.ts`` file and recompile it into JavaScript whenever changes are detected. 

### <a name="tsc-init">Compiling the Entire Project / Multiple Files </a>

- **Step 1**: Run ``tsc --init`` - creates ``tsconfig.json`` file.
- **Step 2**: Run ``tsc -w`` - every change in either file will automatically update the whole project.

#
**[Back To The Top](#Overview-of-the-Section)**
