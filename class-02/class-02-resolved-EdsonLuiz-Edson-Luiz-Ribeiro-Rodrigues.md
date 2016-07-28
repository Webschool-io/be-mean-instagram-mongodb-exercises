# MongoDB - Aula 01 - Exercício
autor: Edson Luiz Ribeiro Rodrigues

## Criar database chamada be-mean-pokemons

```
mac(mongod-3.2.7) be-mean-teste> use be-mean-pokemons
switched to db be-mean-pokemons
mac(mongod-3.2.7) be-mean-pokemons>
```

##  Listar databases

```
mac(mongod-3.2.7) be-mean-pokemons> show dbs
be-mean       → 0.005GB
be-mean-teste → 0.000GB
local         → 0.000GB
mac(mongod-3.2.7) be-mean-pokemons>
```

## Listar as collections da database be-mean-pokemons
```
mac(mongod-3.2.7) be-mean-pokemons> show collections
mac(mongod-3.2.7) be-mean-pokemons>
```

## Inserir 5 pokemons

```
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert({name:"Krabby", description: "Krabby live on beaches, burrowed inside holes dug into the sand. On sandy beaches with little in the way of food, these Pokémon can be seen squabbling with each other over territory.", attack: 105, defense:90, height:0.4})
Inserted 1 record(s) in 11ms
WriteResult({
  "nInserted": 1
})
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert({name:"Cresselia", description: "Shiny particles are released from its wings like a veil. It is said to represent the crescent moon.", attack: 70, defense:120, height:15})
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert({name:"Gothorita", description: "Starlight is the source of their power. At night, they mark star positions by using psychic power to float stones.", attack: 45, defense:70, height:0.7})
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert({name:"Floette", description: "It flutters around fields of flowers and cares for flowers that are starting to wilt. It draws out the hidden power of flowers to battle.", attack: 45, defense:47, height:0.2})
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert({name:"Gorebyss", description: "Gorebyss lives in the southern seas at extreme depths. Its body is built to withstand the enormous pressure of water at incredible depths. Because of this, this Pokémon's body is unharmed by ordinary attacks.", attack: 84, defense:105, height:1.8})
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert({name:"Milotic", description: "Milotic is said to be the most beautiful of all the Pokémon. It has the power to becalm such emotions as anger and hostility to quell bitter feuding.", attack: 60, defense:79, height:6.2})
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
mac(mongod-3.2.7) be-mean-pokemons>

```

## Listar os pokemons da collection pokemons

```
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5777e96678dc84ee3b361f70"),
  "name": "Krabby",
  "description": "Krabby live on beaches, burrowed inside holes dug into the sand. On sandy beaches with little in the way of food, these Pokémon can be seen squabbling with each other over territory.",
  "attack": 105,
  "defense": 90,
  "height": 0.4
}
{
  "_id": ObjectId("5777e97f78dc84ee3b361f71"),
  "name": "Cresselia",
  "description": "Shiny particles are released from its wings like a veil. It is said to represent the crescent moon.",
  "attack": 70,
  "defense": 120,
  "height": 15
}
{
  "_id": ObjectId("5777e98b78dc84ee3b361f72"),
  "name": "Gothorita",
  "description": "Starlight is the source of their power. At night, they mark star positions by using psychic power to float stones.",
  "attack": 45,
  "defense": 70,
  "height": 0.7
}
{
  "_id": ObjectId("5777e99878dc84ee3b361f73"),
  "name": "Floette",
  "description": "It flutters around fields of flowers and cares for flowers that are starting to wilt. It draws out the hidden power of flowers to battle.",
  "attack": 45,
  "defense": 47,
  "height": 0.2
}
{
  "_id": ObjectId("5777e9a278dc84ee3b361f74"),
  "name": "Gorebyss",
  "description": "Gorebyss lives in the southern seas at extreme depths. Its body is built to withstand the enormous pressure of water at incredible depths. Because of this, this Pokémon's body is unharmed by ordinary attacks.",
  "attack": 84,
  "defense": 105,
  "height": 1.8
}
{
  "_id": ObjectId("5777e9ab78dc84ee3b361f75"),
  "name": "Milotic",
  "description": "Milotic is said to be the most beautiful of all the Pokémon. It has the power to becalm such emotions as anger and hostility to quell bitter feuding.",
  "attack": 60,
  "defense": 79,
  "height": 6.2
}
Fetched 6 record(s) in 3ms
mac(mongod-3.2.7) be-mean-pokemons>
```

## Buscar um pokemon e armazenar na variável poke

```
mac(mongod-3.2.7) be-mean-pokemons> var queryPokemon = {name: 'Gorebyss'}
mac(mongod-3.2.7) be-mean-pokemons> var poke = db.pokemons.findOne(queryPokemon)
mac(mongod-3.2.7) be-mean-pokemons> poke
{
  "_id": ObjectId("5777e9a278dc84ee3b361f74"),
  "name": "Gorebyss",
  "description": "Gorebyss lives in the southern seas at extreme depths. Its body is built to withstand the enormous pressure of water at incredible depths. Because of this, this Pokémon's body is unharmed by ordinary attacks.",
  "attack": 84,
  "defense": 105,
  "height": 1.8
}
mac(mongod-3.2.7) be-mean-pokemons>
```

## Alterar e salvar a descrição do pokemon escolhido

```
mac(mongod-3.2.7) be-mean-pokemons> poke.description
Gorebyss lives in the southern seas at extreme depths. Its body is built to withstand the enormous pressure of water at incredible depths. Because of this, this Pokémon's body is unharmed by ordinary attacks.
mac(mongod-3.2.7) be-mean-pokemons> poke.description = "Nova descrição"
Nova descrição
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
mac(mongod-3.2.7) be-mean-pokemons> var poke = db.pokemons.findOne(queryPokemon)
mac(mongod-3.2.7) be-mean-pokemons> poke
{
  "_id": ObjectId("5777e9a278dc84ee3b361f74"),
  "name": "Gorebyss",
  "description": "Nova descrição",
  "attack": 84,
  "defense": 105,
  "height": 1.8
}
mac(mongod-3.2.7) be-mean-pokemons>
```
