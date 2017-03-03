# MongoDB - Aula 01 - Exercício
autor: Judar R. Lima

## Importando os restaurantes;

```
    ➜  ~ mongoimport --db be-mean-instagram --collection restaurantes --drop --file Desktop/restaurantes.json
    2016-06-28T00:11:00.025-0300	connected to: localhost
    2016-06-28T00:11:00.027-0300	dropping: be-mean-instagram.restaurantes
    2016-06-28T00:11:00.914-0300	imported 25359 documents

```


## Contando os restaurantes;

```
    z10n(mongod-3.2.6) be-mean-instagram> db.restaurantes.find({}).count()
    25359
```
