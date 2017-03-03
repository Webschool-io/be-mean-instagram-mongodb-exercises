# MongoDb - Aula 02 - Exercício
Autor: Mauriene Firmino

## Criar database chamada be-mean-pokemons

```
mauriene-J1800NH(mongod-2.6.10) test> use be-mean-pokemons
switched to db be-mean-pokemons
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> 

```

## Listagem de todas dbs

```
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> show dbs
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
local             → 0.078GB
test              → (empty)
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> 

```

## Listagem de todas as collections

```
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> show collections
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> 

```

## Criar cinco pokemons

```
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> var query = {
... name:"Golbat",
... description:"Golbat loves to drink the blood of living things. It is particularly active in the pitch black of night. This Pokémon flits around in the night skies, seeking fresh blood. ",
... attack: 400 ,
... defense: 300,
... height:1.6
... }
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> query
{
  "name": "Golbat",
  "description": "Golbat loves to drink the blood of living things. It is particularly active in the pitch black of night. This Pokémon flits around in the night skies, seeking fresh blood. ",
  "attack": 400,
  "defense": 300,
  "height": 1.6
}
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(query)
Inserted 1 record(s) in 635ms
WriteResult({
  "nInserted": 1
})

mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> var query = {
... name:"Meowth",
... description:"Meowth withdraws its sharp claws into its paws to slinkily sneak about without making any incriminating footsteps. For some reason, this Pokémon loves shiny coins that glitter with light.",
... attack: 200 ,
... defense: 200,
... height:0.4
... }
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> 
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(query)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> var query = {
... name:"Pidgey",
... description:"Pidgey has an extremely sharp sense of direction. It is capable of unerringly returning home to its nest, however far it may be removed from its familiar surroundings.",
... attack: 200 ,
... defense: 200,
... height:0.3
... }
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(query)
Inserted 1 record(s) in 12ms
WriteResult({
  "nInserted": 1
})

mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> var query = {
... name:"Arbok",
... description:"This Pokémon is terrifically strong in order to constrict things with its body. It can even flatten steel oil drums. Once Arbok wraps its body around its foe, escaping its crunching embrace is impossible.",
... attack: 400 ,
... defense: 300,
... height:3.5
... }
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(query)
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})

mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> var query = {
... name:"Ninetales",
... description:"Ninetales casts a sinister light from its bright red eyes to gain total control over its foe's mind. This Pokémon is said to live for a thousand years.",
... attack: 400 ,
... defense: 300,
... height:1.1
... }
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> 
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> 
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(query)
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})


```

## Listar todos os pokemons

```
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57c41bf8d7779311294b6a8b"),
  "name": "Golbat",
  "description": "Golbat loves to drink the blood of living things. It is particularly active in the pitch black of night. This Pokémon flits around in the night skies, seeking fresh blood. ",
  "attack": 400,
  "defense": 300,
  "height": 1.6
}
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
  "description": "Pidgey has an extremely sharp sense of direction. It is capable of unerringly returning home to its nest, however far it may be removed from its familiar surroundings.",
  "attack": 200,
  "defense": 200,
  "height": 0.3
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
Fetched 5 record(s) in 7ms

```

## Buscar um pokemon

```
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> var query = {name:/Pidgey/i}
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c41d712458be9a7cade5bf"),
  "name": "Pidgey",
  "description": "Pidgey has an extremely sharp sense of direction. It is capable of unerringly returning home to its nest, however far it may be removed from its familiar surroundings.",
  "attack": 200,
  "defense": 200,
  "height": 0.3
}
Fetched 1 record(s) in 1ms
```

## Editar a description do pokemon escolhido

```
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> query
{
  "name": /Pidgey/i
}
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> var poke = db.pokemons.findOne(query)
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> poke
{
  "_id": ObjectId("57c41d712458be9a7cade5bf"),
  "name": "Pidgey",
  "description": "Pidgey has an extremely sharp sense of direction. It is capable of unerringly returning home to its nest, however far it may be removed from its familiar surroundings.",
  "attack": 200,
  "defense": 200,
  "height": 0.3
}
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> poke.description = "Um passarinho muito louco"
Um passarinho muito louco
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 46ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
mauriene-J1800NH(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c41d712458be9a7cade5bf"),
  "name": "Pidgey",
  "description": "Um passarinho muito louco",
  "attack": 200,
  "defense": 200,
  "height": 0.3
}
Fetched 1 record(s) in 1ms

```