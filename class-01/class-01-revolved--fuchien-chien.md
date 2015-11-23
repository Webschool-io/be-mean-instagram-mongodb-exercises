# MongoDB - Aula01 - Exericio

##Importando os restaurantes

```
chien@chien-Inspiron-5448:~$ mongoimport --db be-mean --collection restaurantes --file restaurantes.json
connected to: 127.0.0.1
Sat Nov 21 11:46:43.018 check 9 25359
Sat Nov 21 11:46:43.293 imported 25359 objects
```
##Contando os restaurantes

```
chien-Inspiron-5448(mongod-2.4.9) be-mean> db.restaurantes.find({}).count()
25359
```
