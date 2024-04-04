---
title: Les 3
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Tailwind configuratie aanpassen
{: .text-green-100 .fs-6 }

[Tailwind CSS](https://tailwindcss.com/docs/installation) kun je helemaal customizen met je eigen kleuren, stijlen, lettertypen en andere zaken.
Dit doe je in het bestand `tailwind.config.js` dat in de root van je Laravel project staat.
Als je Les 1 hebt gemaakt en Laravel Breeze hebt geïnstalleerd staat hier al wat configuratie in.


---
### 1- Configuratie
Zorg dat de je minimaal 2 elementen aanpast op je website, denk hierbij aan de achtergrond kleur of een ander font.  
Je kunt alle onderdelen van het default theme *extenden* (uitbreiden) of onderdelen helemaal opnieuw instellen (zoals de kleuren, lettertypen e.d.)

Hier vind je de documentatie van de Tailwind configuratie:  
- [https://tailwindcss.com/docs/configuration#configuration-options](https://tailwindcss.com/docs/configuration#configuration-options)
- En hier [het basis Tailwind configuratie bestand](https://unpkg.com/browse/tailwindcss@3.0.24/stubs/defaultConfig.stub.js) met ALLES wat je kunt aanpassen of overschrijven.


---
### 2- Watcher
Tailwind werkt anders dan bijvoorbeeld bootstrap. 
Tailwind kijkt naar jouw view bestanden ( templates ) om te zien welke styles en andere codes jij gebruikt in je bestanden. Alleen noodzakelijke css wordt gecompiled. 
Zo blijft de grote van je css minimaal.   
Hiervoor moet je wel in een terminal scherm npm watch open laten staan.
Open terminal scherm en voer dit commando uit:
```shell
npm run dev
```
Pas maar ergens de achtergrond aan door bijvoorbeeld de background aan te passen.  
Dit doe je door een class toe te voegen of aan te passen. 
```html {% raw %}
    <main class="bg-red-500">
    {% endraw %}
```

---

{% include commit_push.md %}

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Overview: wat zijn routes en controllers?](routes)


