## Routing

The framework uses an internal router to match incoming requests to the defined routes. The router is parsing all routes and stores them in a hashmap. This way the router can match the incoming request to the correct route in O(1) time.

```php
#[Route('/dogs')]
public function list()

#[Route('/dogs', Method::POST)]
public function create(#[Param('name')] string $name)

#[Route('/dogs/:dog')]
public function get(#[Param('dog')] string $id)

#[Route('/dogs/:dog/collars', Method::POST)]
public function get(#[Param('dog')] string $id, #[Param('color')] string $color)

#[Route('/dogs/:dog/collars/:collar')]
public function get(#[Param('dog')] string $id, #[Param('collar')] string $collar)
```
