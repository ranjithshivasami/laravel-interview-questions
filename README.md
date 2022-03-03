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

    [![LARAVEL SERVICE PROVIDERS](https://i.ytimg.com/vi/VYPfncvYW-Y/maxresdefault.jpg =x250)](https://www.youtube.com/watch?v=VYPfncvYW-Y)


