# Configuration

Learn how to configure Docus.

```php
$configuration = new Configuration(
    mode: \GustavPHP\Gustav\Mode::Production,
    cache: __DIR__ . '/../cache/',
    files: __DIR__ . '/../public/',
    eventNamespaces: [
        __NAMESPACE__ . '\Events'
    ],
    routeNamespaces: [
        __NAMESPACE__ . '\Routes'
    ],
    serviceNamespaces: [
        __NAMESPACE__ . '\Services'
    ],
    serializerNamespaces: [
        __NAMESPACE__ . '\Serializers'
    ],
);
```

| **Key**                | **Description**                                         |
| ---------------------- | ------------------------------------------------------- |
| `mode`                 | Sets the application in development or production.      |
| `cache`                | Absoulute path to the directory used for cache.         |
| `files`                | Absoulute path to the directory used for static assets. |
| `eventNamespaces`      | Namespace for all Event classes.                        |
| `routeNamespaces`      | Namespace for all Route classes.                        |
| `serviceNamespaces`    | Namespace for all Service classes.                      |
| `serializerNamespaces` | Namespace for all Serializer classes.                   |
