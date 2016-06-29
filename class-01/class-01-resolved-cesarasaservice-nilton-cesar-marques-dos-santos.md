# MongoDB - Aula 01 - Exercício
autor: Cesar

## Importando os restaurantes

Antes de tudo, devemos levantar o server do MongoDB com o comando `mongod`.
Depois de levantado:

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2016-01-04T19:54:45.982-0300    connected to: 127.0.0.1
2016-01-04T19:54:45.982-0300    dropping: be-mean.restaurantes
2016-01-04T19:54:48.181-0300    imported 25359 documents
```

## Contando os restaurantes

Usando `mongo` para acessar o shell.

```
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359

```
