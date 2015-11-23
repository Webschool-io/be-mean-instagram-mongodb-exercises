# MongoDB - Aula 01 - Exercício
autor: Evandro Cavalcante Santos

## Importando os restaurantes

```

mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-15T22:28:25.352-0200	connected to: localhost
2015-11-15T22:28:25.353-0200	dropping: be-mean.restaurantes
2015-11-15T22:28:27.804-0200	[####################....] be-mean.restaurantes	9.8 MB/11.4 MB (86.2%)
2015-11-15T22:28:28.269-0200	imported 25359 documents

```

## Contando os restaurantes

```

Evandros-Mini(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359

```
