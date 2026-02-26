---
title: Les 11
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Intervention Image library installeren
{: .text-green-100 .fs-6 }

Je gaat de Intervention Image library installeren om afbeeldingen te kunnen bewerken.

---
### 1- Wat is Intervention Image?
Intervention Image is een populaire PHP library voor het bewerken van afbeeldingen.  
Met deze library kun je:
- Afbeeldingen verkleinen of vergroten
- Afbeeldingen uitsnijden (crop)
- Filters toepassen (zoals zwart-wit, contrast, helderheid)
- En nog veel meer...

De library ondersteunt zowel de GD library als ImageMagick.

---
### 2- Installeren via Composer
Open je terminal en navigeer naar je Laravel project folder.  
Voer het volgende commando uit om de library te installeren:

```bash
composer require intervention/image
```

Voor Laravel 10 gebruik je versie 2.x:
```bash
composer require intervention/image:^2.7
```

**Let op:** Versie 3.x vereist Laravel 11+ en PHP 8.1+.

---
### 3- Service Provider registreren
Voor Laravel 5.5+ (inclusief Laravel 10) wordt de service provider automatisch geregistreerd via package auto-discovery.  
Je hoeft dus normaal gesproken niets handmatig te configureren.

Als je een oudere Laravel versie gebruikt (< 5.5), voeg dan handmatig toe aan `config/app.php`:
```php
'providers' => [
    Intervention\Image\ImageServiceProvider::class,
],

'aliases' => [
    'Image' => Intervention\Image\Facades\Image::class,
],
```

---
### 4- Configuratie publiceren (optioneel)
Je kunt optioneel de configuratie publiceren:

```bash
php artisan vendor:publish --provider="Intervention\Image\ImageServiceProviderLaravelRecent"
```

Dit maakt een configuratiebestand aan in `config/image.php` waar je instellingen kunt aanpassen.

---
### 5- Test de installatie
Om te testen of de library correct is geïnstalleerd, kun je een simpele test doen in je controller:

```php
use Intervention\Image\Facades\Image;

// In je controller method:
$image = Image::make(public_path('test.jpg'));
dd($image->width(), $image->height());
```

---
### Geen optionele video
Er is geen video voor deze les.

### Links
- [Intervention Image documentatie](http://image.intervention.io/)
- [Intervention Image v3 documentatie](https://image.intervention.io/v3)
- [Laravel packages installeren](https://laravel.com/docs/10.x/packages)

Zorg dat de Intervention Image library correct is geïnstalleerd in je Laravel project.
{: .text-blue-100 .fs-4 }

---
{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }
[Afbeeldingen verkleinen en vergroten](image-resize)
