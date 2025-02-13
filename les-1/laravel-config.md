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
2. Als je Laravel hebt geïnitialiseerd via curl dan heb je een Sail setup en zijn de database instellingen al goed. 
3. Als je geïnstalleerd hebt via composer dan moet je de database instellingen doen door:
  - in het **.env** bestand de DB_xxx instellingen in te vullen op basis van je docker-compose.yml gegevens. 
4. Pas de **APP_NAME** constante ( bovenin ) de .env file in met de naam van jouw website.

---
### 2- Testen
Bekijk je project nu in de browser.   
1. Open Docker Desktop  
2. Klik dan op de port achter `NGINX` of `Laravel-...` container.   
3. In je browser zie je nu [http://localhost:88](http://localhost:88) of [http://localhost:89](http://localhost:89)  

---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Installeer Laravel Breeze starter kit](install-breeze)


