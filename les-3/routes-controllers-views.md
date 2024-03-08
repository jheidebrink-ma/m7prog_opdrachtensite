---
title: Les 3
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Routes, controllers en view maken
{: .text-green-100 .fs-6 }

Wij gaan nu een aantal routes maken voor je website.  
In eerste instantie wil ik deze pagina maken: http://localhost/about

**Denk na over verschillende pagina's en functionaliteiten:**
Bijvoorbeeld:
- Wat zou de titel van de pagina zijn?
- Wat is een mooie url, bijvoorbeeld: `/projecten` of `/about` of `/contactformulier`.
- Welke naam zou de controller krijgen?, bijvoorbeeld: `ProjectController`, `AboutController`, `ContactController`.

---

## Maak routes, controllers en views voor jouw website
{: .text-green-100 .fs-6 }

Voor alle pagina's ga je nu een route maken, een controller en een view.  
Daarna ga je de pagina's in je navigatie zetten zodat je door de site kan klikken (met nog lege pagina's)

### PHP Artisan
Je kunt routes met de hand maken door verschillende documenten aan te maken en te linken met elkaar, maar Laravel kan je ook via de Artisan commando's uitvoeren.  
Zie voor meer informatie:
[https://laravel.com/docs/10.x/artisan](https://laravel.com/docs/10.x/artisan)
Deze commando's voer je uit in de terminal, dit kan in de code editor of in docker.  
Afhankelijk van je setup gebruik je `php artisan` of `sail artisan`, hier krijg je vanzelf een melding van te zien als je de verkeerde manier gebruikt. 

---
### 1- Controller aanmaken
Om een controller aan te maken gebruik je dit commando:  
`php artisan make:controller controllerName`

Bijvoorbeeld voor mijn about pagina wat wij nu gaan aanmaken:  
`php artisan make:controller AboutController`  

_Let op: dat je deze naam CammelCase is en met een kapitaal begint_  
_Let op: gebruik engelse benamingen voor models en controllers._
{: .text-red-100 .fs-4 }


Later gaan wij models aanmaken en migraties, om een model aan te maken gebruik je dit commando:
`php artisan make:model modelName`  
_Let op dat je op de plek waar modelName staat je natuurlijk wel de juiste model naam moet plaatsen._  
Bijvoorbeeld: `About`  
_Let op: een model is enkelvoud, deze staat straks gelijk aan één regel in uit de database._

Om meerdere elementen _( model én controller )_ te gelijk aan te maken kun je bijvoorbeeld het volgende commando uitvoeren om een model én een controller aan te maken:  
`php artisan make:model modelName -c`

Je kunt ook een combinatie maken, hierbij een aantal opties:
- `-c`, `--controller` Create a new controller for the model
- `-f`, `--factory` Create a new factory for the model
- `--force` Create the class even if the model already exists
- `-m`, `--migration` Create a new migration file for the model
- `-s`, `--seed` Create a new seeder file for the model
- `-p`, `--pivot` Indicates if the generated model should be a custom intermediate table model
- `-r`, `--resource` Indicates if the generated controller should be a resource controller

---
## 2- Controller configureren
In de /app/Http/Controllers vind je nu de nieuwe Controller, `AboutController` open deze.  
Voeg de volgende publieke functie toe:
```php
public function index() {
    return 'Dit is de about pagina.';
}
```
Nu heb je een functie gemaakt die wij als route kunnen aanroepen.  
Deze functie zal een tekstje weergeven op de pagina.

---
## 3- Routes
Ga nu naar het bestand: `/routes/web.php`  
Daar kun je een route aanmaken die naar deze functie verwijst. Geef hierbij aan:
- Welke request methode je gebruikt: `GET` / `POST` / `DELETE` / `PATCH` / `PUT`
- Wat de url is
- Welke class je aanroept
- Welke functie je binnen die class aanroept
Bijvoorbeeld:
```
Route::METHOD(URL, CLASS)->name(INTERNE_NAAM);
```
Bijvoorbeeld voor onze **about** pagina:
```
Route::get('/about', [ \App\Http\Controllers\AboutController::class, 'index'])->name('about');
```

---
### 4- Controle
Bekijk nu wat er in de browser gebeurd door naar de about pagina te gaan, bijvoorbeeld:
http://localhost:89/about

---
### Video:
Kijk de video om te zien hoe je dat doet:
{%include youtube.md video="YdAnPq6hMZo" %}

---
Zorg dat je na deze video alle routes hebt voor jouw website.
{: .text-blue-100 .fs-4 }

---

### Meer uitleg en ondersteuning?

In de Laravel documentatie staat ALLE uitleg over hoe je routes en controllers gebruikt, met voorbeelden.

- [Laravel Routes](https://laravel.com/docs/routing)
- [Laravel Controllers](https://laravel.com/docs/controllers)

---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Menu maken met links (routes) naar alle pagina's](navigatie)


