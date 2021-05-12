# laravel-interview-questions-answers


## what is Artisan ? write some commands ?
Artisan is the command line interface included with Laravel. Artisan exists at the root of your application as the artisan script and provides a number of helpful commands that can assist you while you build your application.

`php artisan list`
`php artisan make:controller DashboarController`
`php artisan serve`

## how to create custom command in laravel ?

In laravel we can create custom command from artisan 
`php artisan make:command WelcomeCommand`

or we can create closure command inside `routes/console.php`

## what is cache in laravel?

Some of the data retrieval or processing tasks performed by your application could be CPU intensive or take several seconds to complete. When this is the case, it is common to cache the retrieved data for a time so it can be retrieved quickly on subsequent requests for the same data.

some method of Cache

`Cache::put('username','kajal452',600)` 10 min
`Cache::get('username')`
`Cache::store('file')->get('foo')` store in some specific type of driver

Retrieve and store in cache

Cache::remember('users', $seconds, function () {
    return DB::table('users')->get();
});

## what is Event and Listener ?

Laravel's events provide a simple observer pattern implementation, allowing you to subscribe and listen for various events that occur within your application. Event classes are typically stored in the app/Events directory, while their listeners are stored in app/Listeners. 

## what is sevice container (Laravel Application) ?

The Laravel service container is a powerful tool for managing class dependencies and performing dependency injection. Dependency injection is a fancy phrase that essentially means this: class dependencies are “injected” into the class via the constructor or, in some cases, “setter” methods
Almost all of your service container bindings will be registered within service providers, so most of these examples will demonstrate using the container in that context.

## what is service provider ?
Service providers are the central place of all Laravel application bootstrapping. Your own application, as well as all of Laravel's core services, are bootstrapped via service providers.
we mean registering things, including registering service container bindings, event listeners, middleware, and even routes. Service providers are the central place to configure your application

there is common two methods register,boot
inside register only registering.

if our service is not required in every request then we define our service as deferred service provider 


## what is facade ?

Facades provide a "static" interface to classes that are available in the application's service container. Laravel ships with many facades which provide access to almost all of Laravel's features.

Every facade extends `Illuminate\Support\Facades` and that facade only have one static method getFacadeAccessor from where return that key name of Factory class that bind into service container

## what is middleware ?

Middleware provide a convenient mechanism for inspecting and filtering HTTP requests entering your application.
whenever we try to visit any url then if we set any route specific custom middleware then before sending request that middleware request is executing 
we can create middleware using artisan
`php artisan make:middleware BeforeMiddleware`
we can set this middleware either global,group or specific route middleware.


## what is CSRF. explain with example?

Cross-site request forgeries are a type of malicious exploit whereby unauthorized commands are performed on behalf of an authenticated user.
ex- in our application we develop that only authenticated user can update their email address. if any user already authenticated to our app and simualtenously he visit another website and that time another website if try to request our app to update email address using javascript that time if we won't use csrf then that another website can successfully change email address from our site because current user is authenticated in our site in that case if we use csrf then another website can't make that (POST,PUT,PATH,DELETE) type of request.

## what is composer ?

Composer is a tool for dependency management in PHP. It allows you to declare the libraries your project depends on and it will manage (install/update) them for you.
Suppose:

You have a project that depends on a number of libraries.
Some of those libraries depend on other libraries.
Composer:

Enables you to declare the libraries you depend on.
Finds out which versions of which packages can and need to be installed, and installs them (meaning it downloads them into your project).
You can update all your dependencies in one command.


## what is difference between authentication and authorization ?

Authentication is the way to checking that specific user logged in or not.
Authorization is that that logged in user have permission or not to access that specific url.

ex-In youtube every user is logged in but who have youtube subscription youtube don't show advertisment that user but if user don't have subscription they show advertisment. :)

we can achieve authorization using gates and policies in laravel
gates are closure based and policies are class based.
gates are written inside authserviceprovider and policies written inside   `app/policy` and we have to map which policies attach with which model inside authserviceprovider $policies variable.


## what is migration . why we should use migration in our laravel app ?

migration used for versioning our database using migration we can directly interact with our database.if we use migration then in future we won't share any sql file to another developer he/she should only run migrate method all table are automatically inserted into that specific database that is map in .env file of that user project.


## what is seeding in laravel ?

seeding is the process of inserting fake data in our database.

`php artisan db:seed` this command run your all seeder class that write inside DatabaseSeeder class run method.
if you want to run specific seeder class only then you can run
`php artisan db:seed --class=UserTableSeeder`