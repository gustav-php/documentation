# Request

Handlers often need access to the client request details. GustavPHP provides access to the request object of the underlying server. We can access the request object by instructing the framework to inject it by adding the `GustavPHP\Gustav\Attribute\Request` attribute to the method's signature.

```php
use GustavPHP\Gustav\Attribute\Request;
use Psr\Http\Message\ServerRequestInterface;

#[Route('/dogs')]
public function list(#[Request] ServerRequestInterface $request)
```

## Query Parameters

Query parameters are a common way to pass data to a server through a URL. In the context of the GustavPHP framework, query parameters can be accessed through the request object's `getQueryParams()` method or the `GustavPHP\Gustav\Attribute\Query` attribute.

Using the request object:

```php
#[Route('/dog')]
public function get(#[Request] ServerRequestInterface $request) {
    $query = $request->getQueryParams();
    $id = $query['id'];
}
```

Using the attribute:

```php
#[Route('/dog')]
public function get(#[Query] array $query) {
    $id = $query['id'];
}
```

You can also pass the key in order to get the desired query parameter:

```php
#[Route('/dog')]
public function get(#[Query('id')] string $id) {
    // Use the value of the `?id=` query parameter
}
```

## Body

The request body is a part of an HTTP request that contains data that is sent from the client to the server. In the context of the GustavPHP framework, the request body can be accessed through the request object's `getBody()` method or the `GustavPHP\Gustav\Attribute\Body` attribute.

Using the request object:

```php
#[Route('/dog', Method::POST)]
public function create(#[Request] ServerRequestInterface $request) {
    $body = $request->getBody();
    $name = $body['name'];
}
```

Using the attribute:

```php
#[Route('/dog', Method::POST)]
public function create(#[Body] array $body) {
    $id = $query['id'];
}
```

You can also pass the key in order to get the desired query parameter:

```php
#[Route('/dog', Method::POST)]
public function create(#[Body('name')] string $name) {
    // Use the value of the `name` query parameter
}
```

## Header

HTTP headers are additional pieces of information that are sent along with an HTTP request or response, providing metadata about the request or response. In the context of the GustavPHP framework, the request body can be accessed through the request object's `getHeader($name)` method or the `GustavPHP\Gustav\Attribute\Header` attribute.

Using the request object:

```php
#[Route('/dog')]
public function get(#[Request] ServerRequestInterface $request) {
    $userAgent = $request->getHeader('User-Agent');
}
```

Using the attribute:

```php
#[Route('/dog')]
public function get(#[Header] array $headers) {
    $userAgent = $headers['User-Agent'];
}
```

You can also pass the key in order to get the desired query parameter:

```php
#[Route('/dog')]
public function get(#[Header('User-Agent')] string $userAgent) {
    // Use the value of the `name` query parameter
}
```

## Data Transfer Object

In order to avoid 10+ arguments for more complex payloads, you can also set the data type from arguments used with the `Query` and `Body` attributes to a class.

Every public property will be used as a param. Properties with a default value are flagged as optional.

```php
class DogDto
{
    public string $name;
    public string $breed;
    public bool $cute = true;
}
```

This class can now be used as a DTO like this:

```php
#[Route('/dog')]
public function get(#[Query] DogDto $dogDto) {

}

#[Route('/dog', Method::POST)]
public function create(#[Body] DogDto $dogDto) {

}
```
