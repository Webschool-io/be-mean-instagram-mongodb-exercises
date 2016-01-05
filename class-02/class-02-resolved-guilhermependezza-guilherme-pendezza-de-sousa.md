#Criando o database

guilherme-notebook(mongod-3.0.7) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons

#Mostrando os dbs
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
local             → 0.078GB
restaurantes      → 0.078GB
be-mean           → 0.078GB
test              → 0.078GB

#Mostrando as collections (ainda não tinha nenhuma =) )
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> show collections
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>

#Inserindo os pokemons
var pokemons = [

  {name: "Pidgeotto", description: "Um quero-quero dos pokemons", type: "voador", attack: 30, height: 1.1},
  {name: "Arbok", description: "Cobra burra da equipe Rocket", type: "venenoso", attack: 40, height: 3.5},
  {name: "Jigglypuff", description: "Pokemon que cau... zzzzzzzzzzz...", type: "fada", attack: 20, height: 0.5},
  {name: "Arcanine", description: "Cachorro que corre que só a porra", type: "fogo", attack: 60, height: 1.9},
  {name: "Psyduck", description: "Só tem dor de cabeça", type: "água", attack: 30, height: 0.8}
];

guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 430ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>

#Listando os pokemons

guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find();
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
  "description": "Cachorro que corre que só a porra",
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
Fetched 5 record(s) in 4ms
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>


#Alterando a descrição do Arcanine

guilherme-notebook(mongod-3.0.7) be-mean-pokemons> var q = {name: 'Arcanine'}
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(q)
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> poke.description = 'Cachorro fofinho =)'
Cachorro fofinho =)
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 9ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>
