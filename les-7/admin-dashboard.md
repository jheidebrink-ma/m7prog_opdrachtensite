---
title: Les 7
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Admin routes maken en dashboard layout gebruiken
{: .text-green-100 .fs-6 }

Je kunt een *verzameling* routes (url's) onder een bepaalde *prefix* hangen.  
Alle beheer pagina's kun je bijvoorbeeld onder de slug `/admin` plaatsen in je route bestand.  

Je krijgt dan bijvoorbeeld de routes:
`/admin` = Admin dashboard  
`/admin/projects` = Overzicht alle projecten  
`/admin/projects/new` = Voor aanmaken een nieuw project   
`/admin/projects/1/edit` = Voor bewerken van project met id 1  
`/admin/projects/2/edit` = Voor bewerken van project met id 2  
`/admin/users`  = Overzicht van alle gebruikers  
`/admin/.....` - Enzovoort. 

Alles begint dus met de *prefix* `/admin`  
Je kunt daarom makkelijk in één keer alle routes met de prefix `/admin` afschermen zodat alleen admin gebruikers er nog bij kunnen.

---

Zorg dat je een route group hebt voor jouw CMS / Admin functionaliteit en dat je hiervoor de dashboard view (met de app layout) gebruikt.  
Dan heb je al standaard een menu en uitlog functionaliteit.  
[Hier vind je die default bestanden](https://github.com/laravel/breeze/tree/1.x/stubs/default/resources/views) mocht je ze kwijt zijn.
{: .text-blue-100 .fs-4 }

---

## Aan de slag

### 1- Resource maken
Wij hebben al een Project model, dus wij hoeven niet een compleet nieuwe resource te maken. Je moet wel een controller maken. 

Meer info: [Lees meer over resource controllers](https://laravel.com/docs/10.x/controllers#resource-controllers)

Wij gaan een `ProjectAdminController` aanmaken voor je model.  
Bij `MijnControler` geef je de naam op van je controller, bijvoorbeeld `ProjectAdminController`.  
Bij `ModelNaam` geef je de naam op van je model, bijvoorbeeld `Project`.  

```shell
  php artisan make:controller MijnControler --model=ModelNaam
```

Je hebt nu een complete controller, bekijk `app/Http/Controllers/ProjectAdminController.php` maar even.

### 2- Routes aanmaken
In de routes gaan wij nu routes aanmaken voor alle CRUD handelingen, hiervoor kun je de route-groups gebruiken:
[Lees meer over Route groups](https://laravel.com/docs/10.x/routing#route-groups)

Maak eerst een Resource route aan:
{% raw %}
```shell
    Route::resources(
        [
            'url' => MyController::class,
        ]
    );
```
{% endraw %}

Op de plek van `url` komt de url van dit model / onderdeel te staan en op de plek van `MyController` verwijs je naar de controller die je net hebt aangemaakt.

**Let wel op** dat je er ook voor zorgt dat deze controller boven in je pagina onder 'use' toegevoegd is.

Voeg nu de `dashboard` route prefix toe, plaats deze code om het `resources` blok heen:
{% raw %}
```shell
Route::prefix('/dashboard')->group( function() {
    
});
```
{% endraw %}

Verplaats nu de de oude dashboard route ook binnen deze prefix.

En tenslotte voeg je de middleware requirements to aan de prefix zodat je zeker weet dat iemand is ingelogd als hij naar het dashboard toe gaat.

Geef deze nieuwe resource ook een naam zodat je deze later ook weer kunt gebruiken.

{% raw %}
```shell
Route::prefix('/dashboard')
     ->middleware(['auth', 'verified'])
     ->group(function () {
         Route::get(
             '/',
             function () {
                 return view('dashboard');
             })->name('dashboard');

         Route::resources(
             [
                 'projectadmin' => ProjectAdminController::class,
             ]
         )->name('projectadmin');
     });
```
{% endraw %}

### 3- Controller instellen
Plaats in de controller die je gemaakt hebt verschillende teksten om zo zeker te weten dat het werkt, bijvoorbeeld zo iets:
{% raw %}
```php
    public function index()
    {
        return 'Dit is mijn index';
    }
```
{% endraw %}


---

### Optionele video
Kijk de video om te zien hoe dit werkt.

{% include youtube.md video="2UtpkqmhmJc" %}

---

### Links

- [Lees meer over resource controllers](https://laravel.com/docs/10.x/controllers#resource-controllers)
- [Lees meer over Route groups](https://laravel.com/docs/10.x/routing#route-groups)
- [Meer over route prefixes](https://laravel.com/docs/10.x/routing#route-groups)
- [Meer over authenticatie en routes afschermen](https://laravel.com/docs/10.x/authentication#protecting-routes)

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[List view maken met dashboard layout](list-view)
