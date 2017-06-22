# MongoDB - Aula 03 - Exercício
Autor: José Neto

## Liste todos Pokemons com a altura **menor que** 0.5;

```
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt:0.5}}
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645560b90461003350c7041"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
{
  "_id": ObjectId("5645560e90461003350c7045"),
  "name": "Weedle",
  "description": "Weedle has an extremely acute sense of smell. It is capable of distinguishing its favorite kinds of leaves from those it dislikes just by sniffing with its big red proboscis (nose). Editado!!!",
  "type": "Bug",
  "attack": 20,
  "defense": 20,
  "height": 0.3
}
Fetched 2 record(s) in 10ms

````


## Liste todos Pokemons com a altura **maior ou igual que** 0.5
````
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte:0.5}}
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645560b90461003350c7042"),
  "name": "Wartortle",
  "description": "Its tail is large and covered with a rich, thick fur. The tail becomes increasingly deeper in color as Wartortle ages. The scratches on its shell are evidence of this Pokémon's toughness as a battler.",
  "type": "Water",
  "attack": 30,
  "defense": 40,
  "height": 1
}
{
  "_id": ObjectId("5645560b90461003350c7043"),
  "name": "Metapod",
  "description": "The shell covering this Pokémon's body is as hard as an iron slab. Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.",
  "type": "Bug",
  "attack": 10,
  "defense": 30,
  "height": 0.7
}
{
  "_id": ObjectId("5645560b90461003350c7044"),
  "name": "Butterfree",
  "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
  "type": "Bug",
  "attack": 20,
  "defense": 20,
  "height": 1.1
}
Fetched 3 record(s) in 10ms

````

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
Obs.: Não tenho nenhum do tipo **grama**, então, usei o tipo **Bug**

````
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> var query = {type: "Bug", height:{$lte: 0.5}}
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645560e90461003350c7045"),
  "name": "Weedle",
  "description": "Weedle has an extremely acute sense of smell. It is capable of distinguishing its favorite kinds of leaves from those it dislikes just by sniffing with its big red proboscis (nose). Editado!!!",
  "type": "Bug",
  "attack": 20,
  "defense": 20,
  "height": 0.3
}
Fetched 1 record(s) in 7ms

````


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
````
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645560b90461003350c7041"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
````


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

````
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

````