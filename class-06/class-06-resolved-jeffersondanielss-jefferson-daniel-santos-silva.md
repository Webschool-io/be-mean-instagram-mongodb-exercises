# MongoDB - Aula 06 - Exercício
autor: Jefferson Daniel (https://github.com/jeffersondanielss)

# 1. Index para o campo name
```
  > db.pokemons.find({ name: "Pikachu" }).explain('executionStats').executionStats.totalDocsExamined
  1
  > db.pokemons.find({ name: "Pikachu" }).explain('executionStats').executionStats.executionTimeMillis
  610

  > db.pokemons.createIndex({ name: 1 })
  {
    "createdCollectionAutomatically" : false,
    "numIndexesBefore" : 1,
    "numIndexesAfter" : 2,
    "ok" : 1
  }

  > db.pokemons.find({ name: "Pikachu" }).explain('executionStats').executionStats.executionTimeMillis
  0

  > db.pokemons.find({ name: "Pikachu" }).explain('executionStats').executionStats.totalDocsExamined
  l

  > db.pokemons.dropIndex( {name: 1 })
```


# 2. Index para dois campos juntos

```
  > db.pokemons.find( { name: "Pikachu", defense: { $gte: 40 } } ).explain('executionStats').executionStats.executionTimeMillis
  1

  > db.pokemons.find( { name: "Pikachu", defense: { $gte: 40 } } ).explain('executionStats').executionStats.totalDocsExamined
  610

  > db.pokemons.createIndex({ name: 1, defense: 1 })
  {
    "createdCollectionAutomatically" : false,
    "numIndexesBefore" : 1,
    "numIndexesAfter" : 2,
    "ok" : 1
  }

  > db.pokemons.getIndexes()
  [
    {
      "v" : 1,
      "key" : {
              "_id" : 1
      },
      "name" : "_id_",
      "ns" : "be-mean.pokemons"
    },
    {
      "v" : 1,
      "key" : {
        "name" : 1,
        "defense" : 1
      },
      "name" : "name_1_defense_1",
      "ns" : "be-mean.pokemons"
    }
  ]

  > db.pokemons.find( { name: "Pikachu", defense: { $gte: 40 } } ).explain('executionStats').executionStats.executionTimeMillis
  0

  > db.pokemons.find( { name: "Pikachu", defense: { $gte: 40 } } ).explain('executionStats').executionStats.totalDocsExamined
  1
```