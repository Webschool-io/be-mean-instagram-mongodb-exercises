# MongoDB - Aula 02 - Exercício
autor: Ederson Devaldo da Silva

## Listando Pokemons com a altura menor que 0.5

```
codevops(mongod-3.0.6) be-mean-pokemons> var query = {height: {$lt: 0.5}}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56623dd5f3045dd41d6869d7"),
  "name": "Pikachu",
  "description": "Bicho muito loko",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

## Listando Pokemons com a altura maior ou igual que 0.5

```
codevops(mongod-3.0.6) be-mean-pokemons> var query = {height: {$gte: 0.5}}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566219f4f3045dd41d6869d2"),
  "name": "Metapod",
  "description": "The shell covering this Pokémons body is as hard as an iron slab.Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.",
  "type": "Bug",
  "attack": 10,
  "defense": 30,
  "height": 0.7
}
{
  "_id": ObjectId("56621a69f3045dd41d6869d3"),
  "name": "Nidorino",
  "description": "Nidorino has a horn that is harder than a diamond. If it senses a hostile presence, all the barbs on its back bristle up at once, and it challenges the foe with all its might.",
  "type": "Poison",
  "attack": 40,
  "defense": 30,
  "height": 0.9
}
{
  "_id": ObjectId("56621b2cf3045dd41d6869d4"),
  "name": "Golduck",
  "description": "The webbed flippers on its forelegs and hind legs and the streamlined body of Golduck give it frightening speed. This Pokémon is definitely much faster than even the most athletic swimmer.",
  "type": "Water",
  "attack": 40,
  "defense": 30,
  "height": 1.7
}
{
  "_id": ObjectId("56621bd9f3045dd41d6869d5"),
  "name": "Primeape",
  "description": "When Primeape becomes furious, its blood circulation is boosted. In turn, its muscles are made even stronger. However, it also becomes much less intelligent at the same time.",
  "type": "Fighting",
  "attack": 50,
  "defense": 30,
  "height": 1
}
{
  "_id": ObjectId("56621cbcf3045dd41d6869d6"),
  "name": "Arcanine",
  "description": "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night. The fire that blazes wildly within this Pokémons body is its source of power.",
  "type": "Fire",
  "attack": 60,
  "defense": 40,
  "height": 1.9
}
Fetched 5 record(s) in 2ms
```
## Listando Pokemons com a altura menor ou igual 0.5 E do tipo grama

```
codevops(mongod-3.0.6) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}},{type: 'grass'}]}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Listando pokemons com o attack MAIOR OU IGUAL QUE 48 E com height MENOR OU IGUAL QUE 0.5

```
codevops(mongod-3.0.6) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}},{height: {$lte: 0.5}}]}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```




