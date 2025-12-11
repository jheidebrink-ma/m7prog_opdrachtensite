---
title: Les 11
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Afbeeldingen verkleinen en vergroten
{: .text-green-100 .fs-6 }

Je gaat afbeeldingen automatisch verkleinen of vergroten naar een specifieke grootte.

---
### 1- Image facade importeren
Open je controller waar je de image upload verwerkt.  
Voeg bovenaan het bestand de Image facade toe:

```php
use Intervention\Image\Facades\Image;
```

---
### 2- Afbeelding verkleinen na upload
Na het uploaden van de afbeelding kun je deze verkleinen voordat je hem opslaat.  
Pas je `store` methode aan:

```php
public function store(Request $request)
{
    // Validatie...
    
    $image = $request->file('plaatje');
    
    if (!empty($image)) {
        // Upload de originele afbeelding
        $path = $image->store('public/projecten');
        
        // Maak een Image instance van de geüploade afbeelding
        $fullPath = storage_path('app/' . $path);
        $img = Image::make($fullPath);
        
        // Verklein de afbeelding tot maximaal 800px breed
        $img->resize(800, null, function ($constraint) {
            $constraint->aspectRatio();  // Behoud verhouding
            $constraint->upsize();        // Voorkom vergroten
        });
        
        // Sla de verkleinde versie op
        $img->save($fullPath);
        
        // Sla het path op in de database
        $project->image = $path;
    }
    
    $project->save();
    // ...
}
```

---
### 3- Verschillende groottes maken
Je kunt ook meerdere versies van een afbeelding maken (thumbnail, medium, large):

```php
if (!empty($image)) {
    // Upload origineel
    $path = $image->store('public/projecten');
    $fullPath = storage_path('app/' . $path);
    $img = Image::make($fullPath);
    
    // Maak een thumbnail (150x150)
    $img->fit(150, 150);
    $thumbnailPath = str_replace('.jpg', '_thumb.jpg', $path);
    $img->save(storage_path('app/' . $thumbnailPath));
    
    // Maak een medium versie (400px breed)
    $img = Image::make($fullPath);
    $img->resize(400, null, function ($constraint) {
        $constraint->aspectRatio();
    });
    $mediumPath = str_replace('.jpg', '_medium.jpg', $path);
    $img->save(storage_path('app/' . $mediumPath));
    
    // Sla de paths op
    $project->image = $path;
    $project->image_thumbnail = $thumbnailPath;
    $project->image_medium = $mediumPath;
}
```

---
### 4- Verschillende resize methodes
Intervention Image heeft verschillende methodes voor het aanpassen van de grootte:

**resize()** - Verander grootte met behoud van verhouding
```php
$img->resize(300, 200); // Exact 300x200
$img->resize(300, null, function ($constraint) {
    $constraint->aspectRatio(); // Behoud verhouding
});
```

**fit()** - Crop en resize naar exacte afmetingen
```php
$img->fit(300, 200); // Crop naar 300x200
```

**widen()** - Verander alleen de breedte
```php
$img->widen(300); // Breedte 300px, hoogte automatisch
```

**heighten()** - Verander alleen de hoogte
```php
$img->heighten(200); // Hoogte 200px, breedte automatisch
```

---
### 5- Database migrations aanpassen (optioneel)
Als je meerdere versies opslaat, voeg dan extra kolommen toe:

```bash
php artisan make:migration add_image_versions_to_projects_table
```

In de migration:
```php
public function up()
{
    Schema::table('projects', function (Blueprint $table) {
        $table->string('image_thumbnail')->nullable();
        $table->string('image_medium')->nullable();
    });
}
```

Voer de migration uit:
```bash
php artisan migrate
```

---
### Optionele video:
{% include youtube.md video="Dyie1Yw9HzE" %}

### Links
- [Intervention Image - Resize](http://image.intervention.io/api/resize)
- [Intervention Image - Fit](http://image.intervention.io/api/fit)

Zorg dat je afbeeldingen automatisch verkleind worden na het uploaden.
{: .text-blue-100 .fs-4 }

---
{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }
[Afbeeldingen uitsnijden (crop)](image-crop)
