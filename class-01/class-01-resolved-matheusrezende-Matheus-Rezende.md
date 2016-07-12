## MongoDb - Aula 01
autor: Matheus Rezende Figueira

#### Exercício Importando os restaurantes
```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2016-05-18T09:27:06.398-0300	connected to: 127.0.0.1
2016-05-18T09:27:06.399-0300	dropping: be-mean.restaurantes
2016-05-18T09:27:08.080-0300	imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```
