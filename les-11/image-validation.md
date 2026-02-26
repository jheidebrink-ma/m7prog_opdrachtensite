---
title: Les 11
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Image upload validatie - JPG en PNG
{: .text-green-100 .fs-6 }

Je gaat de file upload valideren zodat alleen JPG en PNG bestanden geüpload kunnen worden.

---
### 1- Validatie toevoegen aan het formulier
In de vorige les heb je al een file upload veld toegevoegd aan je formulier.  
Nu ga je ervoor zorgen dat alleen afbeeldingen van het type JPG en PNG geüpload kunnen worden.

Open je controller, bijvoorbeeld:
```php
app/Http/Controllers/ProjectAdminController.php
```

---
### 2- Validatie regels toevoegen
In je `store` en `update` methodes kun je validatie regels toevoegen voor het image veld.  
Voeg de volgende validatie regel toe:

```php
$request->validate([
    'plaatje' => 'nullable|image|mimes:jpeg,jpg,png|max:2048',
    // andere validatie regels...
]);
```

**Uitleg van de validatie regels:**
- `nullable` - Het veld is optioneel
- `image` - Het bestand moet een afbeelding zijn
- `mimes:jpeg,jpg,png` - Alleen JPEG, JPG en PNG bestanden zijn toegestaan
- `max:2048` - Maximale bestandsgrootte is 2MB (2048 KB)

---
### 3- Foutmeldingen weergeven
Zorg ervoor dat je in je formulier de foutmeldingen weergeeft:

```php
{% raw %}@error('plaatje')
    <div class="alert alert-danger">{{ $message }}</div>
@enderror{% endraw %}
```

---
### 4- Test je validatie
Probeer nu verschillende bestandstypes te uploaden:
- Een JPG bestand (moet werken)
- Een PNG bestand (moet werken)
- Een GIF bestand (moet een foutmelding geven)
- Een PDF bestand (moet een foutmelding geven)
- Een te groot bestand (moet een foutmelding geven)

---
### Optionele video:
{% include youtube.md video="AaJLsFd2mfc" %}

### Links
- [Validation in Laravel](https://laravel.com/docs/10.x/validation#available-validation-rules)
- [File validation rules](https://laravel.com/docs/10.x/validation#rule-file)

Zorg dat je validatie werkt en dat alleen JPG en PNG bestanden geüpload kunnen worden.
{: .text-blue-100 .fs-4 }

---
{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }
[Intervention Image library installeren](image-library-setup)
