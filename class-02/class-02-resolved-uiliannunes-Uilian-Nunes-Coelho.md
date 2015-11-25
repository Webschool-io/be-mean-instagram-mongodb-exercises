# MongoDB - Aula 02 - Exercício
autor: Uilian Nunes Coelho

## Criando a database be-mean-pokemons (Passo 1)

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) test> use be-mean-pokemons
switched to db be-mean-pokemons

```

## Listando as databases (Passo 2)

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB

```

## Listando as coleções (Passo 3)

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> show collections

```

## Inserindo os Pokemons (Passo 4)

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var pokemons = [{
... "name":"Zubat",
... "description":"Zubat is a Poison/Flying type Pokémon introduced in Generation 1. It is known as the Bat Pokémon",
... "type": "Poison/Flying", 
... "attack": 45, 
... "height": 0.79 
... },
... {
... "name":"Jigglypuff",
... "description":"Jigglypuff is a Normal/Fairy type Pokémon introduced in Generation 1. It is known as the Balloon Pokémon",
... "type": "Fairy", 
... "attack": 45, 
... "height": 0.51 
... },
... {
... "name":"Vileplume",
... "description":"Vileplume is a Grass/Poison type Pokémon introduced in Generation 1. It is known as the Flower Pokémon",
... "type": "Grass/Poison", 
... "attack": 80, 
... "height": 1.19 
... },
... {
... "name":"Dragonite",
... "description":"Dragonite is a Dragon/Flying type Pokémon introduced in Generation 1. It is known as the Dragon Pokémon",
... "type": "Dragon/Flying", 
... "attack": 134, 
... "height": 2.21 
... },
... {
... "name":"Raichu",
... "description":"Raichu is an Electric type Pokémon introduced in Generation 1. It is known as the Mouse Pokémon",
... "type": "electric", 
... "attack": 90, 
... "height": 0.79 
... },
... {
... "name":"Pidgeot",
... "description":"Pidgeot is a Normal/Flying type Pokémon introduced in Generation 1. It is known as the Bird Pokémon",
... "type": "Flying", 
... "attack": 80, 
... "height": 1.5 
... },
... {
... "name":"Cacnea",
... "description":"Cacnea is a Grass type Pokémon introduced in Generation 3. It is known as the Cactus Pokémon.",
... "type": "Grass", 
... "attack": 85, 
... "height": 0.4 
... },
... {
... "name":"Pikachu",
... "description":"Rato elétrico bem fofinho.",
... "type": "electric", 
... "attack": 55, 
... "height": 0.4 
... }]

MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 2979ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 8,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})

```

## Listando os Pokemons (Passo 5)

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564687f79f36874a98ff79bf"),
  "name": "Zubat",
  "description": "Zubat is a Poison/Flying type Pokémon introduced in Generation 1. It is known as the Bat Pokémon",
  "type": "Poison/Flying",
  "attack": 45,
  "height": 0.79
}
{
  "_id": ObjectId("564687f79f36874a98ff79c0"),
  "name": "Jigglypuff",
  "description": "Jigglypuff is a Normal/Fairy type Pokémon introduced in Generation 1. It is known as the Balloon Pokémon",
  "type": "Fairy",
  "attack": 45,
  "height": 0.51
}
{
  "_id": ObjectId("564687f79f36874a98ff79c1"),
  "name": "Vileplume",
  "description": "Vileplume is a Grass/Poison type Pokémon introduced in Generation 1. It is known as the Flower Pokémon",
  "type": "Grass/Poison",
  "attack": 80,
  "height": 1.19
}
{
  "_id": ObjectId("564687f79f36874a98ff79c2"),
  "name": "Dragonite",
  "description": "Dragonite is a Dragon/Flying type Pokémon introduced in Generation 1. It is known as the Dragon Pokémon",
  "type": "Dragon/Flying",
  "attack": 134,
  "height": 2.21
}
{
  "_id": ObjectId("564687f79f36874a98ff79c3"),
  "name": "Raichu",
  "description": "Raichu is an Electric type Pokémon introduced in Generation 1. It is known as the Mouse Pokémon",
  "type": "electric",
  "attack": 90,
  "height": 0.79
}
{
  "_id": ObjectId("564687f79f36874a98ff79c4"),
  "name": "Pidgeot",
  "description": "Pidgeot is a Normal/Flying type Pokémon introduced in Generation 1. It is known as the Bird Pokémon",
  "type": "Flying",
  "attack": 80,
  "height": 1.5
}
{
  "_id": ObjectId("564fb465010a0d37f0f2516e"),
  "name": "Cacnea",
  "description": "Cacnea is a Grass type Pokémon introduced in Generation 3. It is known as the Cactus Pokémon.",
  "type": "Grass",
  "attack": 85,
  "height": 0.4
}
{
  "_id": ObjectId("5654f3f1cd1bdd189cd39d6e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 8 record(s) in 8ms

```

## Buscando um Pokemon e armazenando em uma variável chamada poke (Passo 6)

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {name:"Dragonite"}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var poke = db.pokemons.findOne(query)
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> poke
{
  "_id": ObjectId("564687f79f36874a98ff79c2"),
  "name": "Dragonite",
  "description": "Dragonite is a Dragon/Flying type Pokémon introduced in Generation 1. It is known as the Dragon Pokémon",
  "type": "Dragon/Flying",
  "attack": 134,
  "height": 2.21
}

```

## Modificando a description e salvando (Passo 7)

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> poke.description = "Dragãozinho do Mal"
Dragãozinho do Mal
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 30ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```