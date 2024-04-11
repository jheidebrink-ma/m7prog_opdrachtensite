---
title: Les 7
layout: page
permalink: :path/:basename
nav_exclude: true
---

## Overzicht: Forms en validatie
{: .text-green-100 .fs-6 }

In deze les en de volgende les leer je hoe je formulieren kunt maken waar bezoekers (of jij zelf) gegevens mee kunnen invoeren en opsturen.
Jij als developer kunt de gegevens vervolgens in een controller gaan verwerken.

In de opdracht-video's zie je hoe je een simpel CMS kunt maken onder de url `/dashboard` op je website en hoe je formulieren en CRUD operaties (Create, Read, Update en Delete) kunt gebruiken om de gegevens in je database te beheren.

Een aantal dingen zijn belangrijk hierbij:

- Beveiliging: Zorg dat een script je form niet gaat spammen.
- Authenticatie: Zorg dat je alleen iets mag bewerken/toevoegen als je ingelogd bent als *admin* gebruiker.
- Validatie: De ingevoerde gegevens controleren en valideren.
- Foutmeldingen tonen bij formulier velden die niet correct zijn ingevuld.

---

### Optionele video:
Kijk de video voor een overzicht van wat je aan het einde van de opdrachten (ongeveer) werkend kan hebben.

{% include youtube.md video="7fb_Xfb5VAU" %}

---

In de volgende opdrachten ga je zelf een formulier maken, validatie regels toevoegen en foutmeldingen tonen.
Daarna kun je de gegevens via je Model class makkelijk toevoegen aan de database
{: .text-blue-100 .fs-4 }

---
### Volgende stap:
{: .text-green-100 .fs-4 }  
[Route groep maken voor admin routes - dashboard layout](admin-dashboard)
