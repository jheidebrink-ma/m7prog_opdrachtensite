---
title: Les 1
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Configuratie instellen
{: .text-green-100 .fs-6 }

Je gaat een nu je project instellen met de noodzakelijke gegevens.

---
### 1- Laravel project configureren
1. Configureer je Laravel project door de `.env` file aan te passen als dit noodzakelijk is.
2. Als je Laravel hebt geïnitialiseerd via curl dan heb je een **Sail / Curl** setup en zijn de database instellingen al goed. 
3. Als je geïnstalleerd hebt via **composer** dan moet je de database instellingen doen door:  
  - in het **.env** bestand de DB_xxx instellingen in te vullen op basis van je docker-compose.yml gegevens. 
4. Pas de **APP_NAME** constante ( bovenin ) de .env file in met de naam van jouw website, hier mogen geen spaties en speciale tekens in voorkomen.

---
### 2- Testen
Bekijk je project nu in de browser.   
1. Open Docker Desktop  
2. Klik dan op de port achter `NGINX` of `Laravel-...` container.   
3. In je browser zie je nu [http://localhost](http://localhost)  

---
### 2- Editen van bestanden

#### 1- OSX
Om dit project te bewerken op een Apple _(OSX)_ kun je de folder met het project openen in jouw editor.  
Het resultaat kun je zien in de browser.

#### 2- Windows
Een Windows computer geeft bestand stuk voor stuk door aan de Docker omgevingen via een Linux laag waardoor dit veel vertraging oplevert.   
Al onze files staan nu in het linux file system van wsl hoe komen we daar bij?
1. Open de file explorer (van windows)
2. In de adres balk type je: `\\wsl.localhost\Ubuntu\home\android`
3. Daar staat onze directory  ![](img/laradev.PNG)
4. Open de `Laradev` directory in **visual studio code**
5. Nu kan je beginnen met coderen!


---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Installeer Laravel Breeze starter kit](install-breeze)


