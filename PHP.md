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
- nie można jej skonkretyzować
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

## Polimorfizm
> "Przełączanie klas"

## SOLID
> https://medium.com/prod-io/solid-principles-takeaways-ec0825a07247
### 1. Single responsibility (pojedyncza odpowiedzialność)
### 2. Open Close Principle
Klasa powinna być otwarta na rozszerzanie a zamknięta na modyfikacje
![alt text](https://cdn-images-1.medium.com/max/1600/1*F6KliDBQMPZdycmc0CIgdg.png "Open Close Principle")

## Wzorce projektowe
### Kreacyjne
- Simple factory - **Metoda statyczna**
- Factory method - **Metoda** | *Różne formaty plików*
- Abstract factory - **Interfejs, fabryka fabryk**
- Builder - **Wieloetapowość, telescoping constructor**
- Prototype - **Klonowanie**
- Singleton - **Jedna instancja**
### Strukturalne
- Adapter - **Przejściówka, Old New**
- Facade - **Proste API**
- Proxy - **Klasa pośrednicząca, duży koszt**
- Dependency Injection - **Wstrzykiwanie** | *Konfiguracja bazy danych*
### Czynnościowe
- Mediator - **Trzecia klasa**
- Memento - **Przywrócenie stanu**
- Observer - **Stanu obiektu**
- Strategy - **Zależnie od sytuacji** | *Sortowanie*
- State - **Zmiana zachowania zależnie od stanu** | *Edytor tekstowy*
- Template Method - **Szkielet algorytmu** | *Budowanie aplikacji w zależności od systemu*
> **Single factory**

Prosta klasa z metodą statyczną do tworzenia obiektów
```php
$door = DoorFactory::makeDoor(100, 200);
```
> **Factory method**

**Metoda** tworząca obiekty nieznane ale powiązane np.: kolejne formaty plików

```php
xml, csv, pdf

$creator = new Creator();

$creator->create('xml');
$creator->create('pdf');

create {
    if(class_exists($name)) {
        return new $name();
    }
}
```
> Abstract factory

- **Interfejs** do tworzenia rodzin obiektów
- *"Fabryka fabryk"*

> Builder
- wieloetapowe tworzenie obiektu
- "telescoping constructor" 
```php
// Bad - telescoping constructor
public function __construct(
    $size,
    $cheese = true,
    $pepperoni = true,
    $tomato = false,
    $lettuce = true) {
    //
}
// Good
$burger = (new BurgerBuilder(14))->addPepperoni()->addLettuce()->addTomato()->build();
```
