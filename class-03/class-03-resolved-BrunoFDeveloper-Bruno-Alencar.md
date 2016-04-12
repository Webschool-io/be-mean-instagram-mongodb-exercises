# MongoDB - Aula 03 - Exercício
autor: Bruno Alencar

## 1. Liste todos Pokemons com a altura menor que 0.5;
```
MacBook-Pro-de-bruno-10(mongod-3.2.0) be-mean-pokemons> var query = {"height": {$lt: 0.5}}
MacBook-Pro-de-bruno-10(mongod-3.2.0) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("56f5e0152d3d45cf2e40cbc8"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
  "attack": 200,
  "defense": 200,
  "height": 0.3,
  "type": "bug"
}
```
## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;
```
MacBook-Pro-de-bruno-10(mongod-3.2.0) be-mean-pokemons> var query = {"height": {$gte: 0.5}}
MacBook-Pro-de-bruno-10(mongod-3.2.0) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("56f5dffb2d3d45cf2e40cbc5"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 200,
  "height": 0.5
}

```
## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;
```
MacBook-Pro-de-bruno-10(mongod-3.2.0) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: "grass"}]}
MacBook-Pro-de-bruno-10(mongod-3.2.0) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("56f5dffb2d3d45cf2e40cbc5"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 200,
  "height": 0.5
}

```
## 4. Liste todos Pokemons com o name 'Pikachu' OU com attack menor ou igual que 0.5;
```
MacBook-Pro-de-bruno-10(mongod-3.2.0) be-mean-pokemons> var query = {$or:[{attack: {$lte:0.5}}, {name:'Pikachu'}]}
MacBook-Pro-de-bruno-10(mongod-3.2.0) be-mean-pokemons> db.pokemons.findOne(query)
null

```
## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;
```
MacBook-Pro-de-bruno-10(mongod-3.2.0) be-mean-pokemons> var query = {$and:[{attack: {$gte:48}}, {height:{$lte:0.5}}]}
MacBook-Pro-de-bruno-10(mongod-3.2.0) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("56f5dffb2d3d45cf2e40cbc5"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 200,
  "height": 0.5
}
```