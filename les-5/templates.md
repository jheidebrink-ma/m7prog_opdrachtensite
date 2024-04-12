---
title: Les 5
layout: page 
permalink: :path/:basename 
nav_exclude: true
---

## Layout implementatie
{: .text-green-100 .fs-6 }

Nu heb je verschillende onderdelen van je website en is het handig om onderdelen van de layout te gaan hergebruiken.

In andere projecten gebruikte je daarvoor de de include en require functionaliteit van php.

In Laravel kun je gebruik maken van een basis template waar je variabele objecten in gaat stoppen. 

---
## 1- Yield
Er zijn twee verschillende manieren om deze implementatie te gebruiken. Wij gaan aan de slag met het `@yield` commando.
Zie voor meer informatie [https://laravel.com/docs/10.x/blade](https://laravel.com/docs/10.x/blade)

Wij gaan een master layout maken waar wij verschillende elementen gaan toevoegen. Elke template zal de master gaan extenden ( uitbreiden ).  
Ik gebruik `php artisan` om zoveel mogelijk automatisch te laten uitvoeren.  
Meer informatie over components [https://laravel.com/docs/11.x/blade#components](https://laravel.com/docs/11.x/blade#components)

## 6 stappen:
1. Begin met het maken van een component met onderstaande `php artisan` commando.
   Plaats op de plek van `NAAM-VAN-COMPONENT` de naam van je component, bijvoorbeeld **MasterLayout**.
    ```shell
     php artisan make:Component NAAM-VAN-COMPONENT
    ```
2. In deze folder: `app/View/Components` zie je nu een nieuw bestand: `MasterLayout.php`, open deze en geef in de render functie aan dat je de `layouts.master` wilt weergeven.  
   `return view('layouts.master');`
3. Maak nu een nieuwe view aan in je layouts folder: `master.blade.php`
4. Plaats in deze pagina verschillende HTML onderdelen, zie een voorbeeld van een layout onderaan de pagina, deze niet gebruiken omdat hij niet werkt.    
    Belangrijk is dat je ergens aangeeft dat daar de content moet komen met deze code:    
    `{% raw %}{{ $slot }}{% endraw %}`
5. Open het project/index.blade.php view bestand en geef buiten je content aan dat je de master wilt extenden door deze code te plaatsen:   
   `<x-master-layout>`
6. De content binnen dit blok zal nu in op de plek waar `{% raw %}{{ $slot }}{% endraw %}` staat komen.

---
## 2- JavaScript
Dit zelfde systeem kunnen wij ook voor bijvoorbeeld de JavaScripts gebruiken door deze code in je `layouts/project/index.blade.php` te plaatsen:
_( let op, dit is een niet bestaande javascript functie, plaats zelf een stukje javascript dat wel werkt )_
```javascript
    @section('scripts')
        <script>
            doeIets('Mijn script werkt');
        </script>
    @endsection
```

In de `layouts/partials/footer.blade.php` kun je de scripts section ophalen met de code `@yield( 'scripts' )`  
Heb je dit bestand nog niet? Maak dan in je `layouts` folder een mapje `partials` aan, hier komen verschillende onderdelen in zoals de footer.  
Plaats hierin je nieuwe **footer.blade.php** bestand, met daarin de volgende code:  
```php
    @yield( 'scripts' )
```

Nu is het nog de bedoeling dat deze footer in de master.blade.php geladen gaat worden.  
Dit kun je doen met de `@include` functie zoals je ook in andere blade bestanden ziet voor bijvoorbeeld het menu.  

---
## Voorbeeld

```html
{% raw %}<!DOCTYPE html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="csrf-token" content="{{ csrf_token() }}">
    <title>@yield('page_title') | {{ config('app.name', 'MA-Site') }}</title>
    @vite(['resources/css/app.css', 'resources/js/app.js'])
</head>
<body class="font-sans antialiased">
<div class="min-h-screen bg-gray-100 dark:bg-gray-900">
    <!-- Page Heading -->
    @if (isset($header))
    <header class="bg-white dark:bg-gray-300 shadow">
        <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
            {{ $header }}
        </div>
    </header>
    @endif

    <!-- Page Content -->
    <main class="bg-red-500">
        {{ $slot }}
    </main>
</div>
@include('layouts.partials.footer')
@include('layouts.partials.scripts')
</body>
</html>{% endraw %}
```

---

{% include commit_push.md %}


