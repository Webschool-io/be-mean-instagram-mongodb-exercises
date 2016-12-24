#MongoDb - Aula 02 - Exercício#
##Autor: Leonardo Ribeiro##

###Criar database chamada be-mean-pokemons###

```
use be-mean-pokemons
switched to db be-mean-
```

###Listagem de todas dbs###

```
> show dbs
be-mean            0.005GB
be-mean-instagram  0.000GB
local              0.000GB
```

###Listagem de todas as collections###
```
show collections
```

###Criar cinco pokemons###

```
> db.pokemons.insert({name:"Bulbasaur", description: "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", attack: 300, defense:200, height:0.7})

WriteResult({ "nInserted" : 1 })

> db.pokemons.insert({name:"Charmander", description: "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.", attack: 300, defense:200, height:0.6})
WriteResult({ "nInserted" : 1 })

> db.pokemons.insert({name:"Squirtle", description: "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.", attack: 300, defense:300, height:0.5})
WriteResult({ "nInserted" : 1 })

> db.pokemons.insert({name:"Caterpie", description: "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.", attack: 200, defense:200, height:0.3})
WriteResult({ "nInserted" : 1 })

> db.pokemons.insert({name:"Butterfree", description: "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.", attack: 200, defense:200, height:1.1})
WriteResult({ "nInserted" : 1 })

> db.pokemons.insert({name:"Abra", description: "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.", attack: 100, defense:100, height:0.9})
WriteResult({ "nInserted" : 1 })

> db.pokemons.insert({name:"Farfetch'd", description: "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.", attack: 300, defense:300, height:0.8})
WriteResult({ "nInserted" : 1 })
```
###Listar todos os pokemons###

```
> db.pokemons.find().pretty()
{
  "_id" : ObjectId("5783d060dc6eb212ff9808e7"),
  "name" : "Bulbasaur",
  "description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack" : 300,
  "defense" : 200,
  "height" : 0.7
}
{
  "_id" : ObjectId("5783d086dc6eb212ff9808e8"),
  "name" : "Bulbasaur",
  "description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack" : 300,
  "defense" : 200,
  "height" : 0.7
}
{
  "_id" : ObjectId("5783d0a7dc6eb212ff9808e9"),
  "name" : "Charmander",
  "description" : "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack" : 300,
  "defense" : 200,
  "height" : 0.6
}
{
  "_id" : ObjectId("5783d0bfdc6eb212ff9808ea"),
  "name" : "Squirtle",
  "description" : "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack" : 300,
  "defense" : 300,
  "height" : 0.5
}
{
  "_id" : ObjectId("5783d0dcdc6eb212ff9808eb"),
  "name" : "Caterpie",
  "description" : "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
  "attack" : 200,
  "defense" : 200,
  "height" : 0.3
}
{
  "_id" : ObjectId("5783d0eddc6eb212ff9808ec"),
  "name" : "Butterfree",
  "description" : "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
  "attack" : 200,
  "defense" : 200,
  "height" : 1.1
}
{
  "_id" : ObjectId("5783d0fadc6eb212ff9808ed"),
  "name" : "Abra",
  "description" : "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.",
  "attack" : 100,
  "defense" : 100,
  "height" : 0.9
}
{
  "_id" : ObjectId("5783d10cdc6eb212ff9808ee"),
  "name" : "Farfetch'd",
  "description" : "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.",
  "attack" : 300,
  "defense" : 300,
  "height" : 0.8
}
> 
```

###Buscar um pokemon###
```
> var query = {name:"Squirtle"}
> var poke = db.pokemons.findOne(query)
> poke
{
  "_id" : ObjectId("5783d0bfdc6eb212ff9808ea"),
  "name" : "Squirtle",
  "description" : "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack" : 300,
  "defense" : 300,
  "height" : 0.5
}
> 
```

###Editar a description do pokemon escolhido###
```
> poke.description = "Squirtle's shell is not merely used for protection"
Squirtle's shell is not merely used for protection
> poke.description = "Pokemon que lança liquido venenoso"
Pokemon que lança liquido venenoso
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```
