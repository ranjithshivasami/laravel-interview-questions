# laravel-interview-questions


1. ### What are the main features of Laravel?

    Some of the main features of Laravel are:

   * Eloquent ORM
   * Query builder
   * Reverse Routing
   * Restful Controllers
   * Migrations
   * Database Seeding
   * Unit Testing
   * Homestead

2. ### What do you understand by Eloquent ORM?
   **Eloquent ORM (Object-Relational Mapping)** is one of the main features of the Laravel framework. It may be defined as an advanced PHP implementation of the active record pattern.

    *Active record pattern is an architectural pattern which is found in software. It is responsible for keeping in-memory object data in relational databases*

    Eloquent ORM is also responsible for providing the internal methods at the same time when enforcing constraints on the relationship between database objects. Eloquent ORM represents database tables as classes, with their object instances tied to single table rows, while following the active record pattern.

3. ### What is Query Builder in Laravel?
   Laravel's Query Builder provides more direct access to the database, alternative to the Eloquent ORM. It doesn't require SQL queries to be written directly. Instead, it offers a set of classes and methods which are capable of building queries programmatically. It also allows specific caching of the results of the executed queries.

4. ### Write down the name of some aggregates methods provided by the Laravel's query builder.

    Some of the methods that Query Builder provides are:

    * count()
    * max()
    * min()
    * avg()
    * sum()

5. ### What is routing?

    All Laravel routes are defined in route files, which are stored in the routes directory. These files are loaded by the MVC framework. The routes/web.php files define routes that are available for the web interface. Those routes are allotted as the web middleware group, which provide features such as **session state** and **CSRF** protection. The routes available in **routes/api.php** are stateless and are allotted as the API middleware group. For most of the applications, one should start by defining routes in routes/web.php file.

6. ### What do you understand by Reverse routing?

    Reverse routing in Laravel is used to generate the URL based on name or symbol. It defines a relationship between the links and, Laravel routes, and it is possible to make later changes to the routes to be automatically propagated into relevant links. When the links are generated using names of existing routes, the appropriate uniform resource identifiers (URIs) are automatically generated by Laravel. Reverse routing provides flexibility to the application and helps the developer to write cleaner codes.

    Route Declaration:
    
    ```
    Route::get('login', 'users@login');  
    Route::get('login', 'users@login');  
    ```
    A link can be created to it using reverse routing, which can be further transferred in any parameter that we have defined. If optional parameters are not supplied, they are removed automatically from the generated links

    ```
    {{ HTML::link_to_action('users@login') }}  
    {{ HTML::link_to_action('users@login') }}  
    ```
    By using it, a URL like https://abc.go.com/loginwill be created automatically.

7. ### How will you describe Bundles in Laravel?

    In Laravel, Bundles are also known as **Packages**. Packages are the primary way to add more functionality to Laravel. Packages can be anything, from a great way to work with dates like Carbon, or an entire BDD testing framework like **Behat**. Laravel also provides support for creating custom packages.

    There are different types of packages. Some of them are stand-alone packages. This means they can work with any PHP framework. The frameworks like **Carbon and Behat** are examples of stand-alone packages. Other packages are intended for use with Laravel. These packages may contain routes, controllers, views, and configurations which are mainly designed to enhance a Laravel application.
8. ###  What is a composer, and how can we install Laravel by the composer?

    A composer is a dependency manager in PHP. It manages the dependencies which are required for a project. It means that the composer will pull in all the necessary libraries, dependencies, and manage all at a single place.

    ```
    composer create-project laravel/laravel example-app 

    cd example-app   

    php artisan serve
    ```
9. ###  Does Laravel support caching?
    Yes, Laravel provides support for popular caching backends like **Memcached** and **Redis**.

    By default, Laravel is configured to use file cache driver, which is used to store the serialized or cached objects in the file system. For huge projects, it is suggested to use **Memcached** or **Redis**.
    ### Video link
    [<img src="https://i.ytimg.com/vi/djYRQtfRSH8/maxresdefault.jpg" width="170" height="100">](https://www.youtube.com/watch?v=djYRQtfRSH8&list=PLreYfy6R-5ckUjeS-nld1JDSEqCy-htt0&index=1)

10. ### How to clear cache in Laravel?

    **1. Clearing Configuration Cache**

    However, if you notice changes to the configuration values in .env file is not reflecting on your application, you may want to consider clearing the configuration cache with the following command:

    ```
    $ php artisan config:clear
    Configuration cache cleared!
    ```

    If you want to quickly reset your configuration cache after clearing them, you may instead run the following command:

    ```
    $ php artisan config:cache
    Configuration cache cleared!
    Configuration cached successfully!
    ```
    Caching your configuration will also help clear the current configuration cache. So it helps save your time without having to run both commands.

    **2. Route Caching**

    Caching your routes will drastically decrease the amount of time it takes to register all of your application's routes. When you add a new route, you will have to clear your route cache for the new route to take effect.

    **Clearing Route Cache**

    The following command will clear all route cache in your application:

    ```
    $ php artisan route:clear
    Route cache cleared!
    ```
    To cache your routes again, simply run the following command:

    ```$ php artisan route:cache
    Route cache cleared!
    Routes cached successfully!
    ```
    Again, running the above command alone is enough to clear your previous route cache and rebuild a new one.

    **3. Views Caching**

    Views are cached into compiled views to increase performance when a request is made. By default, Laravel will determine if the uncompiled view has been modified more recently than the compiled view, before deciding if it should recompile the view.

    **Clearing View Cache**

    However, if for some reason your views are not reflecting recent changes, you may run the following command to clear all compiled views cache:

    ```
    $ php artisan view:clear
    Compiled views cleared!
    ```
    In addition, Laravel also provides an Artisan command to precompile all of the views utilized by your application. Similarly, the command also clears the view cache before recompiling a new set of views:

    ```
    $ php artisan view:cache
    Compiled views cleared!
    Blade templates cached successfully!
    ```
    **4. Events Cache**

    If you are using Events in your Laravel application, it is recommended to cache your Events, as you likely do not want the framework to scan all of your listeners on every request.

    **Clearing Events Cache**
    When you want to clear your cached Events, you may run the following Artisan command:
    ```
    $ php artisan event:clear
    Cached events cleared!
    ```
    Likewise, caching your Events also clear any existing cache in the framework before a new cache is rebuilt:

    ```
    $ php artisan event:cache
    Cached events cleared!
    Events cached successfully!
    ```
    **5. Application Cache**

    Using Laravel's Cache is a great way to speed up frequently accessed data in your application. While developing your application involving cache, it is important to know how to flush all cache correctly to test if your cache is working properly.

    **Clearing Application Cache**

    To clear your application cache, you may run the following Artisan command:

    ```
    $ php artisan cache:clear
    Application cache cleared!
    ```
    **6. Clearing All Cache**

    Laravel provides a handy Artisan command that helps clear ALL the above caches that we have covered above. It is a convenient way to reset all cache in your application, without having to run multiple commands introduced before.

    To clear all Laravel's cache, just run the following command:

    ```
    $ php artisan optimize:clear
    Compiled views cleared!
    Application cache cleared!
    Route cache cleared!
    Configuration cache cleared!
    Compiled services and packages files removed!
    Caches cleared successfully!
    ```

11. ### How will you explain middleware in Laravel?
    As the name suggests, middleware works as a middleman between request and response. Middleware is a form of HTTP requests filtering mechanism. For example, Laravel consists of middleware which verifies whether the user of the application is authenticated or not. If a user is authenticated and trying to access the dashboard then, the middleware will redirect that user to home page; otherwise, a user will be redirected to the login page.

    There are two types of middleware available in Laravel:

    **Global Middleware**

    It will run on every HTTP request of the application.

    **Route Middleware**

    It will be assigned to a specific route.

    **Syntax**
    ```
    php artisan make:middlewareMiddelwareName      
    ```
    **Example**
    ```
    php artisan make:middlewareUserMiddleware      
    ```

    Now, UserMiddleware.php file will be created in app/Http/Middleware.

    ![UserMiddleware](./images/laravel-middlwware.png)
12. ###  What do you understand by database migrations in Laravel? How can we use it?

    Migrations can be defined as version control for the database, which allows us to modify and share the application's database schema easily. Migrations are commonly paired with **Laravel's schema builder** to build the application's database schema easily.

    A migration file includes two methods, **up()** and** down()**. A method up() is used to add new tables, columns or indexes database and the down() method is used to reverse the operations performed by the up() method.

    We can generate a migration and its file by using the **make:migration.**

    ```
    php artisan make:migration blog  
    ```
    By using it, a current date blog.php file will be created in database/migrations.

13. ### What do you know about Service providers in Laravel?

    Service providers can be defined as the central place to configure all the entire Laravel applications. Applications, as well as Laravel's core services, are bootstrapped via service providers. These are powerful tools for maintaining class dependencies and performing dependency injection. Service providers also instruct Laravel to bind various components into the Laravel's Service Container.

    An artisan command is given here which can be used to generate a service provider:

    ```
    php artisan make: provider ClientsServiceProvider 
    ```

    Almost, all the service providers extend the Illuminate\Support\ServiceProviderclass. Most of the service providers contain below-listed functions in its file:
     * Register() Function
     * Boot() Function

    Within the Register() method, one should only bind things into the service container. One should never attempt to register any event listeners, routes, or any other piece of functionality within the Register() method.
    
    ### video link
    [<img src="https://i.ytimg.com/vi/VYPfncvYW-Y/maxresdefault.jpg" width="170" height="100">](https://www.youtube.com/watch?v=VYPfncvYW-Y)



14. ### How can we get data between two dates using Query in Laravel?

    We can use **whereBetween()** method to retrieve the data between two dates with Query.

    Example
    ```
    Blog::whereBetween('created_at', [$date1, $date2])->get();  
    ```
15. ### What do you know about CSRF token in Laravel? How can someone turn off CSRF protection for a specific route?

    CSRF protection stands for **Cross-Site Request Forgery** protection. CSRF detects unauthorized attacks on web applications by the unauthorized users of a system. The built-in CSRF plug-in is used to create CSRF tokens so that it can verify all the operations and requests sent by an active authenticated user.

    To turn off CSRF protection for a specific route, we can add that specific URL or Route in $except variable which is present in the app\Http\Middleware\VerifyCsrfToken.phpfile.

    ```
    classVerifyCsrfToken extends BaseVerifier  
    {  
        protected $except = [  
             'Pass here your URL',  
        ];  
    }  
    ```

16. ### List some official packages provided by Laravel?

    There are some official packages provided by Laravel which are given below:

    **Cashier**

    Laravel cashier implements an expressive, fluent interface to Stripe's and Braintree's subscription billing services. It controls almost all of the boilerplate subscription billing code you are dreading writing. Moreover, the cashier can also control coupons, subscription quantities, swapping subscription, cancellation grace periods, and even generate invoice PDFs.

    **Envoy**

    Laravel Envoy is responsible for providing a clean, minimal syntax for defining frequent tasks that we run on our remote servers. Using Blade style syntax, one can quickly arrange tasks for deployment, Artisan commands, and more. Envoy only provides support for Mac and Linux.

    **Passport**

    Laravel is used to create API authentication to act as a breeze with the help of Laravel passport. It further provides a full Oauth2 server implementation for Laravel application in a matter of minutes. Passport is usually assembled on top of League OAuth2 server which is maintained by Alex Bilbie.

    **Scout**

    Laravel Scout is used for providing a simple, driver-based solution for adding full-text search to the eloquent models. Using model observers, Scout automatically keeps search indexes in sync with eloquent records.

    **Socialite**

    Laravel Socialite is used for providing an expressive, fluent interface to OAuth authentication with Facebook, Twitter, Google, and Linkedln, etc. It controls almost all the boilerplate social authentication code that you are dreading writing.

17. ### What do you know about Facades in Laravel? Explain.

    Laravel Facades provide static-like interface classes which are available in the application's service container. Laravel self-ships with several available facades, gives access to almost all features of Laravel. Facades also help to access a service directly from the container itself. It is described in the Illuminate\Support\Facades namespace. Hence, it is easy to use.

    **Example**
    ```
        use Illuminate\Support\Facades\Cache;  

        Route::get('/cache', function () {  
          return Cache::get('PutkeyNameHere');  
        })
    ```
    ### video link

    [<img src="https://i.ytimg.com/vi/zD2VJhOdI5c/maxresdefault.jpg" width="170" height="100">](https://www.youtube.com/watch?v=zD2VJhOdI5c)

18. ### How can we check the Laravel current version?

    One can easily check the current version of Laravel installation using the **-version** option of artisan command.

    ```
    $php artisan -version  
    ```
19. ### How will you explain dd() function in Laravel?

    dd stands for "**Dump and Die**." Laravel's dd() function can be defined as a helper function, which is used to dump a variable's contents to the browser and prevent the further script execution.

20. ### What do you know about PHP artisan? Mention some artisan command.

    PHP artisan is a command-line interface/tool provided with Laravel. It consists of several useful commands which can be helpful while building an application. There are few artisan commands given below:

    **PHP artisan list**

    A 'list' command is used to view a list of all available Artisan commands.

    **PHP artisan help**

    Every command also contains a 'help' screen, which is used to display and describe the command's available arguments and options. To display a help screen, run 'help' command.

    **PHP artisan tinker**

    Laravel's artisan tinker is a repl (Read-Eval-Print Loop). Using tinker, one can write actual PHP code through command-line. One can even update or delete table records in the database.

    **PHP artisan -version**

    By using this command, one can view the current version of Laravel installation.

    **PHP artisan make model model_name**

    This command creates a model 'model_name.php' under the 'app' directory.

    **PHP artisan make controller controller_name**

    This command is used to build a new controller file in app/Http/Controllers folder.

21. ### How will you explain Events in Laravel?

    An event is an activity or occurrence recognized and handled by the program. Events in Laravel provide simple observer implementations which allow us to subscribe and listen for events within our application. The event classes are stored in app/Events, while their listeners are stored in app/Listeners of our application. These can be generated using Artisan console commands. A single event may contain multiple listeners that do not depend on each other.

    There are some events examples in Laravel which are:

    * A new user is registered.
    * A new comment is posted.
    * User login/logout.
    * A new product is added.

22. ### What do you understand by Lumen?

    Lumen is a PHP micro-framework built on Laravel's top components. It is created for building Laravel based micro-services and blazing fast APIs. It is one of the fastest micro-frameworks available. Lumen is not a complete web framework like Laravel and used for creating APIs only. Therefore, most of the components, such as HTTP sessions, cookies, and templating, are excluded from Lumen. Lumen provides support for features such as logging, routing, caching queues, validation, error handling, middleware, dependency injection, controllers, blade templating, command scheduler, database abstraction, the service container, and Eloquent ORM, etc.

    We can install Lumen using composer by running the command given below:

    ```
    composer create-project --prefer-distlaravel/lumen blog  
    ```

22. ### Explain the Service container and its advantages.

    Service container in Laravel is one of the most powerful features. It is an important, powerful tool for resolving class dependencies and performing dependency injection in Laravel. It is also known as **IoC container.**

    Dependency injection is a term which essentially means that class dependencies are "injected" into the class by the constructor or, in some cases," setter" methods.

    **Advantages of Service Container**

    * It can handle class dependencies on object creation.
    * It can combine interfaces to concrete classes.
    * 
    
    ### video link

    [<img src="https://i.ytimg.com/vi/PGVqkEZiUoc/maxresdefault.jpg" width="170" height="100">](https://www.youtube.com/watch?v=PGVqkEZiUoc)

23. ### What do you know about Laravel Contracts?

    Laravel's Contracts are the set of interfaces which are responsible for defining the core functionality of services provided by the Laravel framework.

    ### video link

    [<img src="https://i.ytimg.com/vi/IrIZ7wiWocg/maxresdefault.jpg" width="170" height="100">](https://www.youtube.com/watch?v=IrIZ7wiWocg)

24. ### How will you explain homestead in Laravel?

    Homestead is an official, pre-packaged, vagrant virtual machine which provides Laravel developers all the necessary tools to develop Laravel out of the box. It also includes **Ubuntu, Gulp, Bower**, and other development tools which are useful in developing full-scale web applications. It provides a development environment which can be used without the additional need to install PHP, a web server, or any other server software on the machine.

25. ### How can we get the user's IP address in Laravel?

    We can get the user's IP address using:

    ```
    public function getUserIp(Request $request){  
        // Gettingip address of remote user  
        return $user_ip_address=$request->ip();  
    }  
    ```

26. ### How can we use the custom table in Laravel?
    We can easily use custom table in Laravel by overriding protected $table property of Eloquent. Here, is the sample:

    ```
    class User extends Eloquent{  
        protected $table="my_user_table";  
    }  
    ```
27. ### What is the use of the Eloquent cursor() method in Laravel?

    The cursor method allows us to iterate through our database using a cursor, which will only execute a single query. While processing large amounts of data, the cursor method may be used to reduce your memory usage greatly.

    ```
    foreach (Product::where('name', 'bar')->cursor() as $flight) {  
        //make some stuff  
    }  
    ```
28. ### How will you create a helper file in Laravel?
    We can create a helper file using composer as per the given below steps:

    Make a file "app/helpers.php" within the app folder.

    Add
    ```
    "files": [  
    "app/helpers.php"  
    ]  
    ```
    in the "autoload" variable.

    Now update composer.json with composer dump-autoload or composer update.

29. ###  What is the use of PHP compact function?
    PHP compact function receives each key and tries to search a variable with that same name. If a variable is found, then it builds an associate array.

30. ### Explain some benefits of Laravel over other PHP frameworks.
    There are few benefits of Laravel which can be considered over other PHP frameworks:

    * In Laravel, Setup and customization process is fast and easy as compared to others.
    * Laravel supports multiple file systems.
    * It has pre-loaded packages like **Laravel Socialite, Laravel cashier, Laravel Passport, Laravel elixir, and Laravel Scout**, etc.
    * It consists of in-built Authentication System.
    * It supports Eloquent ORM (Object Relation Mapping) with PHP active record implementation.
    * "Artisan" command-line tool for creating a database structure, code skeleton,  and build their migration.

31. ### Which types of relationships are available in Laravel Eloquent?
    Below are the types of relationships that Laravel Eloquent ORM supports:

    * One to One
    * One to Many
    * One to Many (Inverse)
    * Many to Many
    * Has Many Through
    * Polymorphic Relations
    * Many To Many Polymorphic Relations

32. ### How can we implement a package in Laravel?

    We can implement a package in Laravel by:

    * Creating a package folder and name it.
    * Creating Composer.json file for the package.
    * Loading package through main composer.json and PSR-4.
    * Creating a Service Provider.
    * Creating a Controller for the package.
    * Creating a Routes.php file.

33. ### What do you know about Traits in Laravel?

    PHP Traits is a group of methods which can be included within another class. A Trait cannot be instantiated by itself like an abstract class. Traits are generated to reduce the limitations of single inheritance in PHP. It allows a developer to reuse sets of methods freely in various independent classes living in different class hierarchies.

    ### video link
    ### Traits in php 
    [<img src="https://i.ytimg.com/vi/PMruqUC4Qpc/maxresdefault.jpg" width="170" height="100">](https://www.youtube.com/watch?v=PMruqUC4Qpc)
    
    ### Traits in Laravel: Real Usage Examples
    [<img src="https://i.ytimg.com/vi/6mN0Oj6xR30/maxresdefault.jpg" width="170" height="100">](https://www.youtube.com/watch?v=6mN0Oj6xR30)
    
34. ### How can someone change the default database type in Laravel?

    Laravel is configured to use MySQL by default.

    To change its default database type, edit the file config/database.php:

    * Search for 'default' =>env('DB_CONNECTION', 'mysql')
    * Change it to whatever required like 'default' =>env('DB_CONNECTION', 'sqlite')
  
  
    By using it, MySQL changes to SQLite.

35. ### How can we use maintenance mode in Laravel

    When an application is in maintenance mode, a custom view is displayed for all requests into the application. It makes it easy to "disable" application while it is updating or performing maintenance. A maintenance mode check is added in the default middleware stack for our application. When an application is in maintenance mode, a **MaintenanceModeException** will be thrown with a status code of 503.

    We can enable or disable maintenance mode in Laravel 5, simply by executing the below command:

    ```
    // Enable maintenance mode  
    php artisan down  
    
    // Disable maintenance mode  
    php artisan up  
    ```

36. ### How can we create a record in Laravel using eloquent?

    We need to create a new model instance if we want to create a new record in the database using Laravel eloquent. Then we are required to set attributes on the model and call the save() method.

    ```
    public functionsaveProduct(Request $request )  
    $product = new product;  
    $product->name = $request->name;  
    $product->description = $request->name;  
    $product->save();  
    ```
37. ### How can we check the logged-in user info in Laravel?

    User() function is used to get the logged-in user

    ```
    if(Auth::check()){  
        $loggedIn_user=Auth::User();  
        dd($loggedIn_user);  
    }  
    ```

38. ### How will you describe Fillable Attribute in a Laravel model?

    In eloquent ORM, $fillable attribute is an array containing all those fields of table which can be filled using mass-assignment.

    Mass assignment refers to sending an array to the model to directly create a new record in Database.

    ```
    class User extends Model {  
        protected $fillable = ['name', 'email', 'mobile'];   
        // All fields inside $fillable array can be mass-assigned  
    }  
    ```
39. ### How will you explain Guarded Attribute in a Laravel model?

    The guarded attribute is the opposite of fillable attributes.

    In Laravel, fillable attributes are used to specify those fields which are to be mass assigned. Guarded attributes are used to specify those fields which are not mass assignable.

    ```
    class User extends Model {  
        protected $guarded = ['role'];   
        // All fields inside the $guarded array are not mass-assignable  
    }  
    ```
    If we want to block all the fields from being mass-assigned, we can use:

    ```
    protected $guarded = ['*'];  
    ```
    $fillable serves as a "white list" whereas $guarded functions serves like a "black list". One should use either $fillable or $guarded.

40. ### What do you know about Closures in Laravel?

    In Laravel, a Closure is an anonymous method which can be used as a **callback** function. It can also be used as a parameter in a function. It is possible to pass parameters into a Closure. It can be done by changing the Closure function call in the **handle()** method to provide parameters to it. A Closure can access the variables outside the scope of the variable.
    ```
    function handle(Closure $closure) {  
        $closure();  
    }  
    handle(function(){  
        echo 'Interview Question';  
    });  
    ```
    It is started by adding a Closure parameter to the handle() method. We can call the handle() method and pass a service as a parameter.

    By using $closure(); in the handle() method, we tell Laravel to execute the given Closure which will then display the 'Interview Question.'

41. ### What are service providers in laravel?

    Service providers in laravel application is the central place where application is bootstrapped. That is, laravel’s core services and our application’s services, classes and their dependencies are injected in service container through providers. 

    ### video link
        
    [<img src="https://i.ytimg.com/vi/VYPfncvYW-Y/maxresdefault.jpg" width="170" height="100">](https://www.youtube.com/watch?v=VYPfncvYW-Y)
    
42. ### Laravel Events and Listeners

    Events are just ways to alert your application that an action has happened, and the events can be dispatched at any point of your application, the controller, the model, the middleware, anywhere — even in the blade files.

    Listeners, like the name implies, listens for events that occur in your application, but they do not just listen to any event, each listener must be mapped to an event before it listens for that event.

    For a listener to respond to a dispatched event, the listener class must be mapped to a particular event class. These mappings happen in the EventServiceProvider class which can be found in the app\Providers folder.

    An event can have multiple listeners mapped to it and when it is dispatched, all listening classes will be triggered in succession following the order in which it is mapped.

    ### video link
        
    [<img src="https://i.ytimg.com/vi/VYPfncvYW-Y/maxresdefault.jpg" width="170" height="100">](https://www.youtube.com/watch?v=LvvZ0jqZnBU)