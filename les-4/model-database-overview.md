---
title: Les 4
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Overzicht: Models en de database
{: .text-green-100 .fs-6 }

**Zorg dat je deze introductie even rustig doorleest zodat je snapt hoe de model-laag in Laravel samenwerkt met de database.**  
Deze pagina geeft informatie over Eloquent, lees deze eerst door voordat je gaat bouwen.

---

De *model* laag in een MVC-framework (zoals Laravel) bevat alle functionaliteit om met de gegevens in je website of
webapplicatie te werken.

Laravel bevat hiervoor twee belangrijke onderdelen:

1. De **QueryBuilder** waarmee je vrij "low-level" SQL queries kunt uitvoeren op de database.
2. **Eloquent**. Een onderdeel die het makkelijk maakt om alle CRUD-operaties (create, read, update en delete) en meer uit te
   voeren op de gegevens in je database.

De Eloquent oplossing heeft veel meer voordelen en mogelijkheden, het is ook veiliger om deze te gebruiken.

---

### QueryBuilder

De QueryBuilder is een simpele manier om met gegevens uit je database te werken.  
Deze code laat zien hoe je alle autos' _( cars )_ ophaalt uit de `cars` table (bijvoorbeeld in een controller method):

```php
// Bovenin je PHP file moet je altijd aangeven wat je bedoelt met DB
use Illuminate\Support\Facades\DB;

// En dan bijvoorbeeld in een listCars() function in een controller
public function listCars(){
    $cars = DB::table('cars')->get(); 
    
    // $car bevat een array met alle rijen uit de cars table
    foreach ($cars as $car) {
        echo $car->name;
    }
}
```

Om een rij aan de `cars` table toe te voegen (insert) gebruik je de `insert()` method van de `DB` class:

```php
// Bovenin je PHP file moet je altijd aangeven wat je bedoelt met DB
use Illuminate\Support\Facades\DB;

// En dan bijvoorbeeld in een insertCar() function in een controller
public function insertCar(){
   DB::table('cars')->insert([
       'make'       => 'Fiat',
       'type'       => 'Panda',
       'licence'    => 'kt-234-s',
   ]);
}
```

Uiteraard kun je ook gegevens verwijderen en updaten. Lees hoe je dat doet in [de QueryBuilder documentatie](https://laravel.com/docs/10.x/queries).

---

### Eloquent

Wij gaan **Eloquent** gebruiken om met gegevens uit de database te werken.  

- In Eloquent wordt elke table uit de database gekoppeld aan een PHP (model) class.  
- Een class bevat de eigenschappen van de table en ook functions om met de gegevens te werken uit de database.


De PHP model classes staan altijd in: `app\Models`.  
Bijvoorbeeld `app\Models\Car.php`:

```php
class Car extends Model {
   // De Car erft allerlei functions van de (Eloquent) Model class 
   // Hierdoor krijg je meteen al heel veel handige functionaliteit in je class!
}
```

Om deze Car class (die in dit voorbeeld gekoppeld is aan de cars table!) te gebruiken:

```php
// Altijd bovenaan aangeven welke model class je gaat gebruiken
use App\Models\Car

// Zelfde voorbeeld als in vorige code maar dan met de Eloquent model class
public function listCar(){
    $cars = Car::all(); // Via Car model class haal je alles uit de 'cars' table
    
    // LET OP, HET VERSCHIL MET DE QUERYBUILDER IS: 
    // In elke $car zit nu een instance van de Car class (en dus geen array)
    foreach ($cars as $car) {
        echo $car->type;
    }
}
```
---

Houd goed in gedachten: **De PHP CLASS IS GEKOPPELD AAN EEN DATABASE TABLE**.

![Eloquent en database](images/eloquent-overview.png)

[Alles over Eloquent staat in de Laravel documentatie](https://laravel.com/docs/10.x/eloquent)

---

In de volgende opdracht ga je zelf een database migratie en een model class genereren voor jouw website en deze gebruiken om gegevens op te halen en te tonen in je view.
{: .text-blue-100 .fs-4 }

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Een Eloquent model class en database migration maken](model-migration-migrate)


