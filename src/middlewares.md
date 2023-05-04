## Middlewares

Middlewares are classes that are run before the controller is executed. They are defined by extending the `Middleware\Base` class.

```php
class Security extends Middleware\Base
{

    public function __construct()
    {
    }

    public function handle(Request $request, Response $response, Context $context): void
    {
        // do stuff here
    }
}
```

To add a middleware to a controller, you need to add the `Middleware` attribute to the controllers class.

```php
use GustavPHP\Gustav\Attribute;

#[Attribute\Middleware(Security::class)]
class CatsController extends Controller\Base
//...
```

You can extend the `Context` class to add custom data to the context. The Context is passed to all following middlewares and the executed controller.

```php
class DogsController extends Controller\Base
{
    #[Route('/from-context')]
    public function police()
    {
        return $this->context;
    }
}
```
