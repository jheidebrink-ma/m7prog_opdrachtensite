---
title: Les 3
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Navigatie / menu toevoegen met alle (relevante) pagina's
{: .text-green-100 .fs-6 }

Nu je een aantal routes/pagina's hebt gemaakt en je er in je browser naar toe kunt navigeren, ga je een menu bewerken.  
Uiteraard gebruik je je eigen HTML en CSS en design.  
Als je het dashboard.blade.php voorbeeld hebt gebruikt dan heb je een navigation.blade.php bestand met daarin een **desktop** én een **mobiel** menu.

---
### 1- a href tag
In de HTML kun je links maken naar een betreffende route.  
Hiervoor gebruik je de naam van de route die je hebt ingesteld bij de betreffende route.  
Bijvoorbeeld bij de about route: 
```
{% raw %}{{ route('about') :}{% endraw %}
```
In de blade templates kun je php functies aanroepen door aan te geven dat je iets wilt uitvoeren.  
Dat doe je door een code te plaatsen tussen deze twee karakters:  
`{% raw %}{{ }}{% endraw %}`  
Nu roepen wij een route aan die wij hebben ingesteld, een compleet voorbeeld is dit:
```html
    <a href="{% raw %}{{route('about')}}">About</a>{% endraw %}
```

---
### 2- Menu aanpassen
Zorg ervoor dat je vanuit het menu naar de about pagina kunt linken.

---
### Optionele video:
Kijk de video hoe je navigatie in je layout kunt toevoegen zodat je deze op elke pagina ziet.
{% include youtube.md video="aDg-Qg5FL4Y" %}

---

Zorg dat je na deze les een werkend menu hebt om te navigeren naar de routes / pagina's op je website.  
{: .text-blue-100 .fs-4 }
Minimaal de link naar de about pagina moet werken.

---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Actieve pagina een andere class/stijl geven](active-route)


