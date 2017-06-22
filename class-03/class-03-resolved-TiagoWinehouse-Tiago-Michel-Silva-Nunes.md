# MongoDB - Aula 03 - Exercício
autor: Tiago Nunes

## Listagem pokemons height < 0.5

```
SkyWine(mongod-3.0.7) be-mean-pokemons> var query = {height:{$lt:0.5}}
SkyWine(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644e7834423570108bc916c"),
  "name": "Mewtwo",
  "description": "Canguru revoltado",
  "type": "psychic",
  "attack": 110,
  "defense": 90,
  "height": 0.3
}
{
  "_id": ObjectId("5644f2c44423570108bc916d"),
  "name": "Sambas",
  "description": "Pokémondo samba",
  "attack": 100,
  "defense": 105,
  "height": 0.3
}
{
  "_id": ObjectId("5644f2c44423570108bc916e"),
  "name": "Milagre",
  "description": "Pokémondo do Senhor",
  "attack": 500,
  "defense": 2500,
  "height": 0.2
}
{
  "_id": ObjectId("5644f2c44423570108bc916f"),
  "name": "Killa",
  "description": "Pokémondo Brabu",
  "attack": 570,
  "defense": 23,
  "height": 0.2
}
Fetched 4 record(s) in 3ms

```

## Listagem pokemons height >= 0.5

```

SkyWine(mongod-3.0.7) be-mean-pokemons> var query = {height : { $gte: 0.5} }
SkyWine(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644e7834423570108bc9168"),
  "name": "Meganium",
  "description": "Pokémon que se destaca não pelo seu ataque, mas sim pela sua defesa",
  "attack": 100,
  "defense": 105,
  "height": 1.8
}
{
  "_id": ObjectId("5644e7834423570108bc9169"),
  "name": "Zapdos",
  "description": "Pássaro com fogo no rabo",
  "type": "eletric",
  "attack": 90,
  "defense": 80,
  "height": 21
}
{
  "_id": ObjectId("5644e7834423570108bc916a"),
  "name": "Entei",
  "description": "Cachorro esquentadinho",
  "type": "fire",
  "attack": 115,
  "defense": 85,
  "height": 21
}
{
  "_id": ObjectId("5644e7834423570108bc916b"),
  "name": "Moltres",
  "description": "Pássaro com fogo no rabo",
  "type": "fire",
  "attack": 110,
  "defense": 65,
  "height": 21
}
Fetched 4 record(s) in 7ms

```

## Listagem pokemons height <= 0.5 e type "grama"

```

SkyWine(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}},{type: "grama"}]}
SkyWine(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644f496b14c9cac08ac56ab"),
  "name": "Atonis",
  "description": "Poke Atom",
  "type": "grama",
  "attack": 100,
  "defense": 105,
  "height": 0.3
}
Fetched 1 record(s) in 1ms


```

## Listagem pokemons name "Pikachu" ou attack <= 0.5

```

SkyWine(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
SkyWine(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 21ms


```

## Listagem pokemons attack >= 48 e height <= 0.5

```
SkyWine(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
SkyWine(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644e7834423570108bc916c"),
  "name": "Mewtwo",
  "description": "Canguru revoltado",
  "type": "psychic",
  "attack": 110,
  "defense": 90,
  "height": 0.3
}
{
  "_id": ObjectId("5644f2c44423570108bc916d"),
  "name": "Sambas",
  "description": "Pokémondo samba",
  "attack": 100,
  "defense": 105,
  "height": 0.3
}
{
  "_id": ObjectId("5644f2c44423570108bc916e"),
  "name": "Milagre",
  "description": "Pokémondo do Senhor",
  "attack": 500,
  "defense": 2500,
  "height": 0.2
}
{
  "_id": ObjectId("5644f2c44423570108bc916f"),
  "name": "Killa",
  "description": "Pokémondo Brabu",
  "attack": 570,
  "defense": 23,
  "height": 0.2
}
{
  "_id": ObjectId("5644f496b14c9cac08ac56ab"),
  "name": "Atonis",
  "description": "Poke Atom",
  "type": "grama",
  "attack": 100,
  "defense": 105,
  "height": 0.3
}
Fetched 5 record(s) in 8ms

```
