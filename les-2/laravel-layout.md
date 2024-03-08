---
title: Les 2
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Laravel layout maken voor jouw ontwerp
{: .text-green-100 .fs-6 }

![product-page-fixed-layout.png](images%2Fproduct-page-fixed-layout.png)

Eindelijk is het tijd om jouw ontwerp en stylen om te gaan zetten in HTML en CSS.  
Het belangrijkste is het maken van de layout. De layout bepaalt de algemene look en feel en indeling van je website.  
Alle pagina's maken vervolgens gebruik van die layout (zodat je geen dubbele code hoeft te maken)  
Je kunt gebruik maken van de voorbeeld layout die al in Laravel zit, bekijk eens de bestanden in de `view` folder in de `resources` folder.  

### Note
Het is in deze stap de bedoeling om 'ongeveer' een layout in te stellen.  
Probeer een menu weer te geven en een eigen footer te maken. Maak **niet** je complete website af in deze stap.   

---
#### Advies
{: .text-blue-100 .fs-4 }
Gebruik de indeling van dashboard.blade.php.  
Hierbij wordt op een dynamische manier de layout opgehaald.  
Haal maar eens alles weg en plaats de code binnen deze tags: `<x-guest-layout>`.

---
### 1- Layout instellen
Zorg dat je nu de layout in Laravel werkend hebt en dat je deze kunt gebruiken voor de "views" (pagina's) die je gaat maken.
{: .text-blue-100 .fs-4 }

Meer over layouts in Laravel vind je in de documentatie:
- [https://laravel.com/docs/10.x/blade#building-layouts](https://laravel.com/docs/10.x/blade#building-layouts)

---
### 2- Indeling van website
Voor deze les beginnen wij met een basis structuur van een pagina met de volgende items:
-  layout container
-  header met een logo en het menu
-  navigatie menu met minimaal 3 items
-  footer met copyright
-  content element met voorbeeld tekst  
_Je kunt als voorbeeld van de structuur naar de bestanden kijken in de views en layout folder._  
Zie voor meer informatie: https://laravel.com/docs/10.x/views

---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Maak een homepage view en gebruik hierbij jouw layout](homepage)


