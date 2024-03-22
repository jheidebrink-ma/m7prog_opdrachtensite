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

## 4 stappen:
1. Voordat wij een master.blade.php view kunnen gebruiken, moeten wij aangeven dat er een Master Layout bestaat.  
    Ga naar deze folder `app/View/Components` en maak een nieuw bestand `MasterLayout.php` aan.  
    Gebruik een ander bestand in deze folder als voorbeeld.  
2. Maak nu een `master.blade.php` bestand aan in de folder `resource/views/layout/`
3. Plaats in deze pagina verschillende HTML onderdelen, zie een voorbeeld van een layout onderaan de pagina, deze niet gebruiken omdat hij niet werkt.    
    Belangrijk is dat je ergens aangeeft dat daar de content moet komen met deze code:    
    `{% raw %}{{ $slot }}{% endraw %}`
4. Open het project.blade.php view bestand en geef buiten je content aan dat je de master wilt extenden door deze code te plaatsen:    
   `<x-master-layout>`
5. De content binnen dit blok zal nu in op de plek waar `{% raw %}{{ $slot }}{% endraw %}` staat komen.

---
## 2- JavaScript
Dit zelfde systeem  kunnen wij ook met bijvoorbeeld JavaScript gebruiken door bijvoorbeeld deze code in `project.blade.php` te plaatsen:  
```javascript
    @section('scripts')
        <script>
            Console.log('Mijn script werkt');
        </script>
    @endsection
```

In de `footer.blade.php` kun je in de deze scripts ophalen met deze code:  
```php
    @yield( 'scripts' )
```

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


