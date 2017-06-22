#Exercício 03 - MongoDB - BeMEAN#

##Aluno: Leonardo Ribeiro##



###Liste todos os pokemons com a altura menor que 0.5###

```
be-mean-pokemons> db.pokemons.find({"height":{$lt: 0.5}});
{
  "_id": ObjectId("5783d0dcdc6eb212ff9808eb"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
  "attack": 200,
  "defense": 200,
  "height": 0.3
}
Fetched 1 record(s) in 4ms
```

###Liste todos os Pokemons com a altura maior ou igual que 0.5###

```
be-mean-pokemons> db.pokemons.find({"height":{$gte: 0.5}});
{
  "_id": ObjectId("5783d060dc6eb212ff9808e7"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 300,
  "defense": 200,
  "height": 0.7
}
{
  "_id": ObjectId("5783d086dc6eb212ff9808e8"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 300,
  "defense": 200,
  "height": 0.7
}
{
  "_id": ObjectId("5783d0a7dc6eb212ff9808e9"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 300,
  "defense": 200,
  "height": 0.6
}
{
  "_id": ObjectId("5783d0bfdc6eb212ff9808ea"),
  "name": "Squirtle",
  "description": "Pokemon que lança liquido venenoso",
  "attack": 300,
  "defense": 300,
  "height": 0.5
}
{
  "_id": ObjectId("5783d0eddc6eb212ff9808ec"),
  "name": "Butterfree",
  "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
  "attack": 200,
  "defense": 200,
  "height": 1.1
}
{
  "_id": ObjectId("5783d0fadc6eb212ff9808ed"),
  "name": "Abra",
  "description": "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.",
  "attack": 100,
  "defense": 100,
  "height": 0.9
}
{
  "_id": ObjectId("5783d10cdc6eb212ff9808ee"),
  "name": "Farfetch'd",
  "description": "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.",
  "attack": 300,
  "defense": 300,
  "height": 0.8
}
Fetched 7 record(s) in 1ms
`

###Liste todos os Pokemons com a altura menor ou igual que 0.5 e do tipo grama###
`
be-mean-pokemons> var query = {$and: [{type:"grass"},{height: {$lte: 0.5}}]};
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5783d0dcdc6eb212ff9808eb"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
  "attack": 200,
  "defense": 200,
  "height": 0.3,
  "type": "grass"
}
Fetched 1 record(s) in 1ms
```

###Liste todos os Pokemons com o name "Pikachu" ou com attack menor ou igual que 0.5###
```
be-mean-pokemons> var query = {$or: [{name:"Pikachu"},{attack: {$lte: 0.5}}]};
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5783d060dc6eb212ff9808e7"),
  "name": "Pikachu",
  "description": "Pikachu is an Electric type Pokémon introduced in Generation 1. It is known as the Mouse Pokémon",
  "attack": 229,
  "defense": 196,
  "height": 0.4,
  "type": "ELECTRIC"
}
Fetched 1 record(s) in 1ms
```

###Liste todos os Pokemons com o attack maior ou igual que 48 e com height menor ou igual que 0.5###
```
be-mean-pokemons> var query = {$and: [{attack:{$gte: 48}},{height: {$lte: 0.5}}]};
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5783d060dc6eb212ff9808e7"),
  "name": "Pikachu",
  "description": "Pikachu is an Electric type Pokémon introduced in Generation 1. It is known as the Mouse Pokémon",
  "attack": 229,
  "defense": 196,
  "height": 0.4,
  "type": "ELECTRIC"
}
{
  "_id": ObjectId("5783d0bfdc6eb212ff9808ea"),
  "name": "Squirtle",
  "description": "Pokemon que lança liquido venenoso",
  "attack": 300,
  "defense": 300,
  "height": 0.5
}
{
  "_id": ObjectId("5783d0dcdc6eb212ff9808eb"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
  "attack": 200,
  "defense": 200,
  "height": 0.3,
  "type": "grass"
}
Fetched 3 record(s) in 1ms
```
