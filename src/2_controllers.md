## Controllers

Controllers are the heart of the framework. They are responsible for handling incoming requests and returning a response. All controllers must extend the `Controller\Base` class.

```php
use GustavPHP\Gustav\Controller;

class DogsController extends Controller\Base
{
}
```

Routes can be defined by attaching the Route Attributes to public controller functions.

```php
//...
use GustavPHP\Gustav\Attribute\Route;

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
}
```

You can also define the HTTP method that the route should respond to adding the `Method` enum to the `Route` parameters. You can also define the route parameters by adding the `Param` attribute to the function parameters.

The `name` argument in the `Param` attribute is used to define the parameter mapped to the payload.

```php
//...
use GustavPHP\Gustav\Attribute\Param;
use GustavPHP\Gustav\Router\Method;

class DogsController extends Controller\Base
{
    //...
    #[Route('/dogs', Method::POST)]
    public function create(#[Param('name')] string $name)
    {
        $this->dogs[] = $name;

        return $this->dogs;
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
