# MongoDb - Aula 03 - Exercício

1. Liste todos Pokemons com a altura **menor que** 8;
2. Liste todos Pokemons com a altura **maior ou igual que** 8;
3. Liste todos Pokemons com a altura **menor ou igual que** 8 **E** do tipo agua;
4. Liste todos Pokemons com o name `Snorlax` **OU** com attack **menor ou igual que** 50;
5. Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 50;

## Estrutura

```md
# MongoDB - Aula 03 - Exercício
autor: **Guilherme Coelho Piovesan**

## Liste todos Pokemons com a altura **menor que** 8

guilherme-UB(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 8}}
guilherme-UB(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645366db273d5f44f617ba0"),
  "name": "Totodile",
  "description": "Despite the smallness of its body, Totodile's jaws are very powerful. While the Pokémon may think it is just playfully nipping, its bite has enough power to cause serious injury.",
  "type": "water",
  "attack": 65,
  "defense": 64,
  "height": 6
}
{
  "_id": ObjectId("5645366db273d5f44f617ba2"),
  "name": "Meowth",
  "description": "Meowth withdraws its sharp claws into its paws to slinkily sneak about without making any incriminating footsteps. For some reason, this Pokémon loves shiny coins that glitter with light.",
  "type": "normal",
  "attack": 45,
  "defense": 35,
  "height": 4
}
Fetched 2 record(s) in 1ms

## Liste todos Pokemons com a altura **maior ou igual que** 8

guilherme-UB(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 8}}
guilherme-UB(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645366db273d5f44f617b9e"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "type": "fire",
  "attack": 84,
  "defense": 78,
  "height": 17
}
{
  "_id": ObjectId("5645366db273d5f44f617b9f"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers. This discovery spurred controversy among scholars. Psy y y!!",
  "type": "water",
  "attack": 52,
  "defense": 48,
  "height": 8
}
{
  "_id": ObjectId("5645366db273d5f44f617ba1"),
  "name": "Snorlax",
  "description": "Snorlax's typical day consists of nothing more than eating and sleeping. It is such a docile Pokémon that there are children who use its expansive belly as a place to play.",
  "type": "normal",
  "attack": 110,
  "defense": 65,
  "height": 21
}
Fetched 3 record(s) in 2ms


## Liste todos Pokemons com a altura **menor ou igual que** 8 **E** do tipo água

guilherme-UB(mongod-3.0.7) be-mean-pokemons> var query1 = {height: {$lte: 8}}
guilherme-UB(mongod-3.0.7) be-mean-pokemons> var query2 = {type: "water"}
guilherme-UB(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({ $and: [query1, query2] })
{
  "_id": ObjectId("5645366db273d5f44f617b9f"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers. This discovery spurred controversy among scholars. Psy y y!!",
  "type": "water",
  "attack": 52,
  "defense": 48,
  "height": 8
}
{
  "_id": ObjectId("5645366db273d5f44f617ba0"),
  "name": "Totodile",
  "description": "Despite the smallness of its body, Totodile's jaws are very powerful. While the Pokémon may think it is just playfully nipping, its bite has enough power to cause serious injury.",
  "type": "water",
  "attack": 65,
  "defense": 64,
  "height": 6
}
Fetched 2 record(s) in 6ms


## Liste todos Pokemons com o name `Snorlax` **OU** com attack **menor ou igual que** 50

guilherme-UB(mongod-3.0.7) be-mean-pokemons> var query1 = {name: "Snorlax"}
guilherme-UB(mongod-3.0.7) be-mean-pokemons> var query2 = {attack: {$lte: 50}}
guilherme-UB(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({ $or: [query1, query2] })
{
  "_id": ObjectId("5645366db273d5f44f617ba1"),
  "name": "Snorlax",
  "description": "Snorlax's typical day consists of nothing more than eating and sleeping. It is such a docile Pokémon that there are children who use its expansive belly as a place to play.",
  "type": "normal",
  "attack": 110,
  "defense": 65,
  "height": 21
}
{
  "_id": ObjectId("5645366db273d5f44f617ba2"),
  "name": "Meowth",
  "description": "Meowth withdraws its sharp claws into its paws to slinkily sneak about without making any incriminating footsteps. For some reason, this Pokémon loves shiny coins that glitter with light.",
  "type": "normal",
  "attack": 45,
  "defense": 35,
  "height": 4
}
Fetched 2 record(s) in 1ms


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 50

guilherme-UB(mongod-3.0.7) be-mean-pokemons> var query1 = {attack: {$gte: 48}}
guilherme-UB(mongod-3.0.7) be-mean-pokemons> var query2 = {height: {$lte: 50}}
guilherme-UB(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({ $and: [query1, query2] })
{
  "_id": ObjectId("5645366db273d5f44f617b9e"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "type": "fire",
  "attack": 84,
  "defense": 78,
  "height": 17
}
{
  "_id": ObjectId("5645366db273d5f44f617b9f"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers. This discovery spurred controversy among scholars. Psy y y!!",
  "type": "water",
  "attack": 52,
  "defense": 48,
  "height": 8
}
{
  "_id": ObjectId("5645366db273d5f44f617ba0"),
  "name": "Totodile",
  "description": "Despite the smallness of its body, Totodile's jaws are very powerful. While the Pokémon may think it is just playfully nipping, its bite has enough power to cause serious injury.",
  "type": "water",
  "attack": 65,
  "defense": 64,
  "height": 6
}
{
  "_id": ObjectId("5645366db273d5f44f617ba1"),
  "name": "Snorlax",
  "description": "Snorlax's typical day consists of nothing more than eating and sleeping. It is such a docile Pokémon that there are children who use its expansive belly as a place to play.",
  "type": "normal",
  "attack": 110,
  "defense": 65,
  "height": 21
}
Fetched 4 record(s) in 3ms
```
