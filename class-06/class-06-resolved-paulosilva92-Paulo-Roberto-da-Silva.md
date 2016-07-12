# MongoDB - Aula 06 - Exercício
User: paulosilva92
Autor: Paulo Roberto da Silva

# Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca.

```js
paulo(mongod-3.2.1) be-mean-class5> db.pokemons.find({name:/pikachu/i}).explain();
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-class5.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": /pikachu/i
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /pikachu/i
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "serverInfo": {
    "host": "paulo",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}

```

# Criar um `index` um para o campo `name`.

```js
paulo(mongod-3.2.1) be-mean-class5> db.pokemons.createIndex({name : 1});
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

# Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.

```js
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-class5.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": /pikachu/i
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "filter": {
          "name": /pikachu/i
        },
        "keyPattern": {
          "name": 1
        },
        "indexName": "name_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"\", {})",
            "[/pikachu/i, /pikachu/i]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "serverInfo": {
    "host": "paulo",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```

# Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.
```js
paulo(mongod-3.2.1) be-mean-class5> db.pokemons.find(query).explain();
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-class5.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$gte": 50
          }
        },
        {
          "defense": {
            "$gte": 40
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "attack": {
              "$gte": 50
            }
          },
          {
            "defense": {
              "$gte": 40
            }
          }
        ]
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "serverInfo": {
    "host": "paulo",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```

# Criar um `index` para esses dois campos juntos.
```js
paulo(mongod-3.2.1) be-mean-class5> db.pokemons.createIndex({attack :1}, {defense : 1});
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

# Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.
```js
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-class5.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$gte": 50
          }
        },
        {
          "defense": {
            "$gte": 40
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "filter": {
        "defense": {
          "$gte": 40
        }
      },
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "attack": 1
        },
        "indexName": "attack_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "attack": [
            "[50.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "serverInfo": {
    "host": "paulo",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```
