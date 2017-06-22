# MongoDB - Aula 03 - Exercício
Autor: Jefferson Neves

## 1. Liste todos os Pokemons com altura **menor que** 0.5

```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{
  "_id": ObjectId("56532de874cc222883e7ba5b"),
  "name": "Pikachu",
  "description": "Whenever PIKACHU comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this POKEMON mistook the intensity of its charge.",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "type": "electric"
}
Fetched 1 record(s) in 1ms
```

## 2. Liste todos os Pokemons com altura **maior ou igual que** 0.5

```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{
  "_id": ObjectId("56532de174cc222883e7ba56"),
  "name": "Bulbasaur",
  "description": "BULBASAUR can be seen napping in bright sunlight. There is a seed on its back. By soaking up the suns rays, the seed grows progressively larger.",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "type": "grass"
}
{
  "_id": ObjectId("56532de274cc222883e7ba57"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when CHARMANDER is happy, and blazes when it is enraged.",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "type": "fire"
}
{
  "_id": ObjectId("56532de374cc222883e7ba58"),
  "name": "Squirtle",
  "description": "Its shell is not just for protection. Its rounded shape and the grooves on its surface minimize resistance in water, enabling SQUIRTLE to swim at high speeds.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "water"
}
{
  "_id": ObjectId("56532de474cc222883e7ba59"),
  "name": "Butterfree",
  "description": "It has a superior ability to search for delicious honey from flowers. It can seek, extract, and carry honey from flowers blooming over six miles away.",
  "attack": 45,
  "defense": 50,
  "height": 1.1,
  "type": "insect"
}
{
  "_id": ObjectId("56532de674cc222883e7ba5a"),
  "name": "Pidgeotto",
  "description": "PIDGEOTTO claims a large area as its own territory. This POKMON flies around, patrolling its living space. If its territory is violated, it shows no mercy in thoroughly punishing the foe with its sharp claws.",
  "attack": 60,
  "defense": 55,
  "height": 1.1,
  "type": "flying"
}
Fetched 5 record(s) in 5ms
```

## 3. Liste todos os Pokemons com altura **menor ou igual que** 0.5 **E** do tipo grass

```
> var query = {$and: [{height: {$lte: 0.5}}, {type: /grass/}]}
> db.pokemons.find(query)
Fetched 0 record(s) in 9ms
```

## 4. Liste todos os Pokemons com name 'Pikachu' **OU** com attack **menor ou igual** a 55

```
> var query = {$or: [{attack: {$lte: 55}}, {name: /pikachu/i}]}
> db.pokemons.find(query)
{
  "_id": ObjectId("56532de174cc222883e7ba56"),
  "name": "Bulbasaur",
  "description": "BULBASAUR can be seen napping in bright sunlight. There is a seed on its back. By soaking up the suns rays, the seed grows progressively larger.",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "type": "grass"
}
{
  "_id": ObjectId("56532de274cc222883e7ba57"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when CHARMANDER is happy, and blazes when it is enraged.",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "type": "fire"
}
{
  "_id": ObjectId("56532de374cc222883e7ba58"),
  "name": "Squirtle",
  "description": "Its shell is not just for protection. Its rounded shape and the grooves on its surface minimize resistance in water, enabling SQUIRTLE to swim at high speeds.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "water"
}
{
  "_id": ObjectId("56532de474cc222883e7ba59"),
  "name": "Butterfree",
  "description": "It has a superior ability to search for delicious honey from flowers. It can seek, extract, and carry honey from flowers blooming over six miles away.",
  "attack": 45,
  "defense": 50,
  "height": 1.1,
  "type": "insect"
}
{
  "_id": ObjectId("56532de874cc222883e7ba5b"),
  "name": "Pikachu",
  "description": "Whenever PIKACHU comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this POKEMON mistook the intensity of its charge.",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "type": "electric"
}
Fetched 5 record(s) in 3ms
```

## 5. Liste todos os Pokemons com attack **maior ou igual que** 48 **E** com height **menor ou igual** que 0.5
```
> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
{
  "_id": ObjectId("56532de374cc222883e7ba58"),
  "name": "Squirtle",
  "description": "Its shell is not just for protection. Its rounded shape and the grooves on its surface minimize resistance in water, enabling SQUIRTLE to swim at high speeds.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "water"
}
{
  "_id": ObjectId("56532de874cc222883e7ba5b"),
  "name": "Pikachu",
  "description": "Whenever PIKACHU comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this POKEMON mistook the intensity of its charge.",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "type": "electric"
}
Fetched 2 record(s) in 4ms
```