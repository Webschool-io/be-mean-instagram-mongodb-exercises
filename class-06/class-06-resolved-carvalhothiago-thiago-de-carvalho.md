# MongoDB - Aula 06 - Exercício
User: [carvalhothiago](https://github.com/carvalhothiago)
Autor: Thiago de Carvalho

# Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca.
```
megazord(mongod-3.2.4) be-mean> db.pokemons.find({name: "Charmander"}).explain()
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Charmander"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Charmander"
        }
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "serverInfo": {
    "host": "megazord",
    "port": 27017,
    "version": "3.2.4",
    "gitVersion": "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
  },
  "ok": 1
}
```

# Criar um `index` um para o campo `name`.
```
megazord(mongod-3.2.4) be-mean> db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

# Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.
```
megazord(mongod-3.2.4) be-mean> db.pokemons.find({name: "Charmander"}).explain()
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Charmander"
      }
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
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
            "[\"Charmander\", \"Charmander\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "serverInfo": {
    "host": "megazord",
    "port": 27017,
    "version": "3.2.4",
    "gitVersion": "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
  },
  "ok": 1
}

```

# Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.
```
megazord(mongod-3.2.4) be-mean> var query = { $and: [{ attack: { $gte: 48 }}, {speed: { $gte: 2 } } ] }
megazord(mongod-3.2.4) be-mean> db.pokemons.find(query).explain()
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$gte": 48
          }
        },
        {
          "speed": {
            "$gte": 2
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
              "$gte": 48
            }
          },
          {
            "speed": {
              "$gte": 2
            }
          }
        ]
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "serverInfo": {
    "host": "megazord",
    "port": 27017,
    "version": "3.2.4",
    "gitVersion": "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
  },
  "ok": 1
}

```

# Criar um `index` para esses dois campos juntos.
```
megazord(mongod-3.2.4) be-mean> db.pokemons.createIndex({ attack: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

megazord(mongod-3.2.4) be-mean> db.pokemons.createIndex({ speed: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 3,
  "numIndexesAfter": 4,
  "ok": 1
}
```

# Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.
```
megazord(mongod-3.2.4) be-mean> var query = { $and: [{ attack: { $gte: 48 }}, {speed: { $gte: 2 } } ] }
megazord(mongod-3.2.4) be-mean> db.pokemons.find(query).explain()
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$gte": 48
          }
        },
        {
          "speed": {
            "$gte": 2
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "filter": {
        "speed": {
          "$gte": 2
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
            "[48.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [
      {
        "stage": "FETCH",
        "filter": {
          "attack": {
            "$gte": 48
          }
        },
        "inputStage": {
          "stage": "IXSCAN",
          "keyPattern": {
            "speed": 1
          },
          "indexName": "speed_1",
          "isMultiKey": false,
          "isUnique": false,
          "isSparse": false,
          "isPartial": false,
          "indexVersion": 1,
          "direction": "forward",
          "indexBounds": {
            "speed": [
              "[2.0, inf.0]"
            ]
          }
        }
      }
    ]
  },
  "serverInfo": {
    "host": "megazord",
    "port": 27017,
    "version": "3.2.4",
    "gitVersion": "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
  },
  "ok": 1
}
```
