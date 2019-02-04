# Laravel

## Pivot table
- Nazwa tabeli powinna się składać z nazw powiązanych modeli w kolejności alfabetycznej. Wtedy automatyka Laravela sobie poradzi (https://youtu.be/vxJBqPZSYCk?t=283)

### Migracje Pivot table

```php
$table->foreign()
```
> https://laravel.com/docs/5.7/migrations#foreign-key-constraints

> https://youtu.be/Sw51ucwFfDw?t=842

### Attach

```php
// User.php
public function user() {
    return $this->belongsToMany(User::class, 'user_event')->withTimestamps();
}

// Uwaga!
// Gdy nazwa tabeli pivot jest alfabetyczna nie trzeba `user_event`
public function user() {
    return $this->belongsToMany(User::class)->withTimestamps();
}

// Events.php
?

// stworzenie wiersza w pivot table
$event->user()->attach(user_id)
```

> https://laravel.com/docs/5.7/eloquent-relationships#updating-many-to-many-relationships

> https://youtu.be/59Zrh6y87HQ?t=2504

## Soft deletes
- dodaje do tabeli `deleted_at`
- podczas usunięcia do kolumny `deleted_at` jest dodawana data
- przy zwracaniu wszystkich elementów usunięte nie są zwracane
- Eloquent dodaje
```mysql
AND deleted_at IS NULL
```

> https://youtu.be/59Zrh6y87HQ?t=240

## Data i czas
### Sprawdzanie czy eventy nachodzą na siebie

> https://youtu.be/59Zrh6y87HQ?t=1261

cd.. (surowe zapytanie + opis)
> https://youtu.be/59Zrh6y87HQ?t=3376

Inne rozwiązanie **Krzyżowe sprawdzanie daty**
> https://youtu.be/vxJBqPZSYCk?t=1486

## Repozytoria w Laravel
> https://github.com/andersao/l5-repository

> https://youtu.be/vxJBqPZSYCk?t=684

## Auth
Kombinacje z rejestrowaniem w Kernelu
> https://youtu.be/1DU0ppXxOh0?t=1362