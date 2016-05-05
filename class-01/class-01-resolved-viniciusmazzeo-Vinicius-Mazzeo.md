# MongoDb - Aula 01 - Exercício
autor Vinicius Mazzeo

## Importando os restaurantes

```

mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json 
2016-01-28T21:18:24.161-0200	connected to: 127.0.0.1
2016-01-28T21:18:24.162-0200	dropping: be-mean.restaurantes
2016-01-28T21:18:25.906-0200	imported 25359 documents

```

## Contando os restaurantes

```

db.restaurantes.find({}).count()
25359

```