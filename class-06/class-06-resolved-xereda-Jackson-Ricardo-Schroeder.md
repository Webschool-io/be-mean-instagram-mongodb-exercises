###MongoDB - Aula 06 - Exercício
Autor: Jackson Ricardo Schroeder

### ** (Utilizei a collection `restaurantes`, pois como a quantidade de documentos da `pokemons` é muita pequena, dessa forma a diferença de formance entre um campo com index ou sem index era imperceptível.)

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```js

  macminixereda(mongod-3.2.0) be-mean> var query = { name: "Panera Bread" };
  macminixereda(mongod-3.2.0) be-mean> db.restaurantes.find(query).explain('executionStats').executionStats.executionTimeMillis;
  14
  macminixereda(mongod-3.2.0) be-mean> db.restaurantes.find(query).explain('executionStats').executionStats.totalDocsExamined;
  25359

```

##2. Criar um `index` um para o campo `name`

```js

  macminixereda(mongod-3.2.0) be-mean> db.restaurantes.createIndex({ name: 1 });
  {
    "createdCollectionAutomatically": false,
    "numIndexesBefore": 1,
    "numIndexesAfter": 2,
    "ok": 1
  }

```

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```js
  macminixereda(mongod-3.2.0) be-mean> db.restaurantes.find(query).explain('executionStats').executionStats.executionTimeMillis;
  0
  macminixereda(mongod-3.2.0) be-mean> db.restaurantes.find(query).explain('executionStats').executionStats.totalDocsExamined;
  14
```

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```js

  macminixereda(mongod-3.2.0) be-mean> var query = { borough: "Bronx", cuisine: "American " };
  macminixereda(mongod-3.2.0) be-mean> db.restaurantes.find(query).explain('executionStats').executionStats.executionTimeMillis;
  14
  macminixereda(mongod-3.2.0) be-mean> db.restaurantes.find(query).explain('executionStats').executionStats.totalDocsExamined;
  25359

```

##5. Criar um `index` para esses dois campos juntos

```js

  macminixereda(mongod-3.2.0) be-mean> db.restaurantes.createIndex({ borough: 1, cuisine: 1 });
  {
    "createdCollectionAutomatically": false,
    "numIndexesBefore": 2,
    "numIndexesAfter": 3,
    "ok": 1
  }

```

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```js

  macminixereda(mongod-3.2.0) be-mean> db.restaurantes.find(query).explain('executionStats').executionStats.executionTimeMillis;
  2
  macminixereda(mongod-3.2.0) be-mean> db.restaurantes.find(query).explain('executionStats').executionStats.totalDocsExamined;
  411

```
