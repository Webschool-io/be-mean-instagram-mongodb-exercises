
# MongoDB   - aula 1 - exercicio
autor: Alexandre Evangelista de Souza

## Importando os restaurantes

***

```javascript

mongoimport --db bemean --collection restaurantes --drop --type json --file restaurantes.json 

2016-07-15T19:26:50.640-0300    connected to: localhost
2016-07-15T19:26:50.641-0300    dropping: bemean.restaurantes
2016-07-15T19:26:53.196-0300    imported 25359 documents

```

***

## Contando os restaurantes

```javascript

db.restaurantes.find({}).count()
25359

```

