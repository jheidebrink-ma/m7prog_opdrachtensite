---
title: Les 5 
layout: page 
permalink: :path/:basename 
nav_exclude: true
---

## CRUD ( Create, Read, Update, Delete ) operaties met je Eloquent model class
{: .text-green-100 .fs-6 }

Je hebt nu een Eloquent model class die gekoppeld is aan een database table.

Via deze methode is het eenvoudig gegevens toe te voegen, te lezen, aan te passen en te verwijderen (CRUD) in Laravel.  
Je hoeft geen ingewikkelde SQL queries meer te schrijven, maar werkt via de PHP model class en de ingebouwde functions met de database.

--- 
## Data versturen via de controller.  
Wij gaan tijdelijk via de controller extra projecten toevoegen om iets meer data weer te kunnen geven, dit doen wij in 3 stappen.

---
### Uitgangspunt
{: .text-green-100 .fs-6 }
Ik ga er in dit voorbeeld vanuit dat je in de afgelopen lessen een `Project` model én een `ProjectController` hebt aangemaakt.  
Als je die anders genoemd hebt niet dan moet je overal waar een referentie staat naar een `Project` je eigen object naam plaatsen.  
Of je maakt een nieuw model en controller via php artisan:  
```shell
php artisan make:Controller ProjectController
```

---
### 1- Route aanmaken
Maak een nieuwe route aan in `routes/web.php`, bijvoorbeeld:
```php
    Route::get('/projects/add', [ ProjectController::class, 'add' ])->name('project.add');
```

---
### 2- Controller endpoint aanmaken
Deze nieuwe route moet natuurlijk wel ergens verwerkt worden. Dat doe je in het controller bestand: `app/Http/Controllers/ProjectController.php`.  
Daar moet nu een `add` functie komen die de data gaat toevoegen.  
Plaats dit binnen de Class.
```php
    public function add() {
        
    }
```

---
### 3- Project aanmaken
Met de volgende code kun je een model aanmaken en vervolgens toevoegen aan de database, plaats deze code binnen de bovenstaande functie.
Let op:
Op de plek van `Model` moet waarschijnlijk iets anders staan.  
Waarschijnlijk heb jij in de migratie niet een `field_one` kolom toegevoegd aan je model, kijk maar eens in je laatste bestand in de **migration folder** en voeg daar de velden toe die je wilt vullen.  
```php
    // Maak een model aan
    $model = new Model();
    // definieer de velden
    $model->field_one = 'mijn data';
    // sla het model op
    $model->save();
```
Bijvoorbeeld zo iets, je hoeft alleen velden in te vullen die je wilt:
```php
    $model->titel       = 'Mijn titel';
    $model->description = 'mijn verhaal';
    $model->active      = true;
```



---
## 4- Resultaat
Roep de nieuwe url op in je browser. [http://localhost/projects/add](http://localhost/projects/add)

Als het goed is zie je een witte pagina.

Nu kun je in de database zien dat je een project is aangemaakt.


---

### Optionele video
In de video kun zien hoe je deze model class kunt gebruiken om alle gegevens in de table op te halen via de model class en hoe je die gegevens vervolgens aan de view kunt geven om ze te tonen.

Meer informatie: [Crud videos](crud)



---

Zorg dat je alle CRUD operaties hebt uitgeprobeerd en kan toepassen in je code.
{: .text-blue-100 .fs-4 }

---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Gegevens ophalen in controller en weergeven in de view](model-view-loop)


