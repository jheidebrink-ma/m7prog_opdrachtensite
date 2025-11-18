---
title: Les 1
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Deze setup is voor Windows gebruikers die niet door de vorige stappen heen zijn gekomen.  

# wsl setup
open je wsl _(wij gebruiken Ubuntu als distro)_  
`wsl -d Ubuntu`  
je ziet nu dat je in een mnt directory zit:  
![](img/mnt.PNG)

ga naar je home  
`cd ~`  

maak een directory voor je laravel development  
`mkdir laradev`  
Ga naar de directory  
`cd laradev`  

![](img/initcmd.PNG)


## laravel project opzetten
maak een nieuw project (type of kopieer):  
`curl -s https://laravel.build/m7prog-laravel | bash`  
_HINT m7prog-laravel kan je veranderen als je andere projecten start_  
Als het goed is heb je een wachtwoord voor je android (zo niet zie de `wsl change pw.md` )  
type die zodra die [sudo] password... vraagt  
![](img/sudoandroid.PNG)


## sail up
ga naar je project dir:  
![](img/naarproject.PNG)  
dat is nu m7prog-laravel  

type nu `vendor/bin/sail up`  

nu zie je:  
![](img/sailup.PNG)


## controle
nu draait je docker, check of je dit hebt:  
![](img/docker.PNG)  

## breeze npm etc  
open je exec van je laravel docker container:  
![](img/dockerterm.PNG)  
    
### installeer breeze:
composer require laravel/breeze --dev  
`php artisan breeze:install`  
`php artisan migrate`  

### installeer via npm:
`npm install`

### test:
`npm run dev`  
je ziet:  
![](img/nodeup.PNG)  
    
Open je browser je ziet nu laravel met breeze  
![](img/laralocal.PNG)

## Files in visual studio code
Al onze files staan nu in het linux file system van wsl hoe komen we daar bij?
Open de file explorer (van windows)
in de adres balk type je:
`\\wsl.localhost\Ubuntu\home\android`

Daar staat onze directory  
![](img/laradev.PNG)  
1. Open de `Laradev` directory in **visual studio code** 
2. Nu kan je beginnen met coderen!