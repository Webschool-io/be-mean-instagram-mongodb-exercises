## Criando database

victor-notebook(mongod-3.0.7) be-mean-pokemon> use be-mean-pokemon

switched to db be-mean-pokemon

## Listando databases 

victor-notebook(mongod-3.0.7) be-mean-pokemon> show dbs

be-mean-instagram → 0.078GB
local             → 0.078GB
be-mean           → 0.078GB

## Listando collections

victor-notebook(mongod-3.0.7) be-mean-pokemon> use be-mean-instagram

switched to db be-mean-instagram

victor-notebook(mongod-3.0.7) be-mean-instagram> show collections

pokemons       → 0.001MB / 0.008MB

system.indexes → 0.000MB / 0.008MB

test           → 0.000MB / 0.008MB

teste          → 0.000MB / 0.008MB

## Inserindo

victor-notebook(mongod-3.0.7) be-mean-pokemon> db.pokemons.insert({name: "Venusaur", description: "Pokemon do tipo planta", type: "planta", attack: 82, height: 2.01})
Inserted 1 record(s) in 470ms
WriteResult({
  "nInserted": 1
})

victor-notebook(mongod-3.0.7) be-mean-pokemon> db.pokemons.insert({name: "Charizard", description: "Pokemon do tipo fogo", type: "fogo", attack: 84 , height: 1.70 })
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

victor-notebook(mongod-3.0.7) be-mean-pokemon> db.pokemons.insert({name: "Blastoise", description: "Pokemon do tipo água", type: "água", attack: 83 , height: 1.60  })
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

victor-notebook(mongod-3.0.7) be-mean-pokemon> db.pokemons.insert ({name: "Gyarados", description: "Pokemon do tipo água", type: "água", attack: 125 , height: 6.20  })
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

victor-notebook(mongod-3.0.7) be-mean-pokemon> db.pokemons.insert({name: "Eevee", description: "Pokemon do tipo normal", type: "normal", attack: 55 , height: 0.30  })
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})

victor-notebook(mongod-3.0.7) be-mean-pokemon> db.pokemons.insert({name: "Dragonite", description: "Pokemon do tipo dragão", type: "dragão", attack: 134 , height: 2.21 })
Inserted 1 record(s) in 0ms
WriteResult({
  "nInserted": 1
})

victor-notebook(mongod-3.0.7) be-mean-pokemon> db.pokemons.insert({name: "Mewtwo", description: "Pokemon do tipo psiquico", type: "psiquico", attack: 110 , height: 2.01})
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

## Listando os pokemons

victor-notebook(mongod-3.0.7) be-mean-pokemon> db.pokemons.find()
{
  "_id": ObjectId("564d292a99f90d5badf595f2"),
  "name": "Venusaur",
  "description": "Pokemon do tipo planta",
  "type": "planta",
  "attack": 82,
  "height": 2.01
}
{
  "_id": ObjectId("564d29c599f90d5badf595f3"),
  "name": "Charizard",
  "description": "Pokemon do tipo fogo",
  "type": "fogo",
  "attack": 84,
  "height": 1.7
}
{
  "_id": ObjectId("564d2a2e99f90d5badf595f4"),
  "name": "Blastoise",
  "description": "Pokemon do tipo água",
  "type": "água",
  "attack": 83,
  "height": 1.6
}
{
  "_id": ObjectId("564d2ab799f90d5badf595f5"),
  "name": "Gyarados",
  "description": "Pokemon do tipo água",
  "type": "água",
  "attack": 125,
  "height": 6.2
}
{
  "_id": ObjectId("564d2c53ae0289ce30af7d34"),
  "name": "Eevee",
  "description": "Pokemon do tipo normal",
  "type": "normal",
  "attack": 55,
  "height": 0.3
}
{
  "_id": ObjectId("564d2cc6ae0289ce30af7d35"),
  "name": "Dragonite",
  "description": "Pokemon do tipo dragão",
  "type": "dragão",
  "attack": 134,
  "height": 2.21
}
{
  "_id": ObjectId("564d2d56ae0289ce30af7d36"),
  "name": "Mewtwo",
  "description": "Pokemon do tipo psiquico",
  "type": "psiquico",
  "attack": 110,
  "height": 2.01
}
Fetched 7 record(s) in 2ms

## Buscando pokemon

victor-notebook(mongod-3.0.7) be-mean-pokemon> var query = {name: "Eevee"}
victor-notebook(mongod-3.0.7) be-mean-pokemon> var poke = db.pokemons.findOne(query)
victor-notebook(mongod-3.0.7) be-mean-pokemon> poke
{
  "_id": ObjectId("564d2c53ae0289ce30af7d34"),
  "name": "Eevee",
  "description": "Pokemon do tipo normal",
  "type": "normal",
  "attack": 55,
  "height": 0.3
}

## Atualizando pokemon

victor-notebook(mongod-3.0.7) be-mean-pokemon> poke.description = "Pokemon muito fofinho do tipo normal"
Pokemon muito fofinho do tipo normal
victor-notebook(mongod-3.0.7) be-mean-pokemon> db.pokemons.save(poke)
Updated 1 existing record(s) in 36ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

