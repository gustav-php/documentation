# Routing

You use the `GustavPHP\Gustav\Attribute\Route` attribute to define an endpoint.

```php
#[Route('/dogs')]
public function list()
```

By default the `GET` method is used, however you can pass a method using the `GustavPHP\Gustav\Router\Method` enum.

```php
#[Route('/dogs', Method::POST)]
public function create()
```

You can also use parameters in your path by surround a path segment with curly braces. You can access a param by using the `GustavPHP\Gustav\Attribute\Param` attribute in the arguments.

The argument passed to the attribute must match the one from the desired path segment.

```php
#[Route('/dogs/{dog}')]
public function create(#[Param('dog')] string $id)
```

Of course you can use multiple parameters.

```php
#[Route('/dogs/{dog}/collars/{collar}')]
public function getCollar(
    #[Param('dog')] string $id,
    #[Param('collar')] string $collar
)
```

The framework uses an internal router to match incoming requests to the defined routes.

The router is parsing all routes upfront and stores them in a hashmap on start. This way the router can match the incoming request to the correct route in O(1) time.
