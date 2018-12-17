# PHP

## Interfejsy

- tylko publiczne metody

```php
interface IWriter
{
    public function write();
}
```
- klasa może mieć wiele interfejsów
```php
class BigWriter implements IWriter, IReader {
    public function write() {
        echo '<h1>Big writer</h1>';
    }
    public function read() {
        echo 'reading...';
    }
}
```

## Klasy abstrakcyjne
- metody public, protected lub private
```php
abstract class Writer
{
    abstract protected function write();
}
```
- klasa może dziedziczyć tylko po jednej klasie abstrakcyjnej
- `musi` mieć przynajmniej jedną metodę abstrakcyjną, która `nie może` mieć implementacji
- pozostałe metody nie-abstrakcyjne mogą mieć implementacje