---
title: Les 2
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Debug bar implementeren 
{: .text-green-100 .fs-6 }

Met de debug bar voor Laravel kun je controleren wat er goed of niet goed gaat in je project.  
Stap voor stap uitleg kun je hier vinden:  
[https://github.com/barryvdh/laravel-debugbar](https://github.com/barryvdh/laravel-debugbar)

---
### 1- Installatie
1. Login op de laravel.test of php docker container zodat je geen problemen hebt met php en composer. Hierin heb je namelijk al een werkende composer installatie.
    - Open hiervoor docker-desktop en zoek de juiste php container op
    - Klik op de drie puntjes achter de naam en daarna op **open terminal**
2. Controleer of je op de juiste container zit met het volgende commando: ```php -v```
	- Krijg je een error dan heb je niet de php container geopend, probeer het nog maar een keertje maar dan nu met de correcte container.
3. Installeer de debug bar via composer: <br>
	```composer require barryvdh/laravel-debugbar --dev```
4. Om de debug bar `aan` of `uit` te zetten kun je in de **.env** file aangeven of je applicatie in debug mode zit: ```APP_DEBUG=true```
5. _Optioneel:_ Mogelijk laad het systeem niet automatisch de debug bar, daarom moet je in de  
	`providers array` in de `config/app.php` aangeven dat de debug bar geladen moet worden.   
	Voeg daar deze regel toe:  
   ```Barryvdh\Debugbar\ServiceProvider::class,```
   Als je binnen laravel gebruik wilt maken van de debug functie om bijvoorbeeld een debug regel weer te geven dan moet je in de
   **config/app.php** de volgende regel aan het **facades** onderdeel toevoegen:  
   `'Debugbar' => Barryvdh\Debugbar\Facades\Debugbar::class,`

---
### 2- Controle
Als je nu in de browser naar je project gaat dan zie je onderaan het Laravel logo.  
Daarnaast vind je een aantal elementen, bijvoorbeeld welke views en route er momenteel geladen worden.


---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Installeer Tailwind CSS](tailwind)


