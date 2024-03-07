---
title: Les 2
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Tailwind
{: .text-green-100 .fs-6 }

[Tailwind CSS](https://tailwindcss.com/) kun je helemaal customizen met je eigen kleuren, stijlen, lettertypen en andere zaken.  
Door gebruik te maken van Tailwind hebben wij met weinig moeite een responsive website ontwikkeld.  


---
### 1- Tailwind implementeren
Volg in deze installatie handleiding alleen stappen **1**, **2** en **3**:   
[Tailwind CSS installation](https://tailwindcss.com/docs/installation)
### Let op, de laatste twee stappen zijn voor ons anders:
#### Eerst implementeren wij de css in de header:  
Open `welcome.blade.php` in je `resources/views` folder.  
Het **\<style>\</style>** onderdeel kun je verwijderen.

Om scripts en css dynamisch in te laden kun je gebruik maken van [vite](https://laravel.com/docs/10.x/vite).  
Plaats de volgende regel in de HTML head: 
`@vite(['resources/css/app.css'])`

In het bestand `vite.config.js` staat ingesteld welke bestanden er bijgehouden worden.  
Om de bestanden te gebruiken in de public folder moet je je project compilen via npm.
Draai daarvoor het volgende commando in de terminal:
```shell
npm run dev
```

---
### 2- Compile nu de css
In de terminal kun je de css compile met dit commando:  
```npx tailwindcss -i ./resources/css/app.css -o ./public/dist/app.css --watch ```  
#### Bewaar dit commando omdat je dit elke keer moet aanzetten als je wijzigingen wilt doorvoeren in de css en JavaScript.

---
### 3- Controleer
Bekijk de website en zie dat je nu een complete site hebt met een responsive design.

---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Pas de Laravel layout aan naar jouw ontwerp en gebruik HTML/CSS en Tailwind CSS](laravel-layout)


