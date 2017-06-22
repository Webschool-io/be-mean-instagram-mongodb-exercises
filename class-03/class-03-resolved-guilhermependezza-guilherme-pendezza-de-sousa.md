# 1 - Pokemons com altura menor que 0.5
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> var query = { height: { $lt: 0.5} }
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>


# 2 - Pokemons com altura maior ou igual que 0.5
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> var query = { height: { $gte: 0.5} }
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5666ebdeb4f0168b575fe0af"),
  "name": "Pidgeotto",
  "description": "Um quero-quero dos pokemons",
  "type": "voador",
  "attack": 30,
  "height": 1.1
}
{
  "_id": ObjectId("5666ebdeb4f0168b575fe0b0"),
  "name": "Arbok",
  "description": "Cobra burra da equipe Rocket",
  "type": "venenoso",
  "attack": 40,
  "height": 3.5
}
{
  "_id": ObjectId("5666ebdeb4f0168b575fe0b1"),
  "name": "Jigglypuff",
  "description": "Pokemon que cau... zzzzzzzzzzz...",
  "type": "fada",
  "attack": 20,
  "height": 0.5
}
{
  "_id": ObjectId("5666ebdeb4f0168b575fe0b2"),
  "name": "Arcanine",
  "description": "Cachorro fofinho =)",
  "type": "fogo",
  "attack": 60,
  "height": 1.9
}
{
  "_id": ObjectId("5666ebdeb4f0168b575fe0b3"),
  "name": "Psyduck",
  "description": "Só tem dor de cabeça",
  "type": "água",
  "attack": 30,
  "height": 0.8
}
Fetched 5 record(s) in 2ms
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>


# 3 - Pokemons com altura menor ou igual que 0.5 e do tipo grama
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> var query1 = { height: { $lte: 0.5} }
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> var query2 = { type: 'grama' }
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$and: [query1, query2]})
Fetched 0 record(s) in 1ms
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>


# 4 - Pokemons com nome 'Pikachu' ou attack menor ou igual que 0.5
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> var query1 = { name: 'Pikachu' }
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> var query2 = { attack: { $lte: 0.5} }
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$or: [query1, query2]})
Fetched 0 record(s) in 0ms
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>


# 5 - Pokemons com attack maior ou igual que 48 e height menor ou igual que 0.5
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> var query1 = { attack: { $gte: 48} }
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> var query2 = { height: { $lte: 0.5} }
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$and: [query1, query2]})
Fetched 0 record(s) in 0ms
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>
