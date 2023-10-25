## Middlewares

Middlewares are classes that are run before the controller is executed. They are defined by extending the `Middleware\Base` class.

```php
class MyMiddleware extends Middleware\Base
{
    public function handle(Psr\Http\Message\ServerRequestInterface $request): ServerRequestInterface
    {
        // do stuff with `$request`

        return $request;
    }
}
```

To use a middleware with a controller, you need to add the `GustavPHP\Gustav\Attribute\Middleware` attribute to the controllers class.

```php
#[GustavPHP\Gustav\Attribute\Middleware(new MyMiddleware())]
class CatsController extends Controller\Base
//...
```

You can add information to the request by adding attributes to the request.

```php
public function handle(Psr\Http\Message\ServerRequestInterface $request): ServerRequestInterface
{
    $request = $request->withAttribute('from-middleware', 'Hello World!');

    return $request;
}
```

And then get them from the Request in Controllers.

```php
class DogsController extends Controller\Base
{
    #[Route('/from-middleware')]
    public function police(#[Request] Psr\Http\Message\ServerRequestInterface $request)
    {
        $info = $request->getAttribute('from-middleware');

        return $this->plaintext($info);
    }
}
```
