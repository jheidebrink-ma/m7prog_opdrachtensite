---
title: Les 4 
layout: page 
permalink: :path/:basename 
nav_exclude: true
---

## Een model class en database migration maken
{: .text-green-100 .fs-6 }

Nu je een beeld hebt van hoe Laravel (PHP) via Eloquent samenwerkt met de database ben je klaar om zelf aan de slag te gaan.

Dit ga je doen (de video kan je extra informatie geven):

1. Een Eloquent model class en een database migration maken.
2. De database migration aanpassen (welke velden wil je in je tabel?).
3. De database migration uitvoeren, zodat de table ook echt wordt aangemaakt.

---
## 1- Model class aanmaken
Het Model element is een vertaling / verbinding tussen de website en de database.  
Op onze website komen verschillende projecten.  
Voor deze projecten gaan wij een model aanmaken. 
Ook maken wij gelijk een database migratie aan, hiervoor gebruiken wij de `-m` optie.  
Zorg ervoor dat je model naam met een kapitaal begint.
```shell
php artisan make:model -m Project
```

Je ziet nu dat er een model én een migratie aangemaakt zijn:
```
INFO  Model [app/Models/Project.php] created successfully.

INFO  Migration [database/migrations/2024_02_05_151958_create_projects_table.php] created successfully.
```

Open nu het Model bestand: `app/Models/Project.php` en bekijk eens welke functies er al beschikbaar zijn doordat hij een uitbreiding is op de algemene Model class.    
_Dit bestand kun je nu weer sluiten omdat wij verder gaan met de migraties._

---
## 2- Migratie
Open nu het migratie bestand dat net is aangemaakt en voeg daar de elementen toe die noodzakelijk zijn.  
Dit bestand is te vinden in de folder `/database/migrations/` Meestal is dit het laatste bestand.  
Je ziet nu al een stukje code klaar staan dat ervoor zorgt dat er een nieuwe tabel aangemaakt wordt.  
Ook zie je dat Laravel alvast twee kolommen toe wilt voegen.  
Wij maken nu een paar extra elementen aan, bijvoorbeeld voor een titel en een omschrijving:
```php
    Schema::create('projects', function (Blueprint $table) {
            $table->id();
            $table->string('title');
            $table->text('description')->nullable();
            $table->boolean('active')->default(false);
            $table->timestamps();
        });
```
Ik heb een column voor 'title' toegevoegd, een tekst column voor de description en een boolean om aan te geven of dit project wel of niet actief is.
Kun je zelf nog andere elementen voor de projecten verzinnen? Misschien een `intro` column.  
Zie hier een overzicht van alle mogelijke types: [available-column-types](https://laravel.com/docs/10.x/migrations#available-column-types)  
**Let op: blijf gebruik maken van engelse benamingen, gebruik niet `titel` en `title` door elkaar**

--- 
## 3- Migratie uitvoeren
Voor het toevoegen van de tabel met de kolommen hoeven wij geen mysql te schrijven, maar kan ik Laravel de opdracht geven om dit uit te voeren. 
Gebruik hiervoor de migratie functionaliteit van Laravel:
```shell
// Wanneer je gebruik maakt van de originele docker setup
php artisan migrate
```
```shell
// wanneer je gebruik maakt van sail
sail artisan migrate
```
De kans is groot dat je nu een error ziet doordat Artisan geen verbinding kan maken met de database.  
De oplossing hiervoor is door dit commando uit te voeren vanaf de `laravel` / `php` instance in Docker.  
_Open daarvoor het terminal venster door in docker desktop op de drie puntjes achter de betreffende container te klikken en terminal te selecteren._

Open nu de database interface ( via een app als **HeidiSQL** of **SequelAce** of de webinterface **phpmyadmin** ) en controleer of de tabel is toegevoegd.   

---
### Optionele video:
{% include youtube.md video="WGYmEdzZgtM" %}

---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Een database seeder maken](model-migration-seeders)


