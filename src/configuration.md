# Configuration

Learn how to configure Docus.

```php
$configuration = new Configuration(
    mode: \GustavPHP\Gustav\Mode::Production,
    namespace: __NAMESPACE__,
    cache: __DIR__ . '/../cache/',
    files: __DIR__ . '/../public/',
    eventNamespaces: [],
    routeNamespaces: [],
    serviceNamespaces: [],
    serializerNamespaces: []
);
```

| **Key**                | **Description**                                         |
| ---------------------- | ------------------------------------------------------- |
| `mode`                 | Sets the application in development or production.      |
| `namesüace`            | Sets the application namespace for namespace discovery. |
| `cache`                | Absoulute path to the directory used for cache.         |
| `files`                | Absoulute path to the directory used for static assets. |
| `eventNamespaces`      | Namespace for all additional Event classes.             |
| `routeNamespaces`      | Namespace for all additional Route classes.             |
| `serviceNamespaces`    | Namespace for all additional Service classes.           |
| `serializerNamespaces` | Namespace for all additional Serializer classes.        |
