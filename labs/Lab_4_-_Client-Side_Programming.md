# Lab 4 - Client-Side Programming
In the previous labs, we learned about how to build a server-side Web-application with Express, Node, Pug, and MongoDB. We could build-out our application completely with these server side technologies. However, today’s apps use a fair amount of *client-side programming* to be reactive and dynamic. Therefore, we will look at client side programming in this lab. There are many different frameworks for client-side programming. In particular, React and Angular are popular choices in the JavaScript world. We will look at the latter, as it is particularly suitable for TypeScript development. (Angular is itself written in TypeScript.)

We will be using the Tour of Heroes tutorial of the Angular web site.

## Step 1: Read the [introduction](https://angular.io/tutorial) of the *Tour of Heroes* tutorial. 
## Step 2: Follow the [Application Shell](https://angular.io/tutorial/toh-pt0) part of the tutorial.
- **Note:** WebStorm is an excellent IDE for Angular applications. You can perform many of the tasks in the tutorial, also directly from Webstorm. 
- Carry out the tutorial tasks *after* the installation and project generation tasks. (*Please really do carry out the tasks. Hands on learning works much better than just reading along.*)
- The command npm install -g @angular/cli for installing the relevant packages in your project within WebStorm could generate many errors. Instead, try without the -g option. You will only get a few warnings rather than errors. The next command might not enable you to run “angular tour of heroes” since Node.js need to be updated from to v8.9+. This is done via this command: npm install npm@latest —save for updating node (then run npm -v and node -v to see if the version is updated), or this one (user access privileges need to be enabled or on your machine run as a sudoer) for a fresh installation: first try installing the curl python software features via  sudo apt-get install curl python-software-properties  then try curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
- Next install is the dependent packages via sudo apt-get install -y nodejs or sudo apt-get install nodejs
- You might receive the error “Command ng not found” when you try ng new angular-tour-of-heroes. To resolve this problem, we need to define and specify ng by going to the node_modules directory in your project and find the right path where ng.js is installed. Copy-paste the path like the example below as I tried on my machine (philip is my name, yours is your name with the given pat installed  ;)):  alias ng=”/home/philip/WebstormProjects/ClientSide/node_modules/@angular/cli/bin/ng”
- Now you can execute the command ng new angular-tour-of-heroes  in WebStorm terminal and choose the desirable option (stylesheet) suggested in your terminal to generate your routing module (this substep and the next substep such as compiling angular components to serve the webpage on port 4200 could take several minutes).
- For other substeps continue reading Application Shell (current step). 
## Step 3: Follow the [Hero Editor](https://angular.io/tutorial/toh-pt1) part of the tutorial
- Note: the part of the tutorial about “importing the missing *FormsModule*” may not need to be carried out, since the latest *ng* application generator appears to automatically import it.
- To edit and update your heroes component, you need to access the .ts file(s) as described in the editor. The .ts and .html component files can be found in the heroes folder under app folder which is under src folder in the angular-tour-of-heroes directory.  
- Another important point when generating your angular components, you might get tsconfig.json error file not found! When this happen enforce the project name and include it into the json file. Here is an example (my project name is ClientSide. So change it to your project name): 
    {
      "compileOnSave": false,
      "compilerOptions": {
        "baseUrl": "./",
        "outDir": "./dist/out-tsc",
        "sourceMap": true,
        "declaration": false,
        "module": "es2015",
        "moduleResolution": "node",
        "emitDecoratorMetadata": true,
        "experimentalDecorators": true,
        "target": "es5",
        "typeRoots": [
          "node_modules/@types"
        ],
        "lib": [
          "es2018",
          "dom"
        ],
        "include": ["ClientSide/**/*"]
      }
    }
## Step 4: Follow the [Displaying a Heroes List](https://angular.io/tutorial/toh-pt2) part of the tutorial
- Note that the ./hero typescript error will be rectified when you actually create the hero class in the relevant directory. So skip to later sections of the webpage on this step and create it. 
- Another point is when asked to find the component class the extension is displayed as .scss. WebStorm will ask “Enable FileWatcher to compile SCSS to CSS?” Select Yes. The example is finding heroes.component.css and in your directory it is initially displayed as heroes.component.scss.
## Step 5: Follow the [Master/Detail Components](https://angular.io/tutorial/toh-pt3) part of the tutorial
## Step 6: Follow the [Services](https://angular.io/tutorial/toh-pt4) part of the tutorial
## Step 7: Follow the [Routing](https://angular.io/tutorial/toh-pt5) part of the tutorial
## Step 8: Follow the [HTTP](https://angular.io/tutorial/toh-pt6) part of the tutorial
## Step 9: Connect to a real backend server

In the Tour of Heroes tutorial, you used an in-memory API server for HTTP requests. In this last step, attempt to connect directly to a real HTTP server, namely the backend AP you developed in previous labs. 

Detaching the (fake) in-memory HTTP server is as simfple as commenting out the import of the HttpClientInMemoryWebApiModule in the @NgModule declaration in app.module.ts:

![](https://d2mxuefqeaa7sj.cloudfront.net/s_193FDF11814237EA74040A9F032F09F8B28CD63696818BF08EA74D32383F591F_1534376798456_image.png)


You will also need to let the HeroService know where the real Web API will be located. 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_193FDF11814237EA74040A9F032F09F8B28CD63696818BF08EA74D32383F591F_1534376915747_image.png)


When you run the app, you will likely get an error message.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_193FDF11814237EA74040A9F032F09F8B28CD63696818BF08EA74D32383F591F_1534377188907_image.png)


Opening the developer tools on the Web browser will provide you with further details:

![](https://d2mxuefqeaa7sj.cloudfront.net/s_193FDF11814237EA74040A9F032F09F8B28CD63696818BF08EA74D32383F591F_1534377261752_image.png)


There is an access control violation. The reason for this is that the Express router applies by default the “same-origin” access policy, which checks that accesses to the API come from the same URL. Your Express application is served on localhost:3000 while your Angular app runs on localhost:4200. 

One way to resolve this problem would be to actually serve your Angular app through Express/Node. This would require some refactoring of your project structures and is complicated. Another approach would be to keep your (Angular) client and your (Express) server as separate projects, but configure the server to allow access from the system that serves the Angular app. This solution is often cleaner. To do so, you need to allow [Cross-Origin Resource Sharing (CORS)](https://www.codecademy.com/articles/what-is-cors).

Install the CORS module in your *server* project:

    $ npm install cors
    $ npm install @types/cors

 Then change your *Sever* class to configure and load the CORS middleware (your file *app.ts* in your *src* directory, server project.)
 
 Add the following import and define the configuration options map as follows:
 

    import cors from 'cors';
    
    const options:cors.CorsOptions = {
        allowedHeaders: ["Origin", "X-Requested-With", "Content-Type", "Accept", "X-Access-Token"],
        credentials: true,
        methods: "GET,HEAD,OPTIONS,PUT,PATCH,POST,DELETE",
        origin: "http://localhost:4200",
        preflightContinue: false
    };

As you see above, we configure our options to allow access to all HTTP methods from localhost:4200.

Finally, we need to tell the router to use the CORS middleware with our configuration options (see added, highlighted part below):


    private routes() {
        let router: express.Router;
        router = express.Router();
        router.use(cors(options));
    
        IndexRoute.create(router);
        HeroRouter.create(router);
    
        //use router middleware
        this.app.use(router);
    
    }

Now, if you start your server code (Express) and your Angular client code, you should indeed get your data from the server HTTP API. (If everything went according to plan.)

Go ahead and experiment and learn further. You have now had an introduction to all major building blocks for your course project.

