# MongoDB - Aula 01 - Exercício
autor: Luã Mota

## Importando os restaurantes

```
mocallu-svf-elementary(mongod-3.0.7) mongoimport --db 'be-mean' --collection restaurantes --drop --file restaurantes.json
2015-11-15T04:10:06.489-0200	connected to: localhost
2015-11-15T04:10:06.489-0200	dropping: be-mean.restaurantes
2015-11-15T04:10:09.486-0200	[########################] be-mean.restaurantes	11.4 MB/11.4 MB (100.0%)
2015-11-15T04:10:09.606-0200	imported 25359 documents

```

## Contando os restaurantes

```
mocallu-svf-elementary(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359

```
