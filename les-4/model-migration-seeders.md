---
title: Les 4 
layout: page 
permalink: :path/:basename 
nav_exclude: true
---

## Een seeder maken
{: .text-green-100 .fs-6 }

Op dit moment heb je een tabel gemaakt met bijbehorend model.  
Nu is het tijd om ook wat voorbeeld data in de tabel te plaatsen.  
Dat doe je door gebruik te maken van Seeders.  

---
## 1- Seeder aanmaken
Eerst gaan we een nieuwe seeder maken om straks data toe te kunnen voegen:  
```shell
php artisan make:seeder ProjectSeeder
```

Er is nu een nieuwe seeder aangemaakt waarmee een project toegevoegd kan worden.  
Open maar het bestand: 
```
/database/seeders/ProjectSeeder.php
```

Hier vind je de `run` functie.  
Deze voert het toevoegen uit.  
Je kunt nu Laravel Eloquent gebruiken om je data toe te voegen.  
Dit lijkt erg op zoals wij straks met models omgaan.  
Om gebruik te maken van deze seeder moet je eerst de DB functionaliteit importeren. Daarvoor moet je deze regel toevoegen bovenin het php document ( het `use` gedeelte ):  
```use Illuminate\Support\Facades\DB;```

Het is ook mogelijk om gebruik te maken van **Model Factories** hierbij kun je een aantal items met random data zoals fake tekst toevoegen.  
Zorg ervoor dat in het `use` gedeelte bovenaan de code ook de faker geladen wordt:   
```use Faker\Factory as Faker; ```  
Bovenaan in de functie geef je aan dat je een faker wilt gebruiken om fake data toe te voegen. Dit hoeft niet, je kunt ook zelf de data verzinnen zoals in het voorbeeld met de hand.  
```shell
    $faker = Faker::create();
```

**Elementen**  
Velden die jij zelf hebt bedacht maar hier niet staan zul je moeten toevoegen.   
Vul de verschillende elementen van het model via faker:   
```shell
    DB::table('projects')->insert([
        'title'       => $faker->colorName(),
        'intro'       => $faker->text(50),
        'description' => $faker->text(),
        'active'        => true,
    ]);
```
Of met de hand:
```shell
    DB::table('projects')->insert([
        'title'         => 'Mijn project titel',
        'intro'         => 'Anim non lorem sit est.',
        'description'   => 'Enim labore eu, sed. Sed esse incididunt aute velit. Incididunt, aute velit duis amet sint. Duis amet sint pariatur esse anim officia mollit. Sint pariatur esse anim. Esse anim officia mollit laboris aliqua, et esse.',
        'active'        => true,
    ]);
```


---
## 2- Seeder uitvoeren
Voor het toevoegen van de tabel en instellingen hoeven wij geen mysql te schrijven, maar kan ik Laravel de opdracht geven om dit uit te voeren. 
Gebruik hiervoor de seed functionaliteit van Laravel:
```shell
// Wanneer je gebruik maakt van de originele docker setup
php artisan db:seed --class=ProjectSeeder
```
```shell
// wanneer je gebruik maakt van sail
sail artisan db:seed --class=ProjectSeeder
```

## 3- Controle  
Open nu de database interface ( via een app of phpmyadmin ) en controleer of de data is toegevoegd.   


---
### Optionele video:
{% include youtube.md video="WGYmEdzZgtM" %}

---

{% include commit_push.md %}


