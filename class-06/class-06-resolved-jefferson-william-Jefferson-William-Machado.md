# MongoDB - Aula 06 - Exercício
Autor: Jefferson William Machado

## Fazer a query sem indíce para o campo 'name'
```
> db.pokemons.getIndexes()
[
  {
    "v" : 1,
    "key" : {
      "_id" : 1
    },
    "name" : "_id_",
    "ns" : "be-mean.pokemons"
  }
]
> db.pokemons.find({ name: "Beedrill" }).explain().millis
1
```

## Fazer a query com indíce para o campo 'name'
```
> db.pokemons.createIndex({ name: 1 })
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
      "name" : 1
    },
    "name" : "name_1",
    "ns" : "be-mean.pokemons"
  }
]
> db.pokemons.find({ name: "Beedrill" }).explain().millis
0
```

## Fazer a query sem indíce para dois campos juntos ("speed" e "types: poison")
```
> db.pokemons.find({ speed: 75, types: 'poison' }).explain().millis
1
```

## Fazer a query com indíce para dois campos juntos ("speed" e "types: poison")
```
> db.pokemons.createIndex({ speed: 1, type: 1 })
{
  "createdCollectionAutomatically" : false,
  "numIndexesBefore" : 2,
  "numIndexesAfter" : 3,
  "ok" : 1
}
> db.pokemons.find({ speed: 75, types: 'poison' }).explain().millis
0
```