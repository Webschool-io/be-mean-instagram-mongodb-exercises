# MongoDB - Aula 03 - Exercício
Autor: Mauriene Firmino

##Liste todos Pokemons com a altura menor que 0.5

```
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> var query = {height:{$lt:0.5}}
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c41cd5d7779311294b6a8c"),
  "name": "Meowth",
  "description": "Meowth withdraws its sharp claws into its paws to slinkily sneak about without making any incriminating footsteps. For some reason, this Pokémon loves shiny coins that glitter with light.",
  "attack": 200,
  "defense": 200,
  "height": 0.4
}
{
  "_id": ObjectId("57c41d712458be9a7cade5bf"),
  "name": "Pidgey",
  "description": "Um passarinho muito louco",
  "attack": 200,
  "defense": 200,
  "height": 0.3
}
Fetched 2 record(s) in 1ms

```

## Liste todos Pokemons com a altura maior ou igual que 0.5

```
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> var query = {height:{$gte:0.5}}
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c41bf8d7779311294b6a8b"),
  "name": "Golbat",
  "description": "Golbat loves to drink the blood of living things. It is particularly active in the pitch black of night. This Pokémon flits around in the night skies, seeking fresh blood. ",
  "attack": 400,
  "defense": 300,
  "height": 1.6
}
{
  "_id": ObjectId("57c41dcb2458be9a7cade5c0"),
  "name": "Arbok",
  "description": "This Pokémon is terrifically strong in order to constrict things with its body. It can even flatten steel oil drums. Once Arbok wraps its body around its foe, escaping its crunching embrace is impossible.",
  "attack": 400,
  "defense": 300,
  "height": 3.5
}
{
  "_id": ObjectId("57c41e222458be9a7cade5c1"),
  "name": "Ninetales",
  "description": "Ninetales casts a sinister light from its bright red eyes to gain total control over its foe's mind. This Pokémon is said to live for a thousand years.",
  "attack": 400,
  "defense": 300,
  "height": 1.1
}
Fetched 3 record(s) in 3ms

``` 
## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama

```
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> var query = {$and:[{height:{$lte:0.5}},{type:"grass"}]}
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c41cd5d7779311294b6a8c"),
  "name": "Meowth",
  "description": "Meowth withdraws its sharp claws into its paws to slinkily sneak about without making any incriminating footsteps. For some reason, this Pokémon loves shiny coins that glitter with light.",
  "attack": 200,
  "defense": 200,
  "height": 0.4,
  "type": "grass"
}
{
  "_id": ObjectId("57c41d712458be9a7cade5bf"),
  "name": "Pidgey",
  "description": "Um passarinho muito louco",
  "attack": 200,
  "defense": 200,
  "height": 0.3,
  "type": "grass"
}
Fetched 2 record(s) in 2ms

```

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5

```
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> var query = {$or:[{name:/pikachu/i},{attack:{$lte:0.5}}]}
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

``` 

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5

```
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c41cd5d7779311294b6a8c"),
  "name": "Meowth",
  "description": "Meowth withdraws its sharp claws into its paws to slinkily sneak about without making any incriminating footsteps. For some reason, this Pokémon loves shiny coins that glitter with light.",
  "attack": 200,
  "defense": 200,
  "height": 0.4,
  "type": "grass"
}
{
  "_id": ObjectId("57c41d712458be9a7cade5bf"),
  "name": "Pidgey",
  "description": "Um passarinho muito louco",
  "attack": 200,
  "defense": 200,
  "height": 0.3,
  "type": "grass"
}
Fetched 2 record(s) in 2ms

```  
