###MongoDB - Aula 03 - Exercício
Autor: Thiago de Carvalho

##1. Liste todos Pokemons com a altura menor que 0.5;
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = {height: {$lt: 0.5}}
megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("56d5dc488904f06b371889c1"),
  "name": "Pikachu",
  "description": "Rato que dá choque em geral",
  "attack": 100,
  "defense": 60,
  "height": 0.4
}
{
  "_id": ObjectId("56d5dc488904f06b371889c2"),
  "name": "Rattata",
  "description": "Rattata is cautious in the extreme. Even while it is asleep, it constantly listens by moving its ears around. It is not picky about where it lives—it will make its nest anywhere.",
  "attack": 90,
  "defense": 70,
  "height": 0.3
}
Fetched 2 record(s) in 4ms

```
##2. Liste todos Pokemons com a altura maior ou igual que 0.5;
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = {height: {$gte: 0.5}}
megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("56d5dc488904f06b371889c3"),
  "name": "Gloom",
  "description": "Gloom releases a foul fragrance from the pistil of its flower. When faced with danger, the stench worsens. If this Pokémon is feeling calm and secure, it does not release its usual stinky aroma.",
  "attack": 80,
  "defense": 80,
  "height": 0.8
}
{
  "_id": ObjectId("56d5dc488904f06b371889c4"),
  "name": "Mewtwo",
  "description": "Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémons body, they failed to endow Mewtwo with a compassionate heart.",
  "attack": 70,
  "defense": 90,
  "height": 2
}
{
  "_id": ObjectId("56d5dc488904f06b371889c5"),
  "name": "Gyrados",
  "description": "When Magikarp evolves into Gyarados, its brain cells undergo a structural transformation. It is said that this transformation is to blame for this Pokémons wildly violent nature.",
  "attack": 60,
  "defense": 100,
  "height": 6.5
}
Fetched 3 record(s) in 4ms
```
##3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = { $and: [ {height: { $lte: 0.5 }}, {type: 'grama'}]}
megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```
##4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = { $or: [ {name:'Pikachu'},{ attack: { $lte: 0.5 }}]}
megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("56d5dc488904f06b371889c1"),
  "name": "Pikachu",
  "description": "Rato que dá choque em geral",
  "attack": 100,
  "defense": 60,
  "height": 0.4
}
Fetched 1 record(s) in 4ms
```
##5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = { $and: [{ attack: { $gte: 48 }}, { height: { $lte: 0.5 } } ] }
megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("56d5dc488904f06b371889c1"),
  "name": "Pikachu",
  "description": "Rato que dá choque em geral",
  "attack": 100,
  "defense": 60,
  "height": 0.4
}
{
  "_id": ObjectId("56d5dc488904f06b371889c2"),
  "name": "Rattata",
  "description": "Rattata is cautious in the extreme. Even while it is asleep, it constantly listens by moving its ears around. It is not picky about where it lives—it will make its nest anywhere.",
  "attack": 90,
  "defense": 70,
  "height": 0.3
}
Fetched 2 record(s) in 3ms

```
