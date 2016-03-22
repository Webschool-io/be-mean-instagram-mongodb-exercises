###MongoDB - Aula 01 - Exercício
Autor: Willian Dutras

##Importando os restaurantes
```
sushi@canalsushi:~/github/estudos/be-mean/mongodb/aula01$ mongoimport --db be-mean-instagram --collection restaurantes --file restaurantes.json
2015-11-15T18:35:54.486-0200	connected to: localhost
2015-11-15T18:35:56.532-0200	imported 25359 documents
```

##Contanto os restaurantes
```
> db.restaurantes.find({}).count()
25359
```
