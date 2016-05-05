# MongoDB - Aula 02 - Exercício
autor: Jadir J. Silva Junior

## Listagem das databases (passo 2)
```
ubuntu(mongod-3.0.7) test> show dbs
clothes-store        → 0.078GB
local                → 0.078GB
be-mean-restaurantes → 0.078GB
be-mean-instagram    → 0.078GB
test                 → 0.078GB
be-mean              → 0.078GB
be-mean-pokemons     → 0.078GB
```

## Listagem das coleções (passo 3)
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> show collections
pokemons       → 0.001MB / 0.008MB
system.indexes → 0.000MB / 0.008MB
```

## Cadastro dos pokemons (passo 4)
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.insert({name:"Bulbasaur", description:"Bulbasaur is a Grass/Poison type pokemon. It is known as the 'Seed Pokemon'", attack:49, defense: 49, height:0.71})
Inserted 1 record(s) in 430ms
WriteResult({
  "nInserted": 1
})

ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.insert({name:"Charmander", description:"Charmander is a Fire type pokemon. It is known as the 'Lizard Pokemon'", attack:52, defense: 43, height:0.61})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.insert({name:"Squirtle", description:"Squirtle is a Water type pokemon. It is known as the 'Turtle Pokemon'", attack:48, defense: 65, height:0.51})
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.insert({name:"Caterpie", description:"Caterpir is a Bug type pokemon. It is known as the 'Worm Pokemon'", attack:30, defense: 35, height:0.30})
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})

ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.insert({name:"Weedle", description:"Weedle is a Bug/Poison type pokemon. It is known as the 'Hairy Pokemon'", attack:35, defense: 30, height:0.30})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
```

## Lista dos pokemons (passo 5)
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.find()
{
  "_id": ObjectId("565849392d2ce8b8b6eeb13c"),
  "name": "Bulbasaur",
  "description": "Bulbasaur is a Grass/Poison type pokemon. It is known as the 'Seed Pokemon'",
  "attack": 49,
  "defense": 49,
  "height": 0.71
}
{
  "_id": ObjectId("5658499f2d2ce8b8b6eeb13d"),
  "name": "Charmander",
  "description": "Charmander is a Fire type pokemon. It is known as the 'Lizard Pokemon'",
  "attack": 52,
  "defense": 43,
  "height": 0.61
}
{
  "_id": ObjectId("56584a072d2ce8b8b6eeb13e"),
  "name": "Squirtle",
  "description": "Squirtle is a Water type pokemon. It is known as the 'Turtle Pokemon'",
  "attack": 48,
  "defense": 65,
  "height": 0.51
}
{
  "_id": ObjectId("56584a582d2ce8b8b6eeb13f"),
  "name": "Caterpie",
  "description": "Caterpir is a Bug type pokemon. It is known as the 'Worm Pokemon'",
  "attack": 30,
  "defense": 35,
  "height": 0.3
}
{
  "_id": ObjectId("56584aa22d2ce8b8b6eeb140"),
  "name": "Weedle",
  "description": "Weedle is a Bug/Poison type pokemon. It is known as the 'Hairy Pokemon'",
  "attack": 35,
  "defense": 30,
  "height": 0.3
}
Fetched 5 record(s) in 20ms
```

## Lista de um Pokemon a escolha (passo 6)
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var poke = db.pokemons.findOne({name: /caterpie/i})
ubuntu(mongod-3.0.7) be-mean-pokemons-01> poke
{
  "_id": ObjectId("56584a582d2ce8b8b6eeb13f"),
  "name": "Caterpie",
  "description": "Caterpir is a Bug type pokemon. It is known as the 'Worm Pokemon'",
  "attack": 30,
  "defense": 35,
  "height": 0.3
}
```

## Atualização do Caterpie na description (passo 6)
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> poke.description = "Caterpie is a Bug type pokemon. It is known as the 'Worm Pokpoke.description = "Caterpie is a Bug type pokemon. It is known as the 'Worm Pokemon'"
Caterpie is a Bug type pokemon. It is known as the 'Worm Pokemon'
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.save(poke)
Updated 1 existing record(s) in 9ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
