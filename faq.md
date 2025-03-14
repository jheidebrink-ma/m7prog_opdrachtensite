---
layout: home
title: FAQ
nav_order: 1
---

# FAQ

---
### Waar staat mijn project
Open jouw IDE, _bv Visual Code_  
Selecteer ```open folder```
Navigeer jouw project.  
Start Docker in de terminal
```shell
docker-compose up -d
```

---
### Docker start niet
Start project vanuit je editor.  
Open je Terminal scherm en voer dit commando uit:  
```shell
docker-compose up -d
```

---
### Docker start nog steeds
Lees goed de foutmelding in de terminal.  
Zit je echt in de goede folder of heb je de `doker-compose.yml` in een sub folder staan.  
Open in dat geval de subfolder.


--- 
### Waar vind ik phpmyadmin?
Plaats de onderstaande code in je docker-compose.yml:
```dockerfile
    phpmyadmin:
        image: phpmyadmin:latest
        ports:
          - 888:80
        environment:
          PMA_HOST: '${DB_HOST}'
          PMA_USER: '${DB_USERNAME}'
          PMA_PASSWORD: '${DB_PASSWORD}'
```
