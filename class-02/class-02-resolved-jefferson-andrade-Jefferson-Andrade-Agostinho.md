# MongoDB - Aula 02 - Exercício
Autor: Jefferson Andrade Agostinho

## Create database

```
use be-mean-pokemons
switched to db be-mean-pokemons
db
be-mean-pokemons
```

## List all databases

```
show dbs
local             → 0.078GB
be-mean-instagram → 0.078GB
```

## List all collections

```
show collections
```

## Insert pokemons

```
dev(mongod-3.0.7) be-mean-pokemons> var pokemon1 = {'name': 'Ivysaur', 'description': 'Há um botão na parte de trás deste Pokémon.', 'type': 'grama', 'attack': 65, 'height': 1.0, 'defense': 48}
dev(mongod-3.0.7) be-mean-pokemons> var pokemon2 = {'name': 'Charizard', 'description': 'Charizard voa em torno do céu em busca de adversários poderosos.', 'type': 'fogo', 'attack': 85, 'height': 1.7, 'defense': 65}
dev(mongod-3.0.7) be-mean-pokemons> var pokemon3 = {'name': 'Metapod', 'description': 'O escudo que cobre o corpo deste Pokémon é tão duro como uma laje de ferro.', 'type': 'inseto', 'attack': 45, 'height': 0.7, 'defense': 36}
dev(mongod-3.0.7) be-mean-pokemons> var pokemon4 = {'name': 'Pidgeout', 'description': 'Este Pokémon tem uma plumagem deslumbrante de penas lindamente brilhantes.', 'type': 'passaro', 'attack': 77, 'height': 1.5, 'defense': 68}
dev(mongod-3.0.7) be-mean-pokemons> var pokemon5 = {'name': 'Arbok', 'description': 'Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo.', 'type': 'veneno', 'attack': 63, 'height': 3.5, 'defense': 59}
dev(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon1)
Inserted 1 record(s) in 181ms
WriteResult({
  "nInserted": 1
})
dev(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon2)
Inserted 1 record(s) in 15ms
WriteResult({
  "nInserted": 1
})
dev(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon3)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
dev(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon4)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
dev(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon5)
Inserted 1 record(s) in 6ms
WriteResult({
  "nInserted": 1
})
```

## List pokemons

```
dev(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5644ab4e4d97fd165a5e4f3b"),
  "name": "Ivysaur",
  "description": "Há um botão na parte de trás deste Pokémon.",
  "type": "grama",
  "attack": 65,
  "height": 1,
  "defense": 48
}
{
  "_id": ObjectId("5644ab524d97fd165a5e4f3c"),
  "name": "Charizard",
  "description": "Charizard voa em torno do céu em busca de adversários poderosos.",
  "type": "fogo",
  "attack": 85,
  "height": 1.7,
  "defense": 65
}
{
  "_id": ObjectId("5644ab544d97fd165a5e4f3d"),
  "name": "Metapod",
  "description": "O escudo que cobre o corpo deste Pokémon é tão duro como uma laje de ferro.",
  "type": "inseto",
  "attack": 45,
  "height": 0.7,
  "defense": 36
}
{
  "_id": ObjectId("5644ab574d97fd165a5e4f3e"),
  "name": "Pidgeout",
  "description": "Este Pokémon tem uma plumagem deslumbrante de penas lindamente brilhantes.",
  "type": "passaro",
  "attack": 77,
  "height": 1.5,
  "defense": 68
}
{
  "_id": ObjectId("5644ab594d97fd165a5e4f3f"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo.",
  "type": "veneno",
  "attack": 63,
  "height": 3.5,
  "defense": 59
}
Fetched 5 record(s) in 4ms
```

## Find pokemon

```
dev(mongod-3.0.7) be-mean-pokemons> var q = {name: 'Charizard'}
dev(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(q)
dev(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("5644ab524d97fd165a5e4f3c"),
  "name": "Charizard",
  "description": "Charizard voa em torno do céu em busca de adversários poderosos.",
  "type": "fogo",
  "attack": 85,
  "height": 1.7,
  "defense": 65
}
```

## Modify pokemon

```
dev(mongod-3.0.7) be-mean-pokemons> poke.description = 'Cospe fogo'
Cospe fogo
dev(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("5644ab524d97fd165a5e4f3c"),
  "name": "Charizard",
  "description": "Cospe fogo",
  "type": "fogo",
  "attack": 85,
  "height": 1.7,
  "defense": 65
}
dev(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
