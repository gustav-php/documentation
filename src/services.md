# Services

Services are classes that can be injected into controllers and services itself. They are defined by extending the `Service\Base` class.

```php
use GustavPHP\Gustav\Service;

class Police extends Service\Base
{
    public string $icon = '👮‍♀️';
}
```

To inject a service into a controller, you need to add the desired service to the controllers constructor.

```php
use DI\Attribute\Inject;

class DogsController extends Controller\Base
{
    public function __construcst(protected Police $police)
    {
    }

    #[Route('/police')]
    public function police()
    {
        return $this->police->icon;
    }
}
```
