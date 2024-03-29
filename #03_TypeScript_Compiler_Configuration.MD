<h1 align="center">TypeScript Compiler</h1>

### Overview of the Section
* **[Using "Watch Mode"](#watch-mode)**
* **[Compiling the Entire Project / Multiple Files](#tsc-init)**
* **[Including & Excluding Files](#including-excluding-files)**
* **[Compiler Options](#compiler-options)**
* **[TypeScript Core Librarys'](#core-lib)**
* **[Working with Source Maps](#working-with-source-maps)**
* **["rootDir" and "outDir"](#root-dir)**
* **[Strict Compilation](#strict-compilation)**



### <a name="watch-mode">Using "Watch Mode"</a>

``tsc app.js -w`` is used with the TypeScript Compiler (tsc) to transpile TypeScript code into JavaScript. 

In summary, ``tsc app.js -w`` is a command that tells the TypeScript Compiler to watch for changes in the ``app.ts`` file and recompile it into JavaScript whenever changes are detected. 

#
### <a name="tsc-init">Compiling the Entire Project / Multiple Files </a>

- **Step 1**: Run ``tsc --init`` - creates ``tsconfig.json`` file.
- **Step 2**: Run ``tsc -w`` - every change in either file will automatically update the whole project.

#
### <a name="including-excluding-files">Including & Excluding Files</a>

 The ``tsconfig.json`` file you provided contains settings for including and excluding files during the TypeScript compilation process.

```
{
    "compilerOptions": {},
    "exclude": [
        "analytics.ts",        // This file will not be compiled.
        "*.dev.ts",            // All files with .dev.ts extension will be ignored by the compiler.
        "**/*.dev.ts",         // Any file with this pattern in any folder will be ignored.
        "node_modules"         // Files in the node_modules folder are ignored by default.
    ],
    "include": [
        // Anything that's not listed here will not be compiled.
    ]
}
```

- The ``exclude`` section is used to specify files and patterns that should be excluded from compilation.
- The ``include`` section, when populated, would specify the files that should be explicitly included for compilation. However, since it's empty, TypeScript will include all TypeScript files by default, except those listed in the exclude section.
#
**[Back To The Top](#Overview-of-the-Section)**

### Compiler Options
```
/* Language and Environment */
    "target": "es2016",    /* Set the JavaScript language version for emitted JavaScript and include compatible library declarations. */
```
#
### <a name="core-lib">TypeScript Core Librarys'</a>

In the TypeScript ``tsconfig.json`` file, the ``"lib"`` compiler option is used to specify a set of bundled library declaration files that describe the target runtime environment.

- **[TypeScript - What is a tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)**
- **[TypeScript - tsc CLI Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html)**

#
**[Back To The Top](#Overview-of-the-Section)**

### Working with Source Maps

**Source Maps**: 
Source maps are files that establish a mapping between the original TypeScript code and the generated JavaScript code. 

When you set **"sourceMap": true**, you instruct the TypeScript compiler to generate these source maps alongside the compiled JavaScript code.

**Advantages**: Readable Debugging: Source maps provide a seamless debugging experience by allowing developers to work with the original TypeScript code in the debugging tools, even though the code running in the browser is JavaScript.

![DevTools](https://github.com/tsokac2/-_-_TypeScript_CheatSheet/blob/main/src/01.JPG)

#
**[Back To The Top](#Overview-of-the-Section)**

### <a name="root-dir">"rootDir" and "outDir"</a>

### ``"rootDir": "./src"``
**Explanation**: This option sets the root directory within your source files. 

In your example, the ``"rootDir"`` is set to ``"./src"``, indicating that the TypeScript compiler should consider ``./src`` as the root directory for your TypeScript source files.

### ``"outDir": "./dist"``
**Explanation**: This option specifies the output directory for all emitted (compiled) files. In your example, the ``"outDir"`` is set to ``"./dist"``, meaning that the compiled JavaScript files will be placed in the dist directory.

#
**[Back To The Top](#Overview-of-the-Section)**

### Strict Compilation

TypeScript, being a superset of JavaScript, introduces strict type-checking options to enhance the reliability and maintainability of your code.

``strictNullChecks``
- **Description**: This option is fundamental for avoiding the common issue of ``null`` or undefined values causing unexpected behavior in your code.

``strictBindCallApply``:
- **Description**: This option is designed to improve the correctness of function calls and the usage of functions like bind, call, and apply.

``strictPropertyInitialization``
- **Description**: This option helps in ensuring that class properties are always initialized before they are used.

#
### Debugging with Visual Studio Code

**File - Preferences - Extensions**:

- ESLint
- Prettier - Code formatter
- JavaScript Debugger

**[VS Code TS Debugging](https://code.visualstudio.com/docs/typescript/typescript-debugging)**

**[Back To The Top](#Overview-of-the-Section)**