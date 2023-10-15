## Events

All events must extend the `Events\Base` class.

```php
use GustavPHP\Gustav\Events;

class TestEvent extends Events\Base
{
}
```

Events can be defined by attaching the Event Attributes to a class.

```php
use GustavPHP\Gustav\Attribute\Event;
use GustavPHP\Gustav\Event;
use GustavPHP\Gustav\Logger\Logger;

#[Event('test')]
class TestEvent extends Event\Base
{
    public function handle(Event\Payload $payload): void
    {
        Logger::log('Event: ' . $payload->getEvent());
    }
}
```

Events can be dispatched from anywhere using.

```php
use GustavPHP\Gustav\Event;

//...

Event\Manager::dispatch('test', [
    'key' => 'value'
]);
```

Events are automatically added like Routes by passing the `eventNamespaces` argument to the `Configuration` constructor.

```php
$configuration = new Configuration(
    eventNamespaces: [
        'GustavPHP\Example\Events'
    ]
);

$app = new Application(configuration: $configuration);
```
