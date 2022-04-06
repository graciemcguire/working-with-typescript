# Working with TypeScript Code Along

## Learning Goals

- Successfully set up a local environment to run TypeScript
- Configure and understand the tsconfig.json file
- Practice compiling with `tsc`

## Introduction

TypeScript is a very useful and powerful tool we can use to optimize our code by
checking for syntax errors before runtime, giving tips on how to fix bugs before
they happen and more, all by adding in types to our regular JavaScript code!
Though we can start using TypeScript right out of the box, it does recognize
that every application and developer is different, and gives us some room for
flexibility. We get access to this flexibility/customization through the
ts.config file that we will keep in the root of our application, where we can
change default rules, and add some rules of our own!

## Environment Setup

- fork and clone this lab, then open in your text editor
- install ts globally

You should already have Node Installed on your machine, but if you haven't,
please do so following the [Node.js Installation Docs][]. If you would like a
more detailed walk through, please check out the following repositories:

- [Installing NVM & Node.js on MacOS][]
- [Installing NVM & Node.js on WSL2][]

While we can install TypeScript globally, it's generally best practice to do so
on a project-by-project basis to avoid different versioning across machines.
Let's install TypeScript to this project by running the following code in your
terminal _(Remember to cd into the correct project directory!)_:

```zsh
$ npm install typescript --save-dev
```

Once TypeScript is done installing into our project, you should see some
node_modules files appear into our file directory. Our next step is adding in
our `tsconfig.json` file.

## The tsconfig.json file

So what _is_ the tsconfig.json file? The tsconfig file is used to help us
configure and compile our code! This file is _always_ kept in the root of our
project, and is used to identify the compiler rules we want to enforce, as well
as specify the root files of the project. The rules the compiler enforces are
completely customizable and up to you to determine based on your project needs.

There's unlimited ways that you can setup your tsconfig.json file, and a lot of
different properties you can add to it.

Let's create our tsconfig.json file in the root of our project directory by
running:

```zsh
$ touch tsconfig.json
```

Awesome. Now let's fill in our properties. Were going to start with a
`"compilerOptions"` key with an object as it's value. The `"compilerOptions"`
object property is what we will use to declare the rules we want to enforce in
our project. Inside of the `"compilerOptions"` object, we're going to add 3
properties.

Let's start by adding the property`"module"`, and setting it's value to
`"commonjs"`. This tells TypeScript that we intend to use `commonjs` syntax for
importing and exporting modules. Next, add the `"target"` property.

The `"target"` property is used to tell TypeScript what version of ECMAscript we
will be using. Because all modern browsers are able to use `es6`, let's set that
value to `"es6"`. If we were sure we would only be using newer or updated
browsers we could set our value to include the year (e.g. `es2022`), or even
`esnext`.

Our final property to add is`"strictNullChecks"`, which makes sure no variable
has the value of `null` or `undefined` unless we explicitly assign them.

Let's add one more property to our json object, `"include": ["**/*.ts"]`. The
`include` property tells our compiler what files to check our rules against. Our
value, `["**/*.ts"]`, tells the compiler to run these rules against every file
in our project that has the extension `.ts`.

You should now have an object that looks something like this:

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "target": "es6",
    "strictNullChecks": true
  },
  "include": ["**/*.ts"]
}
```

For this exercise, we're working with a very simple `tsconfig.json` file, but
it's definitely worth taking a look at the [TypeScript Docs - tsconfig][] for
more compiler options and properties to add to your projects in the future!

## Compiling with `tsc`

- run tsc to see the errors
- then fix the errors
- then run tsc to see there are no more errors
- run node index.js to run our code
- submit code

Now that we have our `tsconfig.json` setup, we're able to compile our code using
the `tsc` command! There's a ton of different compiler options for us (check out
[TypeScript Docs - Compiler Options][] to see them all!) to use... we can use
the command by adding a specific file to it like `npx tsc index.ts`, or we can
run it as is `npx tsc`!

At a high level, when we run `npx tsc`, our program takes our `.ts` files and
_compiles_ them into JavaScript code, or `.js` files. Woah! This command not
only creates our `.js` files in the same directory as our `.ts` files, but also
is how we are able to see the errors and bugs that the transpiler has found,
allowing us to fix them immediately.

If you try running `npx tsc` right now however, you'll probably get an error
back saying something like this:

```zsh
error TS18003: No inputs were found in config file
```

Let's fix that by creating some files to test this out!

- Create a file `index.ts`
- In your file add console.log of a string saying _"Hello, TypeScript World!"_
- Now run `npx tsc`
- You should now have a newly created `index.js` file
- Let's run our js file to see our message print out into the console

```zsh
node index.js
```

## Conclusion

In this lesson we were able to set up our local environment to run TypeScript
files, and configure our own tsconfig.json file from scratch. We also learned
how to use the TypeScript compiler to run our code and compile our `.ts` files
into JavaScript!

## Installation Resources

- [TypeScript Docs - Download TypeScript](https://www.typescriptlang.org/download)
- [Node.js Installation Docs](https://nodejs.org/en/)
- [Installing NVM & Node.js on MacOS](https://github.com/learn-co-curriculum/phase-0-macos-env-nodejs)
- [Installing NVM & Node.js on WSL2](https://github.com/learn-co-curriculum/phase-0-wsl2-env-nodejs)

## Configuration Resources

- [TypeScript Docs - tsconfig](https://www.typescriptlang.org/tsconfig)
- [TypeScript Docs - module](https://www.typescriptlang.org/tsconfig#module)
- [TypeScript Docs - target](https://www.typescriptlang.org/tsconfig#target)
- [TypeScript Docs - strictNullChecks](https://www.typescriptlang.org/tsconfig#strictNullChecks)
- [TypeScript Docs - include](https://www.typescriptlang.org/tsconfig#include)
- [TypeScript Docs - Compiler Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html)
