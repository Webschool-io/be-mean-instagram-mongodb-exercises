# MongoDB - Aula 01 - Exercício
autor: Felipe Sousa

## Importando os restaurantes

```markdown
mongoimport --db be-mean -c restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
2015-11-16T23:28:28.228-0300 dropping: be-mean.restaurantes
2015-11-16T23:28:30.780-0300 check 9 25359
2015-11-16T23:28:31.199-0300 imported 25359 objects

```
## Contando os restaurantes

```
felipesousa(mongod-2.6.11) be-mean> db.restaurantes.find({}).count()
25359

```
