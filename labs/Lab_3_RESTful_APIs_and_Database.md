# Lab 3: RESTful APIs and Database
In the last lab, we learned how to set up a server-side Web application with Express and Node. We *could* build our entire application using server-side programming. However, today’s modern Web apps use a fair amount of client side code (code that is directly running in the user’s browser) in order to provide a reactive and dynamic user experience. The client-side code interfaces with the server-side code by using REST interfaces. We will look at this aspect in the current lab.

**What is REST?**
[REST](https://www.codementor.io/restful/tutorial/rest-api-design-best-practices-strategy) is an acronym for Representational State Transfer. It is web standards architecture and HTTP Protocol. 
RESTful applications use HTTP requests to perform four operations termed as *CRUD (C: create, R: read, U: update, and* *D: delete**)*. Create and/or update is used to post data, get for reading/listing data, and delete to remove data.
RESTful is composed of methods such as; base URL, URL, media types, etc.


## Step 1: Build a first Web API

We will use the example of a simple Web-API to manage data about heroes. You will recall from the last lab that HTTP routes were defined in the “routes” directory of our application. Go ahead and create a new (TypeScript) file “*heroRouter*” in that directory with the following content: 


    import {Router, Request, Response, NextFunction} from 'express';
    const Heroes = require('../../dist/data.json');
    export class HeroRouter {
        public static create(router: Router) {
            //log
            console.log("[HeroRoute::create] Creating HeroRoutes route.");
    
            //add home page route
            router.get("/api/heroes", (req: Request, res: Response, next: NextFunction) => {
                new HeroRouter().getAll(req, res, next);
            });
        }
    
        constructor() {
            // not much here yet
        }
    
        /**
         * GET all Heroes.
         */
        public getAll(req: Request, res: Response, next: NextFunction) {
            res.send(Heroes);
        }
    
    
    }

As you see, this router class is quite similar to the *IndexRouter* we created in Lab 2. Since we are defining a REST API here, we do not need to render HTML content. Therefore, we do not need to extend the *BaseRoute* superclass. 

In line 9, we register a *get* http method (*Read* in terms of CRUD) under URI /api/heroes.

The anonymous handler function delegates to *getAll* method, which simply returns the value of the *Heroes* constant. For a full-fledged app, we would want to pull the data from **a database**. However, for now, we simply read the data from a JSON file in the *dist* folder. Of course, you will need to create this file. (The Webstorm IDE will actually offer to create it. Go ahead and allow that - or create it using the project browser.) You can copy the data for the file from here:


    /* Modify the following according to the format standard given here: https://en.wikipedia.org/wiki/JSON to remove errors if generated */ 
    [
      { id: 11, name: 'Mr. Nice' },
      { id: 12, name: 'Narco' },
      { id: 13, name: 'Bombasto' },
      { id: 14, name: 'Celeritas' },
      { id: 15, name: 'Magneta' },
      { id: 16, name: 'RubberMan' },
      { id: 17, name: 'Dynama' },
      { id: 18, name: 'Dr IQ' },
      { id: 19, name: 'Magma' },
      { id: 20, name: 'Tornado' }
    ]; //need to make a very simple change to close this file

Now that we have a new router class, we need to modify our *Server* class to use it. Open the *app.ts* file to do so. We first need to import the new class:


    import { HeroRouter } from "./routes/heroRouter";

Then we need to create and register the new router. Add the following line to the *routes* method after the creation of the *IndexRoute*:

    HeroRouter.create(router);


![](https://d2mxuefqeaa7sj.cloudfront.net/s_0F08A98126072E53BA5A8D9169872740612450B23C8C2286712746932C144BC6_1534270351498_image.png)


Your router method should now look like the one on the right. If everything went according to plan, you should now be able to start up your Web server and navigate to http://localhost:3000/api/heroes to get the JSON data returned.




## Step 2: Test the REST API

While using a browser to test the simple API (get) function created above is possible, we would want a more powerful tool for more complex Web APIs and for test automation. We could use unit testing to do this programmatically (with frameworks such as [Mocha](https://mochajs.org) and [Chai](http://www.chaijs.com)). However, to avoid the complexity of learning yet another framework in this lab, we will use an App called [*Postman*](https://www.getpostman.com). (Feel free to explore unit testing frameworks on your own in your project.) The free version of Postman is installed in the lab and you can also download it on your computer. Below is a screenshot of Postman testing the above API function. As you can see, tests can be scripted in JavaScript. Go ahead and explore Postman on your own for testing the above API function. 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_0F08A98126072E53BA5A8D9169872740612450B23C8C2286712746932C144BC6_1534272420125_image.png)



## Step 3: Create more API endpoints

Our API has only one endpoint so far. Let’s create a second one. The creation of each additional endpoint requires the following three steps:


1. Create a method on `HeroRouter` that takes the arguments of your typical Express request handler: `request`, `response`, and `next`.
2. Implement the server’s response for the endpoint in this method.
3. Inside of `create`, register the method as a handler for the desired HTTP method (get/post/…) and the desired endpoint URL.

So, let’s create an endpoint to get a single hero. We can implement this in a method *getOne*, as shown below:


    /**
     * GET one hero by id
     */
    public getOne(req: Request, res: Response, next: NextFunction) {
        let query = parseInt(req.params.id);
        let hero = Heroes.find(hero => hero.id === query);
        if (hero) {
            res.status(200)
                .send({
                    message: 'Success',
                    status: res.status,
                    hero
                });
        }
        else {
            res.status(404)
                .send({
                    message: 'No hero found with the given id.',
                    status: res.status
                });
        }
    }

Note that the above method extracts the “id” parameter into a variable “query” and then uses that variable to find the hero with the right id (if such a hero exists).

Now we just need to register the additional endpoint in the static *create* method (added lines are 10-13):


    public static create(router: Router) {
        //log
        console.log("[HeroRoute::create] Creating HeroRoutes route.");
    
        //add getAll route
        router.get("/api/heroes", (req: Request, res: Response, next: NextFunction) => {
            new HeroRouter().getAll(req, res, next);
        });
    
        // add getOne route
        router.get("/api/heroes/:id", (req: Request, res: Response, next: NextFunction) => {
            new HeroRouter().getOne(req, res, next);
        });
    }

Go ahead and try the new endpoint. Hero id 2 should return Spiderman, for example. Use Postman again to write a test script.

You should now be able to add more endpoints to the API using the same steps.

## Step 4: Creating a database

So far we have only created R (Read) endpoints. The other types of CRUD functions (create, update, delete) would require us to change the persistent data. At this point, it makes sense to connect to a database rather than reading the data from a file.

Different types of databases may be used (relational and non-relational). Since CSC 370 is not a prerequisite for this course, we will use MongoDB (a non-relational database) so that we do not have to require SQL knowledge.

[MongoDB](https://www.mongodb.com) should be installed in your lab. You can also install it in your own computer. You will need a config file prior to starting the database server. The default config file on the instructor’s machine is in /usr/local/etc/mongod.conf - but you can put it anywhere. 
(Use **which mongod** or **locate mongod** in your terminal to find the exact path. The latter displays all files with extension including .conf if exists). Here is its contents:


    systemLog:
      destination: file
      path: /usr/local/var/log/mongodb/mongo.log
      logAppend: true
    storage:
      dbPath: /usr/local/var/mongodb
    net:
      bindIp: 127.0.0.1

Start the MongoDB server with `mongod --config /usr/local/etc/mongod.conf`

Now you can start the mongo command line shell with the `mongo` command (see comment on the right in order to implement user access privileges against default path access security restrictions. It is recommended to create .conf under node_modules within WebStorm after you install packages from Step 5. See next before you continue). From there, we will create a database “heroes” and insert the data from our data.json file:


    > use myapp; 
    switched to db myapp
    > heroes = /* copy the data from the JSON file here and add a semicolon */
    > db.heroes.insert(heroes); 
    BulkWriteResult({
    "writeErrors" : [ ],
    "writeConcernErrors" : [ ],
    "nInserted" : 5,
    "nUpserted" : 0,
    "nMatched" : 0,
    "nModified" : 0,
    "nRemoved" : 0,
    "upserted" : [ ]
    })

We first switch to a database called “myapp” (which will be newly created if not existent) (line 1). We then assign our test data to a variable heroes (line 3). We then insert that data into a new collection called “heroes” (line 4).

You can verify that the data is indeed stored by querying one record, for example with:
`db.heroes.findOne();` We will not discuss the mongoshell commands further. Explore [online references](https://docs.mongodb.com/manual/reference/mongo-shell/) as needed.


## Step 5 (retroactive to Step 4): Connecting to the Database

We will now connect to the database from within our Node Web application. 
Make sure the mongodb drivers for Node and their type definitions are installed:

`npm install mongodb`

`npm install @types/mongodb`

If you have done the previous step(s) properly, you now should have no issues in exploring your coding options and add layers to your server, such as the DB layer to perform “CRUD.” The CR have been fulfilled and now, UD need to be implemented.  

**Creating a DbClient class for connecting to MongoDB**
In order to avoid connecting every time to MongoDB before querying a database, we are going to store the opened connection in the singletDbClion object. Let’s create a new file **DbClient.ts** and save it in the **src** folder. The singleton class will look like this:


    import { MongoClient, Db } from "mongodb";
    
    class DbClient {
        public db: Db;
    
        public connect() { /* ... */ }
    }
    
    export = new DbClient();

In the first line, we imported **MongoClient** and **Db** types from mongodb package. The DbClient class contains a single method **connect()** where we will connect to the MongoDB database and then save the connection as a class member. In the last line, we export a new instance of the DbClient class. That instance will be returned every time when we use/load the DbClient by calling
 `import DbClient = require(“../common/DbClient”);`

**A word about the Node architecture**
Before implementing the method **connect()**, we need to discuss an important aspect of the Node.js architecture, namely the fact that it is **single-threaded**. This is very different from more traditional Web application servers, which are **multi-threaded**. In traditional (multi-threaded) architectures, components can use synchronized communication, since “waiting” for a response does not block the progress of other components (which run in other threads). In a single-threaded architecture (like Node) however, components need to communicate asynchronously, since any “waiting” would block the progress of other components. You can read about these architectures in more detail [here](https://www.journaldev.com/7462/node-js-architecture-single-threaded-event-loop).

******Back to implementing the connect() method.**
Keeping in mind the fact that the Node.js programming model is asynchronous, we can now discuss how to implement the **connect()** method. Multiple different alternatives can be used.

**Alternative 1 - the callback approach**
The MongoClient allows you to pass a callback function as the last argument which would be called when the connection is established or when an error occurs.


    MongoClient.connect("mongodb://localhost:27017", (err, client) => {
         if(err) {
             console.log(err);
         } else {
             this.db = client.db("myapp");
         } 
     });

**Alternative 2 - the promise approach**
The second approach is to use a *Promise* object. A [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) is an object representing the eventual completion or failure of an asynchronous operation. (You can read more about the Promise class [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises) and elsewhere on the Web.) If you skip passing a callback function to MongoClient’s connect function, MongoClient will return a new Promise (which can be consumed with *.then* and *.catch*.


    return MongoClient.connect("mongodb://localhost:27017/myapp")
        .then(client => {
            this.db = client.db("myapp");
        })
        .catch(err => {
            console.log(err);
        });

  
**Alternative 3 - the async/await approach**
You may also use [**async/await**](https://basarat.gitbooks.io/typescript/docs/async-await.html) [approach](https://basarat.gitbooks.io/typescript/docs/async-await.html). (This is the one we will be using, as it arguably leads to the cleanest code.) Take some time to read about [async/wait here](https://tutorialedge.net/typescript/async-await-in-typescript-tutorial/)!


    try {
        let client = await MongoClient.connect("mongodb://localhost:27017");
        this.db = client.db("myapp");
        console.log("Connected to db");
        return this.db;
    } catch (error) {
        console.log("Unable to connect to db");
    }

If you have read the above-linked description of async/wait, you will recall that the *await* keyword can only be used in *async* functions. We will therefore have to declare our **connect()** method as an async function. The final DbClient class is below:

![](https://d2mxuefqeaa7sj.cloudfront.net/s_0F08A98126072E53BA5A8D9169872740612450B23C8C2286712746932C144BC6_1534292348392_image.png)


You may wonder about the exclamation mark in the definition of the private *db* member. It is a type assertion that tells the TypeScript compiler that we assert that the db field will be initialized to a value. Without the exclamation mark, the TypeScript compiler will (rightfully) complain that the db field may not be initialized:

![](https://d2mxuefqeaa7sj.cloudfront.net/s_0F08A98126072E53BA5A8D9169872740612450B23C8C2286712746932C144BC6_1534292577061_image.png)


With the exclamation mark, we assert that it will be initialized. You can read more about this assertion in the [TypeScript documentation on the Web](https://stackoverflow.com/questions/42273853/in-typescript-what-is-the-exclamation-mark-bang-operator-when-dereferenci). 

## Step 6: Using the DbClient

Let’s now use the DBClient class in our RESTful API. Let’s change the *getAll* method in the *HeroRouter* class to read heroes from the database instead of from a file. We start by importing the DbClient singleton:

`import DbClient = require("../DbClient");`

Now we can use it in the implementation of *getAll:*


    /**
     * GET all Heroes.
     */
    public getAll(req: Request, res: Response, next: NextFunction) {
        DbClient.connect()
            .then((db: any) => {
                return db!.collection("heroes").find().toArray();
                })
            .then((heroes:any) => {
                console.log(heroes);
                res.send(heroes);
                })
            .catch((err: any) => {
            console.log("err.message");
                })
    }

Again, remember that we declared the *connect()* method as an `async` method, which means that it returns a Promise. We use the `.then` operator to specify the function that should be executed when the Promise is fulfilled. In that function (line 7) we tell the database to find all items in the *heroes* collection. Calling this MongoClient operation again returns a promise. The second .`then` operator specifies a function to be executed when that second promise is fulfilled. In that function (line 10-11) we write the db result to the console and send it back as a response. Finally, the catch clause (line 13) catches any errors during resolution of the promises.

*Note: if this is still confusing to you, please read up on Promises and async methods. This style of event driven programming is quite important in some software architectures (including Node.js.)*

If everything went according to plan, you should now be able to (re)start your Web application and use a Web browser or postman to check whether the *getAll* endpoint (with database access) works. (It should return the same JSON, but this time pulled from the database.)


## Step 7: Change the implementation of the second endpoint

Let’s now change the implementation of our second endpoint (getOne) to use the database. This part of the lab is not scripted. You will need to find the right MongoClient API functions for the query yourself. Otherwise, the implementation should be similar to *getAll*.


## Summary

We learned how to set up a REST API with Express and TypeScript. We explored the Postman Web API testing tool. We learned about MongoDB and its integration with Node. We also learned an important fact about the Node architecture, namely that it is single-threaded. This requires that communication among different Node components should be asynchronous in order to avoid that “wait” times stall the Node server. We learned about Promises and async functions in TypeScript. There are obviously many more things that should be done, such as defining a password / login for database access, etc. Go ahead and learn and explore these things on your own. 

