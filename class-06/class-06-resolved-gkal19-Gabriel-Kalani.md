#MongoDB - Aula 06 - Exercício
autor: Gabriel Kalani


1 - Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```js
  be-mean-pokemons> db.restaurantes.find({"name": "Glorious Food"}).explain('executionStats')
{
  "cursor": "BasicCursor",
  "isMultiKey": false,
  "n": 0,
  "nscannedObjects": 0,
  "nscanned": 0,
  "nscannedObjectsAllPlans": 0,
  "nscannedAllPlans": 0,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 0,
  "nChunkSkips": 0,
  "millis": 16,
  "allPlans": [
    {
      "cursor": "BasicCursor",
      "n": 0,
      "nscannedObjects": 0,
      "nscanned": 0
    }
  ],
  "server": "gkal19-aula-bemean-2468380:27017"
}
```

2 - Criar um `index` um para o campo `name`

```js
  be-mean-pokemons>db.restaurantes.createIndex({name: 1})
  {
    "createdCollectionAutomatically": false,
    "numIndexesBefore": 1,
    "numIndexesAfter": 2,
    "ok": 1
  }
```

3 - Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```js
  be-mean-pokemons> db.restaurantes.find({"name": "Glorious Food"}).explain('executionStats')
  {
    "cursor": "BasicCursor",
    "isMultiKey": false,
    "n": 0,
    "nscannedObjects": 0,
    "nscanned": 0,
    "nscannedObjectsAllPlans": 0,
    "nscannedAllPlans": 0,
    "scanAndOrder": false,
    "indexOnly": false,
    "nYields": 0,
    "nChunkSkips": 0,
    "millis": 0,
    "allPlans": [
      {
        "cursor": "BasicCursor",
        "n": 0,
        "nscannedObjects": 0,
        "nscanned": 0
      }
    ],
    "server": "gkal19-aula-bemean-2468380:27017"
  }
```

4 - Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```js
  be-mean-pokemons> var query = {$and:[{borough: 'Queens'},{cuisine: 'Jewish/Kosher'}]}
  be-mean-pokemons> db.restaurantes.find(query).explain('executionStats')
  {
    "cursor": "BasicCursor",
    "isMultiKey": false,
    "n": 0,
    "nscannedObjects": 0,
    "nscanned": 0,
    "nscannedObjectsAllPlans": 0,
    "nscannedAllPlans": 0,
    "scanAndOrder": false,
    "indexOnly": false,
    "nYields": 0,
    "nChunkSkips": 0,
    "millis": 1,
    "allPlans": [
      {
        "cursor": "BasicCursor",
        "n": 0,
        "nscannedObjects": 0,
        "nscanned": 0
      }
    ],
    "server": "gkal19-aula-bemean-2468380:27017"
  }
```

5 - Criar um `index` para esses dois campos juntos

```js
  be-mean-pokemons > db.restaurantes.createIndex({borough: 1, cuisine: 1})
{
  "createdCollectionAutomatically": true,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

6 - Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca
```js
  db.restaurantes.find(query).explain('executionStats')
  {
    "cursor": "BasicCursor",
    "isMultiKey": false,
    "n": 62,
    "nscannedObjects": 25359,
    "nscanned": 25359,
    "nscannedObjectsAllPlans": 25359,
    "nscannedAllPlans": 25359,
    "scanAndOrder": false,
    "indexOnly": false,
    "nYields": 200,
    "nChunkSkips": 0,
    "millis": 112,
    "allPlans": [
      {
        "cursor": "BasicCursor",
        "isMultiKey": false,
        "n": 62,
        "nscannedObjects": 25359,
        "nscanned": 25359,
        "scanAndOrder": false,
        "indexOnly": false,
        "nChunkSkips": 0
      }
    ],
    "server": "gkal19-aula-bemean-2468380:27017",
    "filterSet": false,
    "stats": {
      "type": "COLLSCAN",
      "works": 25364,
      "yields": 200,
      "unyields": 200,
      "invalidates": 0,
      "advanced": 62,
      "needTime": 25298,
      "needFetch": 0,
      "isEOF": 1,
      "docsTested": 25359,
      "children": [ ]
    }
  }
```
