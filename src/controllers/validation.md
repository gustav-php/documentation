# Validation

Request validation is achieved by the arguments itself. If a argument for `Body` and `Query` has no default value, its required. 

```php
#[Route('/some')]
public function get(
    #[Query('required')] string $required,
    #[Query('optional')] string $optional = 'default',
) {
}
```


The same goes for DTO.

```php
class SomeDto
{
    public string $required;
    public string $optional = 'default';
}
```