# MongoDB - Aula 01 - Exercício


## Importando os restaurantes

autor: Werner Eduard Gutschow

```
root@wernerlinux:/home/werner/Área de Trabalho#
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json.txt
2015-12-26T00:56:45.905-0200 connected to: localhost
2015-12-26T00:56:45.905-0200 dropping: be-mean.restaurantes
2015-12-26T00:56:45.905-0200 imported 25359 documents
```

## Contando os restaurantes

```
wernerlinux(mongod-3.0.8) be-mean> db.restaurantes.find({}).count()
25359
```
