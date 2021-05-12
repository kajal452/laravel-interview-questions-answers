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