# MongoDB - Aula 01 - Exercício
Autor: Daniel Mota

## Importando os restaurantes
```
$ mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2017-07-26T15:32:26.964-0300	connected to: 127.0.0.1
2017-07-26T15:32:26.966-0300	dropping: be-mean.restaurantes
2017-07-26T15:32:27.442-0300	imported 25359 documents
```
## Contando os restaurantes
```
db.restaurantes.find({}).count()
25359

```