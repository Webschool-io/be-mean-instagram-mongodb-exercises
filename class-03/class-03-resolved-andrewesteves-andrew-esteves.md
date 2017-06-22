# MongoDB - Aula 03 - Exercício
autor: Andrew Esteves

## 1. Liste todos Pokemons com a altura menor que 0.5;

```
var query = {height: {$lt: 0.5}};
Andrew(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 2ms

```

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```
var query = {height: {$gte: 0.5}};
Andrew(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("56447e617fe9cee4a5bc8adc"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "attack": 60,
  "defense": 80,
  "height": 1.6
}
{
  "_id": ObjectId("56447e617fe9cee4a5bc8add"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "attack": 70,
  "defense": 50,
  "height": 1.7
}
{
  "_id": ObjectId("56447e617fe9cee4a5bc8ade"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flowers aroma soothes the emotions of people.",
  "attack": 50,
  "defense": 80,
  "height": 2
}
{
  "_id": ObjectId("56447e617fe9cee4a5bc8adf"),
  "name": "Pidgeot",
  "description": "This Pokémon has a dazzling plumage of beautifully glossy feathers. Many Trainers are captivated by the striking beauty of the feathers on its head, compelling them to choose Pidgeot as their Pokémon.",
  "attack": 75,
  "defense": 50,
  "height": 1.5
}
{
  "_id": ObjectId("56447e617fe9cee4a5bc8ae0"),
  "name": "Golduck",
  "description": "Description updated",
  "attack": 90,
  "defense": 70,
  "height": 1.7
}
Fetched 5 record(s) in 8ms
Andrew(mongod-3.0.4) be-mean-pokemons> 

```

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
var query = {$and: [{height: {$lte: 0.5}}, {type: 'Grama'}]}
Andrew(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 1ms

```

## 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

```
var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
Andrew(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 0ms

```

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
Andrew(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 1ms

```
