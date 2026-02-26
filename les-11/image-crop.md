---
title: Les 11
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Afbeeldingen uitsnijden (crop)
{: .text-green-100 .fs-6 }

Je gaat afbeeldingen uitsnijden naar een specifieke uitsnede of verhouding.

---
### 1- Basis crop functionaliteit
Met Intervention Image kun je afbeeldingen uitsnijden op verschillende manieren.  
Open je controller en zorg dat de Image facade geïmporteerd is:

```php
use Intervention\Image\Facades\Image;
```

---
### 2- Crop naar exacte afmetingen
Je kunt een afbeelding uitsnijden naar exacte afmetingen vanaf een specifieke positie:

```php
if (!empty($image)) {
    $path = $image->store('public/projecten');
    $fullPath = storage_path('app/' . $path);
    
    // Laad de afbeelding
    $img = Image::make($fullPath);
    
    // Crop 300x200 pixels vanaf positie (100, 50)
    $img->crop(300, 200, 100, 50);
    
    // Of crop vanaf het midden
    $img->crop(300, 200);
    
    $img->save($fullPath);
    $project->image = $path;
}
```

---
### 3- Crop naar vierkant (profielfoto's)
Voor profielfoto's wil je vaak een vierkante afbeelding:

```php
if (!empty($image)) {
    $path = $image->store('public/projecten');
    $fullPath = storage_path('app/' . $path);
    
    $img = Image::make($fullPath);
    
    // Bepaal de kleinste zijde
    $size = min($img->width(), $img->height());
    
    // Crop vierkant vanaf het midden
    $img->crop($size, $size);
    
    // Optioneel: resize naar gewenste grootte
    $img->resize(400, 400);
    
    $img->save($fullPath);
    $project->image = $path;
}
```

---
### 4- Crop met behoud van verhouding (fit)
De `fit()` methode combineert cropping en resizing:

```php
if (!empty($image)) {
    $path = $image->store('public/projecten');
    $fullPath = storage_path('app/' . $path);
    
    $img = Image::make($fullPath);
    
    // Crop en resize naar 800x600 (crop vanaf midden)
    $img->fit(800, 600);
    
    // Of met aangepaste positie
    $img->fit(800, 600, function ($constraint) {
        $constraint->upsize();
    }, 'top'); // Crop vanaf bovenkant
    
    $img->save($fullPath);
    $project->image = $path;
}
```

Beschikbare posities voor `fit()`:
- `top-left`, `top`, `top-right`
- `left`, `center` (standaard), `right`
- `bottom-left`, `bottom`, `bottom-right`

---
### 5- Crop met gebruiker input (geavanceerd)
Je kunt gebruikers ook zelf een uitsnede laten kiezen. Dit vereist extra inputs in je formulier:

**Formulier aanpassen:**
```html
<input type="hidden" name="crop_x" id="crop_x">
<input type="hidden" name="crop_y" id="crop_y">
<input type="hidden" name="crop_width" id="crop_width">
<input type="hidden" name="crop_height" id="crop_height">
```

**Controller verwerking:**
```php
if (!empty($image)) {
    $path = $image->store('public/projecten');
    $fullPath = storage_path('app/' . $path);
    
    $img = Image::make($fullPath);
    
    // Gebruik crop waarden van formulier
    if ($request->has('crop_x')) {
        $img->crop(
            $request->input('crop_width'),
            $request->input('crop_height'),
            $request->input('crop_x'),
            $request->input('crop_y')
        );
    }
    
    $img->save($fullPath);
    $project->image = $path;
}
```

**JavaScript (optioneel) - gebruik een library zoals Cropper.js:**
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/cropperjs/1.5.12/cropper.min.js"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/cropperjs/1.5.12/cropper.min.css">

<script>
const image = document.getElementById('image-preview');
const cropper = new Cropper(image, {
    aspectRatio: 16 / 9,
    crop(event) {
        document.getElementById('crop_x').value = event.detail.x;
        document.getElementById('crop_y').value = event.detail.y;
        document.getElementById('crop_width').value = event.detail.width;
        document.getElementById('crop_height').value = event.detail.height;
    }
});
</script>
```

---
### 6- Thumbnail met crop
Maak automatisch een vierkante thumbnail:

```php
if (!empty($image)) {
    $path = $image->store('public/projecten');
    $fullPath = storage_path('app/' . $path);
    
    // Maak thumbnail
    $img = Image::make($fullPath);
    $img->fit(200, 200); // Vierkante thumbnail
    
    // Bepaal bestandsextensie
    $pathInfo = pathinfo($path);
    $extension = $pathInfo['extension'];
    $filename = $pathInfo['filename'];
    $directory = $pathInfo['dirname'];
    $thumbnailPath = $directory . '/' . $filename . '_thumb.' . $extension;
    
    $img->save(storage_path('app/' . $thumbnailPath));
    
    $project->image = $path;
    $project->image_thumbnail = $thumbnailPath;
}
```

---
### Optionele video:
Er is geen specifieke video voor deze les.

### Links
- [Intervention Image - Crop](http://image.intervention.io/api/crop)
- [Intervention Image - Fit](http://image.intervention.io/api/fit)
- [Cropper.js library](https://fengyuanchen.github.io/cropperjs/)

Zorg dat je afbeeldingen kunt uitsnijden naar een specifieke grootte of verhouding.
{: .text-blue-100 .fs-4 }

---
{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }
[Kleuren aanpassen (filters)](image-color-adjustments)
