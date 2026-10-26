# Module 1
## Lesson 1: What is TypeScript

**Def:** Typescript is a programming language built on top of Js that adds **static type system**

Think about a calculator application. It expects numbers when performing addition. But what happens if somebody accidently passes a word instead of a number?

Js lets you do this:

	```code
	let price = 100;

	price = "expensive";

	console.log(price);
	```

Output:
	expensive


Js accepts the reassignment because variable can hold values of different types.

Now imagine that your application has hundreds of variables and functions.
An accidental value of the wrong type could cause a bug somewhere else in your program.

consider this TypeScript example: 

```ts
	let price : number = 100;
	price = "expensive";
```

TypeScript reports an error on the second line because  `expensive` is a string, 
while `price` is declared to hold a number.

The important thing to understand is that TypeScript helps catch mistankes, 
it doesn't automatically fix them.


## Topic 2 -- JavaScript versus TypeScript

let's compare the two directly

```js
	const add (a, b){
	return a + b;
	
	}
	console.log(add(10,20));
	console.log(add("10", 20));
```

> JavaScript executes both calls. The second produces `1020` because the string causes concantenation rather than numeric addition.

TypeScripy -- Calculator.ts

```ts
	const add(a: number, b: number): number {
		return a + b;
	}

	console.log(add(10, 20));
	console.log(add("10", 20));

 ```

> TypeScript flags the second call because its first argument is a string. The function expects a number.

Notice three new pieces of syntax:

- `a: number` - the parameter `a` must be a number.
- `b: number` - the parameter `b` must be a number.
- `: number` after the parentheses -- the functional is declared to return a number

Notice: a compiler error doesn't always stop JS  output from being generated.
TypeScript can emit JavaScript despite some type errors unless configured otherwise.
That's why we'll learn type  checking and runtime execution as separate concepts.

## Topic 3 -- What does **static typing** means? 

**Static type** 

Types are checked before the program runs, using the source code and the information available to the tupe checker

eg:

```ts
	let age: number = 22;

	age = "Twenty-two"; // Type error
```

**Dynamic typing**

In Javascript, the type of a value is determined as the program executes. A variable can be reassigned a value of a different type.
f
```ts 
	let age = 21;
	age = "Twenty-two" // allowed
```

> One subtle point: JavaScript has types. The difference isn't that JavaScript has no types.  Rather, JavaScript's types are associated with runtime values, while TypeScript adds checks that analyze how those values are used before execution .

## Topic 4 - Type checking versus runtime execution

The TypeScript annotation `: number` helps the compiler check your program.
It is generally doesn't become a runtime type declaration in the generated Js.

Which mean after the runtime end the code will become as nomal js without `ts` the annotation

eg: 

```ts 
        let score: number = 50;
        console.log(score);
```

the emmited JavaScript looks like this:

```ts 
        let score = 50;
        console.log(score);
```

**Catch-up concept:** TypeScript is not a replacement for Node.js TypeScript is the language and type-checking toolchain; Node.js is one enviroment that can execute JavaScript

And TypeScript's checks don't validate external data automatically. If an API sends "Hello"
where you expected a number , you will eventually need runtime validation as well.

## Topic -- 5 Type annotations versus type inference

TypeScript can determine many types automatically.

Explicit annotation

```ts
	let username: string = "Victoire";
```

Type inference: 

```ts
        let username = "Victoire";
```

> In the second example, Typescript infers that "userneme" is a string because you initialiazed it with a string.

Remember this rule

- **Annotation:** You explicitly tell Ts the type
- **Inference:** Ts figures out the type from the available information


The command `npm init -y` : used to initiliaze a Node project
The command `npm install --save-dev typescript` installs the TypeScript compiler and tools locally into your current project as a development dependency 

- `--save-dev` (or short form -D): Instructs npm to categorize this package under `devDependencies` in your `package.json`
- `typescript`: Specifies the targer package to download, which includes `tsc` (The typescript compiler)
- `npx tsc --init`: This generate a `tsconfig.json` file.
some ts code

```ts
let studentName: string = "Victoire";
let studentAge: number = 21;
let isLearning: boolean = true;

console.log(studentName);
console.log(StudentAge);
console.log(isLearning);

```

**Let us talk a bit about `npx tsc --init`**

It will generate a file `tsconfig.json`

that file contains couple of settings

- `target`: Specifies the Js language version that Ts should emit. it doesn't install 
Node.js or determine the Node.js version

In TypeScript, *“emit”* means to generate or output JavaScript code from your TypeScript code.

`module` and `moduleResolution`

These control how Js modules are emitted and how imports are resolved for modern Node.js
projects

`rootDir` and `outDir`

`rootDir` identifies the source-code directory, and `outDir` specifies where compiled JavaScript files are written


`strict` Enables a collection of stricter type-checking rules. We'll use it from the beginning because it encourages safer habits

`sourceMap` Generates source-map files that help debuggers connect the emmitted Js back
to your original TypeScript source.


`noEmitOnError` Prevents the compiler from generating output when it encounters errors during that compilation

`include` and `exclude` These tell TypeScript which source files to include and which 
directory to exclude from normal source discovery.

