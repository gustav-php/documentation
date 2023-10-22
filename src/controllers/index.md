## Controllers

Controllers are the heart of the framework.

They are responsible for handling incoming requests and returning a response. All controllers must extend the `Controller\Base` class.

```php
use GustavPHP\Gustav\Controller;

class DogsController extends Controller\Base
{
}
```

Routes are defined by attaching the `GustavPHP\Gustav\Attribute\Route` Attributes to public controller methods.

```php
use GustavPHP\Gustav\Attribute\Route;

class DogsController extends Controller\Base
{
    private $dogs = [
        [
            'name': 'Rex',
            'breed': 'German Shepherd'
        ]
    ];

    #[Route('/dogs')]
    public function list()
    {
        return $this->json($this->dogs);
    }
}
```

You can also define the HTTP method that the route should respond to adding the `Method` enum to the `Route` parameters. You can also define the route parameters by adding the `Param` attribute to the function parameters.

```php
//...
use GustavPHP\Gustav\Attribute\Body;
use GustavPHP\Gustav\Router\Method;

class DogsController extends Controller\Base
{
    //...
    #[Route('/dogs', Method::POST)]
    public function create(#[Body('name')] string $name)
    {
        return $this->json([
            'name': 'Rex',
            'breed': 'German Shepherd'
        ])
    }
}
```

Now we just need to inizialize the framework and we are ready to go.

```php
use GustavPHP\Gustav\Application;

//...

$app = new Application(routes: [CatsController::class]);

$app->start();
```

Instead of adding every controller manually, Gustav PHP can also automatically discover all Controllers in the Namespace by using the Configuration. This is done by adding the `routeNamespaces` argument to the `Configuration` constructor.

```php
$configuration = new Configuration(
    routeNamespaces: [
        'GustavPHP\Example\Routes'
    ]
);

$app = new Application(configuration: $configuration);
```

Full example:

```php
use GustavPHP\Gustav\Application;
use GustavPHP\Gustav\Attribute\Param;
use GustavPHP\Gustav\Attribute\Route;
use GustavPHP\Gustav\Controller;
use GustavPHP\Gustav\Router\Method;

class DogsController extends Controller\Base
{
    protected array $dogs = [
        'Fido',
        'Rex',
        'Spot',
    ];

    #[Route('/dogs')]
    public function list()
    {
        return $this->dogs;
    }

    #[Route('/dogs', Method::POST)]
    public function create(#[Param('name')] string $name)
    {
        $this->dogs[] = $name;

        return $this->dogs;
    }
}

$app = new Application(routes: [CatsController::class]);

$app->start();
```
