# MongoDB - Aula 01 - Exercício
autor: Uilian Nunes Coelho

## Importando os restaurantes

```
MacBook-Pro-de-Uilian-Nunes:Be_Mean Uilian$ mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2015-11-11T23:52:48.721-0200    connected to: 127.0.0.1
2015-11-11T23:52:48.722-0200    dropping: be-mean.restaurantes
2015-11-11T23:52:51.712-0200    [####################....] be-mean.restaurantes 9.8 MB/11.3 MB (86.3%)
2015-11-11T23:52:52.397-0200    imported 25359 documents

```

## Contando os restaurantes

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean> db.restaurantes.find({}).count()
25359

```