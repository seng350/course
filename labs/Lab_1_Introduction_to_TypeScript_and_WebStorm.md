# Lab 1: Introduction to TypeScript and WebStorm
The project for SENG 350 will be developed in [TypeScript](https://www.typescriptlang.org), a superset of JavaScript. Typescript avoids many of the pitfalls of JavaScript and compiles to JavaScript. The main advantage of TypeScript is (as the name says) that it is a typed language and provides better concepts of object orientation. [Recent empirical studies](https://blog.acolyer.org/2017/09/19/to-type-or-not-to-type-quantifying-detectable-bugs-in-javascript/) show that using TypeScript (over JavaScript) can prevent *at least* 15% of coding bugs.


## Step 1: Check that TypeScript is installed

You can check that TypeScript is installed by validating that the TypeScript compiler is available:


    tsc -v

If it is not installed, you can install it using the Node package manager (npm). (Node.js is a runtime engine for JavaScript. It should be installed in the lab. You can also install it on your own computer by downloading the appropriate installer from the Node.js web site.)


    npm install -g typescript


## Step 2: Build a simple app

We will build a simple library application to demonstrate core TypeScript syntax and features including types, classes, and various ECMA Script 6 (ES6) features (that get transpiled down to ES5, which is supported in [most major browsers](http://caniuse.com/#feat=es5)). (ECMA Script is the standardized version of JavaScript.)

**Quick background**
To start, make a directory that will hold all of our files, and create this bare-bones HTML file, `index.html`, that will run the JavaScript code. (Just use a plain text editor for now.)


    <!DOCTYPE HTML>
    <html>
    <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    
    <title>Intro to Typescript</title>
    </head>
    <body>
    </body>
    
    <script src="intro.js"></script>

Note that the included script is just a normal `.js` file! We will transpile our TypeScript code into plain JavaScript. Next, in the same directory, create the `intro.ts` file:


    function hello(name: string) {
        return "Hello, " + name;
    }
    
    document.body.innerHTML = hello("world!");

This is standard JavaScript with the exception of `name: string` on the first line. This is called a **type annotation**, which indicates that the `name`parameter must be a string.
Next, to compile, navigate to the directory in your terminal and run  `tsc intro.ts`, which will transpile `intro.ts` into JavaScript. There should be no output from this command, but an `intro.js` file will be silently generated. Let’s take a look at the generated code:


    function hello(name) {
        return "Hello, " + name;
    }
    
    document.body.innerHTML = hello("world!");

This is exactly the same code as above, except without the type annotation! So, this means that type checking is entirely handled by the compiler, which will print an error if there is a type mismatch, e.g. `hello(1)`, but the outputted JavaScript has no knowledge of types. This is consistent with how compilation works for statically typed languages such as C.[[1]](https://x-team.com/blog/introduction-typescript/#fn1)
If you open `index.html` in a browser, the page should display `Hello, world!`, as expected. Go ahead and confirm this!

**Building the app**
We will build a library application using object-oriented constructs in TypeScript. Books are an essential part of any library, so we can start out by creating a `Book` class:


    class Book { //Try exemplifying other classes similar to book in java and execute (using javac compile command) but with a different standard or nature: journal or paper or assignments with specific parameters involved (that adds to your parameters and could be usueful for your coding practice)
    title: string;
    isbn: number;  // Unique number used to identify books
    constructor(title: string, isbn: number) { 
    this.title = title;
    this.isbn = isbn;
    }
    }  

This is a departure from standard JavaScript syntax – let’s dig into what’s happening here. We define a **class** called `Book`, with the two **members**(also called instance variables) `title` and `isbn`. Both of these variables are annotated with their types. We also create a **constructor** for this class, which will instantiate a `Book` object with the two parameters.

Compile the code again and check out the generated JavaScript. You will see that this is implemented with an immediately-invoked function expression to manage scope and state. The generated JavaScript code should look like this:


    var Book = /** @class */ (function () {
        function Book(title, isbn) {
            this.title = title;
            this.isbn = isbn;
        }
        return Book;
    }());

For simplicity, we do not need to worry too much about the generated JavaScript from now on, since we will be programming at the level of TypeScript.

A much more compact, and stylistically better version of the above TypeScript class is:

    class Book {
        constructor(public title: string, public isbn: number) {}
    }

The `public` prefix to the constructor parameters tells the compiler to automatically declare and set the `title` and `isbn` members – it is equivalent to the previous code. (Go ahead and compile the new version to check that the generated JavaScript code is indeed the same.)

In addition to a title and ISBN, a library book may have an additional property that tracks whether it is available or not. Let’s implement this in a **subclass** of `Book` called `LibraryBook`. In addition, whenever the availability of a book changes, we’ll want to print an update. This can be done with **private members** and **getter/setter functions** in TypeScript:ls


    class LibraryBook extends Book {
        private _available = true;
        constructor(title: string, isbn: number) {
            super(title, isbn);
        }
    
        get available() { return this._available; }
        set available(isAvailable: boolean) {
            console.log(`"${this.title}" is now ${isAvailable ? 'available' : 'unavailable'}`);
            this._available = isAvailable;
        }
    }

There are many interesting things happening here! Let’s go through and discuss line-by-line. The first line declares a new class `LibraryBook`, that extends our previous class `Book`. This means that `LibraryBook` will inherit the structure of a `Book`, i.e. the two members `title` and `isbn`.

Next, we define the **private member**`_available` to be `true` on initialization, which is similar to how we explicitly declared the public member `title`previously, but with the addition of the `private` keyword. A private member can only be accessed within its own class, and not externally. This is necessary because we don’t want `_available` to be set directly, so we can print an update before its value changes; you’ll see how in a bit. The underscore prefix is a naming convention for private members.

The next function defines the constructor for `LibraryBook`. The `super()` call in its body will simply run the constructor of the parent class `Book` there, which sets the two members `title` and `isbn`.

Next, we have two functions defined with the keywords `get` and `set` – these are called accessors, or **getters/setters**. These functions are similar to creating a public member called `available`, except the functions are called whenever we read or write to the member. In other words, a statement like `var x = book.available` (get/read) or `book.available = false`(set/write), will call the appropriate function, even though the syntax suggests a simple variable expression.

The getter function is fairly straightforward. The setter function will set `book._available` to the argument `isAvailable`, taken from a statement such as `book.available = isAvailable`. It also prints an update using an [ES6 template string](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/template_strings).

Now we understand how `LibraryBook` is implemented! As a side note, we’ve now seen the data types `string`, `number`, and `boolean`. There are [a few other types](http://www.typescriptlang.org/Handbook) in TypeScript, including an `any` type, which allows a variable to take on any value, regardless of type – this is occasionally useful when working with existing JavaScript code.

Finally, let’s create a `Library` class that keeps track of a collection of `LibraryBook`‘s.


    class Library {
        books: LibraryBook[] = [];
        addBooks(...newBooks: LibraryBook[]) { 
            this.books.push(...newBooks); 
        }
        checkOut(book: LibraryBook) { 
            book.available = false; 
        }
        checkIn(book: LibraryBook) { 
            book.available = true; 
        }
        printBooks() {
            for (var book of this.books) {
                let {title, isbn} = book;
                console.log(`Title: "${title}", ISBN: ${isbn}`);
            }
        }
    }

This is fairly straightforward, but there is some important syntax hidden in these short functions, so let’s also go through this class line-by-line. At the top, we declare an independent class `Library`, which does not inherit from any other class.
Next, we define the sole member of `Library`, called `books`, initialized to an empty array. Note the array type annotation syntax is `: LibraryBook[]`, which means an array of `LibraryBook`‘s. Also, this class does not have an explicit constructor, since there are no other members to set!

The `addBooks()` function uses an [ES6 rest parameter](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/rest_parameters) to take in an arbitrary number of arguments, which we then append to the `books` member by using the [ES6 destructuring syntax](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/rest_parameters). Note an idiosyncrasy in using rest parameters in TypeScript: the argument is an array type `: LibraryBook[]`rather than an element type `: LibraryBook`.

The `checkOut()` and `checkIn()` functions are fairly straightforward. They take advantage of the getter/setter syntactic sugar we set up beforehand in the `LibraryBook` class.

The `printBooks()` function will log every book currently in the library. We use an [ES6 for…of loop](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Statements/for...of) to iterate through our `books` member. For each `LibraryBook` object, we use [ES6 object destructuring](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) to set the [block-scope variables](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Statements/let) `title` and `isbn` to the appropriate values in the `LibraryBook`instance. We can destructure a TypeScript object! Last, we print the book information to the console.
Finally, our app is complete! Try it out yourself – replace the contents of `intro.ts` with the following code:


    class Book {
        constructor(public title: string, public isbn: number) {}
    }
    
    class LibraryBook extends Book {
        private _available = true;
        constructor(title: string, isbn: number) {
            super(title, isbn);
        }
    
        get available() { return this._available; }
        set available(isAvailable: boolean) {
            console.log(`"${this.title}" is now ${isAvailable ? 'available' : 'unavailable'}`);
            this._available = isAvailable;
        }
    }
    
    class Library {
        books: LibraryBook[] = [];
        addBooks(...newBooks: LibraryBook[]) { 
            this.books.push(...newBooks); 
        }
        checkOut(book: LibraryBook) { 
            book.available = false; 
        }
        checkIn(book: LibraryBook) { 
            book.available = true; 
        }
        printBooks() {
            for (var book of this.books) {
                let {title, isbn} = book;
                console.log(`Title: "${title}", ISBN: ${isbn}`);
            }
        }
    }
    
    var bookA = new LibraryBook('Gödel, Escher, Bach: an Eternal Golden Braid', 9780465026562);
    var bookB = new LibraryBook('Structure and Interpretation of Computer Programs', 9780262510875);
    var library = new Library();
    library.addBooks(bookA, bookB);
    library.printBooks();
    library.checkOut(bookA);
    library.checkIn(bookA);

At the bottom, we include some code to test out our library app. Next, compile the code with, `tsc intro.ts --target ES5` (we specify the output to be ES5 since we’ve used ES6 features), and run `index.html` in a browser. Make sure to open the JavaScript console! You should see the following output:

![Introduction to TypeScript - Console Output](https://res.cloudinary.com/dukp6c7f7/image/upload/f_auto,fl_lossy,q_auto/s3-ghost/2016/01/Introduction-to-TypeScript-Console-Output.png)


Success! Definitely play around with creating new books, adding them to the library, and checking them out in the console – you’ll see that our app functions normally in JavaScript.

Out of interest, see what happens when you have a type error in your code, for example, if you accidentally swapped the two arguments for the `LibraryBook` constructor.

## Step 3: Configure TypeScript using tsconfig

TypeScript programs are configured using a file called *tsconfig.json*. Adding `tsconfig.json` to  your project folder marks that folder as the root directory of our TypeScript project. In this file, we can specify compiler options to compile our `.ts` files as well as root files for our project. For example, we can specify the target JavaScript standard for the compiler:


    {
      "compilerOptions": {
        "target": "ES5"
      }
    }

From now on, whenever we run the `tsc` command, the compiler will check this file first for special instructions and then proceed with compilation based on those instructions. It’s important to know that to make use of `tsconfig.json`, we do not specify any file inputs to `tsc`. To compile `intro.ts` once again under this new configuration simply run the command `tsc` in your terminal.

There’s a much easier way to initialize a TypeScript project and create its `tsconfig.json` file. We can use a handy shortcut. Let’s go ahead and delete the `tsconfig.json` file that we created and then run the following initialization command:


    tsc --init

The output of running this command is a newly created `tsconfig.json` file that is packed with a lot of default options to configure our TypeScript project compiler - most of them are not enabled by default. The configuration options are accompanied by comments that explain what each one configures in our compiler!

The best part of this new `tsconfig.json` is definitely how well documented the options are - they are pretty self-explanatory! You don’t have to use all of these options though. Check out the tsconfig file that was generated.

## Step 4: Get familiar with the WebStorm IDE

There are many different IDEs that support TypeScript (and JavaScript) development. One of them is WebStorm. It is installed in the lab and you can get a free student license to install it on your own computer.

Start WebStorm and open your Library project with it. Open the TypeScript file (intro.ts). Observe that WebStorm will offer to automatically compile the TypeScript. (Click “yes”).

![](https://d2mxuefqeaa7sj.cloudfront.net/s_CA153E515301889FEEAD687CCF8CD6AC319987F909919E3F7EB23FC19687DC87_1533239113388_image.png)


Also observe how the IDE supports you with additional information, such as the names of the parameters in the constructor call for LibraryBook:

![](https://d2mxuefqeaa7sj.cloudfront.net/s_CA153E515301889FEEAD687CCF8CD6AC319987F909919E3F7EB23FC19687DC87_1533241867963_image.png)


Let’s make a change to our app that would trigger a compiler error. For example, change the type of the second parameter of a LibraryBook constructor call to a string.
You will see that the code is compiled instantly by WebStorm and the error is shown in the Errors tab.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_CA153E515301889FEEAD687CCF8CD6AC319987F909919E3F7EB23FC19687DC87_1533242060890_image.png)



![](https://d2mxuefqeaa7sj.cloudfront.net/s_CA153E515301889FEEAD687CCF8CD6AC319987F909919E3F7EB23FC19687DC87_1533246770220_image.png)


Putting TypeScript sources and JavaScript target files in the same directory is not a good idea in terms of project structure. We can go ahead and create a better structure in our project folder. Let’s create *src* and *build* folders and put the files accordingly. We need to update the tsconfig file to reflect this structure.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_CA153E515301889FEEAD687CCF8CD6AC319987F909919E3F7EB23FC19687DC87_1533246987298_image.png)




**Debugging TypeScript**
WebStorm can be used for debugging TypeScript. For this purpose, we need to configure the TypeScript compiler to emit a map of the compiled TypeScript code, so that we can set breakpoints in the TypeScript code. This is done by setting the *sourceMap* and *inlineSource* options in the tsconfig file.




![](https://d2mxuefqeaa7sj.cloudfront.net/s_CA153E515301889FEEAD687CCF8CD6AC319987F909919E3F7EB23FC19687DC87_1533247044140_image.png)


No we can create a “run configuration” to run and test our TypeScript code with Webstorm. Set the *build* directory as the working directory and our target JavaScript file as the “JavaScript file”. Also tell WebStorm to make sure to compile the TypeScript prior to running the code. 




![](https://d2mxuefqeaa7sj.cloudfront.net/s_CA153E515301889FEEAD687CCF8CD6AC319987F909919E3F7EB23FC19687DC87_1533247199286_image.png)


We can now set breakpoints and then run the WebStorm debugger to debug our TypeScript.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_CA153E515301889FEEAD687CCF8CD6AC319987F909919E3F7EB23FC19687DC87_1533247281019_image.png)


See the [WebStorm documentation](https://www.jetbrains.com/help/webstorm/running-and-debugging-typescript.html) for more information on the debugger. Go ahead and experiment and learn on your own.


## Summary

We have explored our first TypeScript project, some of the differences to JavaScript and an IDE for TypeScript development.

