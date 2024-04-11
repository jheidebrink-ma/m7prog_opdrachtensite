---
title: Les 5 
layout: page 
permalink: :path/:basename 
nav_exclude: true
---

## Gegevens ophalen in controller en weergeven in de view
{: .text-green-100 .fs-6 }

Je kunt nu (na wat oefenen) alle CRUD operaties uitvoeren met de Eloquent model class.  
Het doel is om een lijst met projecten op te halen en aan een view door te geven.  
In de view kun je met de Blade `@foreach` directive de gegevens tonen met jouw eigen HTML en CSS.  

---
### 1- Maak een functie aan in je ProjectController
Maak in je ProjectController een index functie aan waar je straks alle projecten gaat ophalen.
```php
    public function index() {
        
    }
```

---
### 2- Haal alle projecten op
Binnen deze functie haal je vervolgens alle Projecten op door het model te laden en daarbij aan te geven wat je wilt ophalen.
```php
    $projects = Project::all();
```
Of als je alleen de actieve projecten wilt ophalen, gesorteerd op title:
```php
    $projects = Project::where('active', 1)
               ->orderBy('title')
               ->take(10)
               ->get();
```
Geef vervolgens deze informatie door aan het view bestand dat je straks gaat maken: `/resources/views/projects/index.blade.php`
```php
        return view(
            'projects.index',
            [
                'projects' => $projects,
            ]
        );
```


---
### 3- Maak een view bestand 
Maak een nieuw views bestand aan:  
`/resources/views/projects/index.blade.php`
Je kunt hierbinnen de als voorbeeld een oud bestand gebruiken.  
In het content gedeelte plaats je vervolgens de loop:  
```php {% raw %}
    @foreach( $projects as $project )
        <div
            class="max-w-sm p-2 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
            <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white text-center">
                {{$project->title}}
            </h5>
        </div>
    @endforeach {% endraw %}
```


---
### 4- Maak een route aan
De route die ik nu wil gebruiken is:
```php
    Route::get('/projects/index', [ ProjectController::class, 'index' ])->name('project.index');
```


---
### 5- Test de route
Bekijk deze route en geniet van het mooie overzicht dat je gemaakt hebt op dit endpoint.
`/projects/index`

---

### Optionele video:
In de video laat ik zien hoe je dit doet.  
{% include youtube.md video="tsZTDguVaBs" %}

---

Zorg dat je na deze opdracht een werkende lijst pagina hebt met gegevens uit de database. In de volgende les ga je een formulier maken om gegevens via de model class op te slaan.
{: .text-blue-100 .fs-4 }

Ook leer je hoe je forms veilig maakt met CSRF en hoe je gegevens makkelijk kunt valideren met Laravel. Ook ga je gebruiksvriendelijke foutmeldingen als de ingevulde gegevens niet geldig zijn.
{: .text-blue-100 .fs-4 }

---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Templates](templates)
