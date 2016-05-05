# MongoDB - Aula 04 - Exercício
Autor: Wladek Zacharski

## Adicionando 2 ataques ao mesmo tempo para os pokemons

```
> var query = { $or:[ { name:"Pikachu" },{ name: "Squirtle" },{name: "Bulbasaur"},{name: "Charmander"} ]}
> var mod = { $pushAll:{ moves:['Investida', 'ataque de areia']} }
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
```

## Adicionando 1 movimento em todos os pokemons

```
> var query = {}
> var mod = { $push:{ moves:'Desvio'} }
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 8, "nUpserted" : 0, "nModified" : 8 })
```
## Adicionando o pokemon "AindaNaoExisteMon"

```
> var query = {name: /AindaNaoExisteMon/i}
> var mod = {$set: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"}}
> var options = {upsert: true}
> db.pokemons.update(query, mod, options)
```

## Pesquisando todos com ataque "investida" e mais um favorito

```
> var query = { moves:{$in:[/investida/i, /desvio/i] } }
> db.pokemons.find(query)
{ "_id" : ObjectId("56678e6a0d5830549257b42e"), "attack" : 84, "defense" : 78, "description" : "Pokemon mais foda para mim", "height" : 5.1, "name" : "Charizard", "type" : "Fire / Flying", "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56678e950d5830549257b430"), "attack" : 110, "defense" : 90, "description" : "Pokemon sinistro do mau", "height" : 6, "name" : "Mewtwo", "type" : "Psychic", "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56678e7f0d5830549257b42f"), "attack" : 55, "defense" : 25, "description" : "Pokemon minhoca", "height" : 0.6, "name" : "Diglett", "type" : "Ground", "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56678ea70d5830549257b431"), "attack" : 130, "defense" : 90, "description" : "Pokemon Raro", "height" : 11.5, "name" : "Ho-oh", "type" : "Fire /  Flying", "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56683da51c44396fb4e1138a"), "attack" : 52, "defense" : 43, "descriptions" : "Pokemon com fogo no rabo", "height" : 1.8, "name" : "Charmander", "type" : "Fire", "moves" : [ "Investida", "ataque de areia", "Desvio" ] }
{ "_id" : ObjectId("56683eaa1c44396fb4e1138b"), "attack" : 48, "defense" : 65, "descriptions" : "Pokemon Tartaruga", "height" : 1.5, "name" : "Squirtle", "type" : "Weather", "moves" : [ "Investida", "ataque de areia", "Desvio" ] }
{ "_id" : ObjectId("56683f961c44396fb4e1138c"), "attack" : 55, "defense" : 40, "descriptions" : "Pokemon amarelinho fofinho", "height" : 1.2, "name" : "Pikachu", "moves" : [ "Investida", "ataque de areia", "Desvio" ] }
{ "_id" : ObjectId("56678e480d5830549257b42d"), "attack" : 49, "defense" : 49, "description" : "Pokemon inseto", "height" : 0.7, "name" : "Bulbasaur", "type" : "Grass", "moves" : [ "Investida", "ataque de areia", "Investida", "ataque de areia", "Desvio" ] }

```

## Pesquisando todos que possuem ataque que eu adicionei

```
> var query = { moves:{$in:[/Lança Chamas/i]} }
> db.pokemons.find(query)
{ "_id" : ObjectId("56678e6a0d5830549257b42e"), "attack" : 84, "defense" : 78, "description" : "Pokemon mais foda para mim", "height" : 5.1, "name" : "Charizard", "type" : "Fire / Flying", "moves" : [ "Desvio", "Lança Chamas" ] }
{ "_id" : ObjectId("56683da51c44396fb4e1138a"), "attack" : 52, "defense" : 43, "descriptions" : "Pokemon com fogo no rabo", "height" : 1.8, "name" : "Charmander", "type" : "Fire", "moves" : [ "Investida", "ataque de areia", "Desvio", "Lança Chamas" ] }

```

## Pesquisando todos que não são do tipo "elétrico"

```
> var query = { type:{$not:/eletric/i}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56678e6a0d5830549257b42e"), "attack" : 84, "defense" : 78, "description" : "Pokemon mais foda para mim", "height" : 5.1, "name" : "Charizard", "type" : "Fire / Flying", "moves" : [ "Desvio", "Lança Chamas" ] }
{ "_id" : ObjectId("56678e950d5830549257b430"), "attack" : 110, "defense" : 90, "description" : "Pokemon sinistro do mau", "height" : 6, "name" : "Mewtwo", "type" : "Psychic", "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56678e7f0d5830549257b42f"), "attack" : 55, "defense" : 25, "description" : "Pokemon minhoca", "height" : 0.6, "name" : "Diglett", "type" : "Ground", "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56678ea70d5830549257b431"), "attack" : 130, "defense" : 90, "description" : "Pokemon Raro", "height" : 11.5, "name" : "Ho-oh", "type" : "Fire /  Flying", "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56683da51c44396fb4e1138a"), "attack" : 52, "defense" : 43, "descriptions" : "Pokemon com fogo no rabo", "height" : 1.8, "name" : "Charmander", "type" : "Fire", "moves" : [ "Investida", "ataque de areia", "Desvio", "Lança Chamas" ] }
{ "_id" : ObjectId("56683eaa1c44396fb4e1138b"), "attack" : 48, "defense" : 65, "descriptions" : "Pokemon Tartaruga", "height" : 1.5, "name" : "Squirtle", "type" : "Weather", "moves" : [ "Investida", "ataque de areia", "Desvio" ] }
{ "_id" : ObjectId("56678e480d5830549257b42d"), "attack" : 49, "defense" : 49, "description" : "Pokemon inseto", "height" : 0.7, "name" : "Bulbasaur", "type" : "Grass", "moves" : [ "Investida", "ataque de areia", "Investida", "ataque de areia", "Desvio" ] }
{ "_id" : ObjectId("5668bbcd9a0d41953f0b1145"), "name" : "AindaNaoExisteMon", "attack" : null, "defense" : null, "height" : null, "description" : "Sem maiores informações" }

```

## Pesquisando todos que tenham ataque investida E tenham defesa não <= a 49

```
> var query = { $and:[ {moves:{$in:[/investida/i]}}, {defence:{$not:{$lte:49}}} ]}
> db.pokemons.find(query)
{ "_id" : ObjectId("56683da51c44396fb4e1138a"), "attack" : 52, "defense" : 43, "descriptions" : "Pokemon com fogo no rabo", "height" : 1.8, "name" : "Charmander", "type" : "Fire", "moves" : [ "Investida", "ataque de areia", "Desvio", "Lança Chamas" ] }
{ "_id" : ObjectId("56683eaa1c44396fb4e1138b"), "attack" : 48, "defense" : 65, "descriptions" : "Pokemon Tartaruga", "height" : 1.5, "name" : "Squirtle", "type" : "Weather", "moves" : [ "Investida", "ataque de areia", "Desvio" ] }
{ "_id" : ObjectId("56683f961c44396fb4e1138c"), "attack" : 55, "defense" : 40, "descriptions" : "Pokemon amarelinho fofinho", "height" : 1.2, "name" : "Pikachu", "moves" : [ "Investida", "ataque de areia", "Desvio" ], "type" : "Eletric" }
{ "_id" : ObjectId("56678e480d5830549257b42d"), "attack" : 49, "defense" : 49, "description" : "Pokemon inseto", "height" : 0.7, "name" : "Bulbasaur", "type" : "Grass", "moves" : [ "Investida", "ataque de areia", "Investida", "ataque de areia", "Desvio" ] }

```

## Removendo todos os pokemons do tipo água e com ataque < 50

```
> var query = {$and: [{type: "water"}, {attack: {$lt: 50}}]}
> db.pokemons.remove(query)
WriteResult({ "nRemoved" : 0 })

```
