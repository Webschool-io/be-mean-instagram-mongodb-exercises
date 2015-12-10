# MongoDB - Aula 02 - Exercício
Author: Wladek Zacharski

## Criar Database
```
>use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listando Databases 
```
> show dbs
be-mean  0.078GB
local    0.078GB

```

## Listando Collections
```
> show collections
```

## Cadastrando Pokemons
```
var regPokemons = [
    {name: "Bulbasaur", description: "seed pokemon", attack: 49, defense: 49, heigth: 7.0}, 
    {name: "Ivysaur", description: "seed pokemon", attack: 62, defense: 63, heigth: 10.0}, 
    {name: "Venusaur", description: "seed pokemon", attack: 82, defense: 83, heigth: 20.0}, 
    {name: "Charizard", description: "fire pokemon", attack: 84, defense: 78, heigth: 17.0}, 
	{name: "Squirtle", description: "weather pokemon", attack: 48, defense: 65, heigth: 5.0}, 
]
```

```
> db.pokemons.insert(regPokemons)
BulkWriteResult({
    "writeErrors" : [ ],
    "writeConcernErrors" : [ ],
    "nInserted" : 5,
    "nUpserted" : 0,
    "nMatched" : 0,
    "nModified" : 0,
    "nRemoved" : 0,
    "upserted" : [ ]
})
```

## Listagem dos Pokemons
``` 
> db.pokemons.find()
{ "_id" : ObjectId("566755008191a79b9c07bad6"), "name" : "Bulbasaur", "description" : "seed pokemon", "attack" : 49, "defense" : 49, "heigth" : 7 }
{ "_id" : ObjectId("566755008191a79b9c07bad7"), "name" : "Ivysaur", "description" : "seed pokemon", "attack" : 62, "defense" : 63, "heigth" : 10 }
{ "_id" : ObjectId("566755008191a79b9c07bad8"), "name" : "Venusaur", "description" : "seed pokemon", "attack" : 82, "defense" : 83, "heigth" : 20 }
{ "_id" : ObjectId("566755008191a79b9c07bad9"), "name" : "Charizard", "description" : "fire pokemon", "attack" : 84, "defense" : 78, "heigth" : 17 }
{ "_id" : ObjectId("566755008191a79b9c07bada"), "name" : "Squirtle", "description" : "weather pokemon", "attack" : 48, "defense" : 65, "heigth" : 5 }
```

## Procurando Pokemon Arceus
### Usando o seletor para poder mudar a propiedade :)
``` 
> var poke = db.pokemons.findOne({name:'Charizard'})
```

## Atualização da propiedade para Fight
``` 
>poke.description = "Fire / Flying"
>db.pokemons.save(poke)
```
