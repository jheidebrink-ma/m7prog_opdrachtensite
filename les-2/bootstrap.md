---
title: Les 2
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Bootstrap css
{: .text-green-100 .fs-6 }

# Gebruik alleen Bootstrap als je GEEN Tailwind gebruikt
{: .text-red-100 .fs-6 }

[Tailwind CSS](https://tailwindcss.com/) kun je helemaal customizen met je eigen kleuren, stijlen, lettertypen en andere zaken.  
Door gebruik te maken van Tailwind hebben wij met weinig moeite een responsive website ontwikkeld.  


---
### 1- Bootstrap implementeren
Je kunt ervoor kiezen om Bootstrap te gebruiken voor jouw project. Volg daaar voor de volgende stappen.
[Uitleg website](https://www.kreaweb.be/laravel-11-bootstrap-5/)

Installeer de Laravel UI package
```shell
composer require laravel/ui --dev
```


Installeer de Bootstrap 5 package door dit commando uit te voeren in de terminal van je laravel docker.     
```shell
php artisan ui bootstrap --auth
```

Waarschijnlijk zag je net een melding over een commando dat je nu moest uitvoeren:
```shell
npm install && npm run dev
```

Als je nu bijvoorbeeld naar het `login.blade.php` bestand gaat dan kun je nu een bootrap style toevoegen.
Dit bestand kun je vinden in: ```resources\views\auth\login.blade.php```  
[Meer informatie over Bootstrap](https://getbootstrap.com)  
[Meer informatie over de opties](https://getbootstrap.com/docs/4.1/getting-started/introduction/)  

---
### 2- Compile nu de css
Om ervoor te zorgen dat de css bestanden gecompiled zijn en Bootstrap wordt geladen moet je je project compilen via npm.  
Draai daarvoor het volgende commando in de terminal _( in je editor )_ :
```shell
npm run dev
```
#### Bewaar dit commando omdat je dit elke keer moet aanzetten als je wijzigingen wilt doorvoeren in de css en JavaScript.

---
### 3- Controleer
Bekijk de website en zie dat je nu een complete site hebt met een responsive design.

---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Pas de Laravel layout aan naar jouw ontwerp en gebruik HTML/CSS](laravel-layout)


