---
title: Les 1
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Laravel Breeze installeren (inloggen/uitloggen)
{: .text-green-100 .fs-6 }

[Laravel Breeze](https://laravel.com/docs/11.x/starter-kits#laravel-breeze-installation){: target="_blank" %} is een starter kit van Laravel die
allerlei handige authenticatie features toevoegt aan je Laravel project.

Als je dit installeert krijg je o.a. registratie, inlog, uitlog, wachtwoord vergeten e.d. tot je beschikking.

---
### 1- Installeer Breeze
Doorloop nu de stappen om Breeze toe te voegen aan je project: [Installeer Breeze](https://laravel.com/docs/11.x/starter-kits#laravel-breeze-installation)
Je moet daarvoor de onderstaande commando's uitvoeren in de terminal.
```cmd
composer require laravel/breeze --dev
```
Als dit niet direct lukt, ga dan naar `Docker Desktop` en klik op de 3 puntjes achter je `php` of `Laravel.test` container en selecteer `terminal`.  
Daar kun je hetzelfde commando uitvoeren.

### 2- Breeze en Blade
Installeer nu Breeze met Blade door deze commando's uit te voeren in de bovenstaande terminal:
```shell
php artisan breeze:install
```
Vervolgens voer je een migratie voor je database uit:
```shell
php artisan migrate
```
Nu is het tijd om npm te installeren.  
Dit voer je uit in de WSL terminal in je editor _( Visual Studio )_ 
```shell
npm install
npm run dev
```

---
### 2- Controle en account
Als het goed is heb je nu ook werkende registratie, inlog/uitlog en wachtwoord vergeten functionaliteit.  
Ga maar in je browser naar je project en tik vervolgens het volgende path achter de url: `register`  
Je kunt ook rechtsboven op register klikken.  
Zorg dat je een account hebt gemaakt om mee in te loggen op je website.  

---
### 3- Commit
- Voeg alles toe aan je repository met `git add .`
- Commit (met een goede commit message) en push alles weer naar Github.

---

{% include commit_push.md %}


