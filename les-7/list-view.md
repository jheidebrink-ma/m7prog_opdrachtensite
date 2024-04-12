---
title: Les 7
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Lijst weergave maken met de dashboard layout
{: .text-green-100 .fs-6 }

Nu ga je eerst de lijst weergave maken met de dashboard layout.  
Ook laat je een simpele lijst zien met de gegevens en een paginering.  

Later ga je daar edit-linkjes aan toevoegen zodat je elke rij uit de database kunt gaan aanpassen.

---

### 1- Menu aanmaken
Zoek in de web.php welke view er gebruikt is voor de dashboard pagina.

Dit is het onderdeel van het huidige dashboard menu item:
{% raw %}
```php
<x-nav-link :href="route('dashboard')" :active="request()->routeIs('dashboard')">
    {{ __('Dashboard') }}
</x-nav-link>
```
{% endraw %}

Zoek nu via artisan op welke view er naar het projecten overzicht binnen het dashboard gaat met dit commando:

```shell
php artisan route:list
```

Kopieer de naam en plaats deze in het nieuwe menu item dat je gemaakt hebt.

Let op, er is mogelijk ook een hamburger menu, onderaan, daar is het ook handig om het menu item toe te voegen.

---

### 2- Dashboard view folder
Maak in de **views** folder een mapje `dashboard` plaats daarin een nieuwe map met de naam `projects` 

Kopieer het bestand `dashboard.blade.php` naar deze `projects` folder en noem hem `index.blade.php`  
Je hebt nu twee dezelfde bestanden.  
Pas in dit bestand een tekst aan zodat je weet naar welke view je kijkt en je niet per ongeluk naar de dashboard view andere bestand kijkt.   
Bijvoorbeeld het tekstje: `You're logged in!` kun je veranderen in `Projecten overzicht`

Geef aan in de `index` functie van je `controller` aan dat je een view wilt weergeven.  
Bijvoorbeeld met deze functie:
```php
return view('dashboard.projects.index');
```
_( slashes zijn vervangen door puntjes )_


---
### 3- Overzicht in je view 
In de view ga je nu een weergave maken van je projecten.  
Haal eerst in de `index` functie in je controller ( `ProjectenAdminController.php` ) de producten op.    
Geef aan dat je gebruik wilt maken van paginering. Dit doe je door de inhoud van de `index function` aan te passen in deze code:
{% raw %}
```php
$projects = Project::paginate(2);
return view('dashboard.projects.index', ['projects'=>$projects]);
```
{% endraw %}

In het view bestand `/dashboard/projects/index.blade.php` kun je nu alle projecten weergeven zoals je al eerder hebt gedaan.  
Daaronder kun je nu de paginering weergeven met deze code {% raw %}{{$projects->links()}}{% endraw %}  
Dan krijg je bijvoorbeeld zo'n stuk code:
{% raw %}
```php
@foreach($items as $item)
    <a href="{{route('project.show', $item)}}">{{ $item->title }}</a><br>
@endforeach
{{$items->links()}}
```
{% endraw %}
Let wel op dat jullie waarschijnlijk niet `$items` meegeven aan deze view, maar dat de variabele anders heet.              

---
### 4- Controleren
Om dit te bekijken ga je nu in de browser naar de dashboard projects index pagina.  
Bekijk eerst even welke routes er allemaal zijn door dit Artisan commando uit te voeren:
```shell
php artisan route:list
```
Hier zie je als het goed is een route staan voor je projecten admin index in het dashboard.  
De route naam ( aan het eind van de regel ) kun je gebruiken om dit overzicht op te halen. 
Bij mij is dat: `project.index`  
Gebruik deze route naam bijvoorbeeld op deze manier:  
```html
{% raw %}
<a href="{{route('project.index')">Naar mijn project admin index</a>
{% endraw %}
``` 

---

### Optionele video:

{% include youtube.md video="KJqt5Y7fe_I" %}

In de volgende opdracht ga je zelf een formulier maken, validatie regels toevoegen en foutmeldingen tonen.
Daarna kun je de gegevens via je Model class makkelijk toevoegen aan de database
{: .text-blue-100 .fs-4 }

---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Formulier maken en de gegevens opsturen](create-view)
