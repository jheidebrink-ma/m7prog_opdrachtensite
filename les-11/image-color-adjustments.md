---
title: Les 11
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Kleuren aanpassen (filters)
{: .text-green-100 .fs-6 }

Je gaat filters toepassen op afbeeldingen om kleuren, contrast en helderheid aan te passen.

---
### 1- Basis kleur aanpassingen
Met Intervention Image kun je verschillende kleur aanpassingen toepassen op afbeeldingen.  
Open je controller en zorg dat de Image facade geïmporteerd is:

```php
use Intervention\Image\Facades\Image;
```

---
### 2- Helderheid aanpassen
Je kunt de helderheid van een afbeelding verhogen of verlagen:

```php
if (!empty($image)) {
    $path = $image->store('public/projecten');
    $fullPath = storage_path('app/' . $path);
    
    $img = Image::make($fullPath);
    
    // Helderheid verhogen (+50)
    $img->brightness(50);
    
    // Of verlagen (-30)
    // $img->brightness(-30);
    
    $img->save($fullPath);
    $project->image = $path;
}
```

Waarde range: -100 (donkerder) tot +100 (lichter)

---
### 3- Contrast aanpassen
Verhoog of verlaag het contrast van een afbeelding:

```php
if (!empty($image)) {
    $path = $image->store('public/projecten');
    $fullPath = storage_path('app/' . $path);
    
    $img = Image::make($fullPath);
    
    // Contrast verhogen (+40)
    $img->contrast(40);
    
    // Of verlagen (-20)
    // $img->contrast(-20);
    
    $img->save($fullPath);
    $project->image = $path;
}
```

Waarde range: -100 tot +100

---
### 4- Grijstinten (greyscale)
Converteer een kleurenafbeelding naar zwart-wit:

```php
if (!empty($image)) {
    $path = $image->store('public/projecten');
    $fullPath = storage_path('app/' . $path);
    
    $img = Image::make($fullPath);
    
    // Converteer naar grijstinten
    $img->greyscale();
    
    $img->save($fullPath);
    $project->image = $path;
}
```

---
### 5- Kleuren omkeren (invert)
Inverteer alle kleuren in de afbeelding:

```php
$img->invert();
```

---
### 6- Pixelate effect
Voeg een pixelate effect toe:

```php
$img->pixelate(10); // 10 = grootte van pixels
```

---
### 7- Blur effect
Maak de afbeelding wazig:

```php
$img->blur(15); // 15 = blur sterkte (0-100)
```

---
### 8- Gamma correctie
Pas gamma correctie toe:

```php
$img->gamma(1.6); // >1 = lichter, <1 = donkerder
```

---
### 9- Kleurtint toevoegen (colorize)
Voeg een kleurtint toe aan de afbeelding:

```php
// Voeg een rode tint toe
$img->colorize(100, 0, 0); // RGB waarden: -100 tot +100

// Sepia effect (bruine tint)
$img->greyscale();
$img->colorize(50, 25, 0);

// Blauw/koele tint
$img->colorize(0, 0, 50);
```

---
### 10- Meerdere filters combineren
Je kunt meerdere filters na elkaar toepassen:

```php
if (!empty($image)) {
    $path = $image->store('public/projecten');
    $fullPath = storage_path('app/' . $path);
    
    $img = Image::make($fullPath);
    
    // Combineer meerdere aanpassingen
    $img->brightness(10)      // Iets lichter
        ->contrast(15)         // Meer contrast
        ->sharpen(10);         // Scherper
    
    $img->save($fullPath);
    $project->image = $path;
}
```

---
### 11- Filter selectie via formulier
Je kunt gebruikers een filter laten kiezen via het formulier:

**Formulier aanpassen:**
```html
<select name="image_filter" class="form-control">
    <option value="none">Geen filter</option>
    <option value="greyscale">Zwart-wit</option>
    <option value="sepia">Sepia</option>
    <option value="bright">Extra helder</option>
    <option value="dark">Donker</option>
    <option value="high_contrast">Hoog contrast</option>
</select>
```

**Controller verwerking:**
```php
if (!empty($image)) {
    $path = $image->store('public/projecten');
    $fullPath = storage_path('app/' . $path);
    
    $img = Image::make($fullPath);
    
    // Pas filter toe op basis van selectie
    $filter = $request->input('image_filter', 'none');
    
    switch($filter) {
        case 'greyscale':
            $img->greyscale();
            break;
        case 'sepia':
            $img->greyscale();
            $img->colorize(50, 25, 0);
            break;
        case 'bright':
            $img->brightness(30);
            break;
        case 'dark':
            $img->brightness(-30);
            break;
        case 'high_contrast':
            $img->contrast(50);
            break;
    }
    
    $img->save($fullPath);
    $project->image = $path;
}
```

---
### 12- Preset filters maken
Maak handige preset filters:

```php
private function applyVintageFilter($img)
{
    $img->brightness(-10)
        ->contrast(5)
        ->greyscale()
        ->colorize(40, 20, -10);
    return $img;
}

private function applyModernFilter($img)
{
    $img->brightness(5)
        ->contrast(20)
        ->sharpen(5);
    return $img;
}

// Gebruik in je store/update method:
if (!empty($image)) {
    $path = $image->store('public/projecten');
    $fullPath = storage_path('app/' . $path);
    
    $img = Image::make($fullPath);
    
    // Pas preset toe
    $img = $this->applyVintageFilter($img);
    
    $img->save($fullPath);
    $project->image = $path;
}
```

---
### 13- Overzicht van beschikbare filters
Alle beschikbare kleur aanpassingen in Intervention Image:

- `brightness($level)` - Helderheid (-100 tot 100)
- `contrast($level)` - Contrast (-100 tot 100)
- `greyscale()` - Grijstinten
- `invert()` - Kleuren omkeren
- `pixelate($size)` - Pixelate effect
- `blur($amount)` - Blur effect (0-100)
- `gamma($correction)` - Gamma correctie
- `colorize($red, $green, $blue)` - Kleurtint (-100 tot 100 per kanaal)
- `sharpen($amount)` - Verscherpen (0-100)

---
### Optionele video:
Er is geen specifieke video voor deze les.

### Links
- [Intervention Image - Filters](http://image.intervention.io/api/filter)
- [Intervention Image - Adjustments](http://image.intervention.io/use/effects)

Zorg dat je verschillende kleur filters kunt toepassen op je afbeeldingen.
{: .text-blue-100 .fs-4 }

---
{% include commit_push.md %}

---
### Je bent klaar met les 11!
{: .text-green-100 .fs-4 }

Je hebt nu geleerd hoe je:
- JPG en PNG bestanden kunt uploaden met validatie
- De Intervention Image library kunt gebruiken
- Afbeeldingen kunt verkleinen en vergroten
- Afbeeldingen kunt uitsnijden
- Kleur filters kunt toepassen

Met deze kennis kun je een professionele image upload en bewerkings functionaliteit bouwen in je Laravel applicatie!
