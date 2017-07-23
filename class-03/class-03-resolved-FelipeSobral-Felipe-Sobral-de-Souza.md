# MongoDB - Aula 03 - Exercício
Autor: Felipe Sobral de Souza

## Liste todos Pokemons com a altura **menor que** 0.5;
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = {height: {$lt: 0.5}}
felipe-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
Fetched 0 record(s) in 40ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = {height: {$gte: 0.5}}
felipe-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("56433350342f68f460c236b4"),
  "name": "Ivysaur",
  "description": "There is a bud on this Pokémons back. To support its weight, Ivysaurs legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, its a sign that the bud will bloom into a large flower soon.",
  "type": "Poison",
  "attack": 62,
  "defense": 63,
  "height": 10
}
{
  "_id": ObjectId("56433350342f68f460c236b5"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "type": "Water",
  "attack": 83,
  "defense": 100,
  "height": 16
}
{
  "_id": ObjectId("56433350342f68f460c236b6"),
  "name": "Rattata",
  "description": "Rattata is cautious in the extreme. Even while it is asleep, it constantly listens by moving its ears around. It is not picky about where it lives—it will make its nest anywhere.",
  "type": "Normal",
  "attack": 56,
  "defense": 35,
  "height": 3
}
{
  "_id": ObjectId("56433350342f68f460c236b7"),
  "name": "Heatmor",
  "description": "Using their very hot, flame-covered tongues, they burn through Durants steel bodies and consume their insides.",
  "type": "Fire",
  "attack": 97,
  "defense": 66,
  "height": 14
}
{
  "_id": ObjectId("56433350342f68f460c236b8"),
  "name": "Boldore",
  "description": "Pokemon Boladão",
  "type": "Rock",
  "attack": 105,
  "defense": 105,
  "height": 9
}
Fetched 5 record(s) in 2ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = {$and:[{height:{$lte:0.5}},{'type':'grass'}]}
felipe-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```
## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = {$or:[{'name':'Pikachu'},{'attack':{$lte:0.5}}]}
felipe-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = {$and:[{height:{$lte:0.5}},{'atack':{$gte:48}}]}
felipe-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```
