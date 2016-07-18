#MongoDB - Aula 02 - Exercício
autor: Emerson Chalegre

##Criando database be-mean-pokemons
emerchalegre(mongod-3.0.12) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
emerchalegre(mongod-3.0.12) be-mean-pokemons> 

##Listar databases do servidor
emerchalegre(mongod-3.0.12) be-mean-pokemons> show dbs
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
local             → 0.078GB

##Listar collections da database
emerchalegre(mongod-3.0.12) be-mean-pokemons> show collections

##Inserir 5 pokemons
db.pokemons.insert({name:"Snorlax",description:"Pokemon que dorme e acorda pra comer", attack:60,defense:30,height:2.1})
db.pokemons.insert({name:"Eevee",description:"Mano esse cachorrinho é muito loko",attack:30,defense:20,height:0.3})
db.pokemons.insert({name:"Gyarados",description:"Dragão cobra d'agua",attack:60,defense:30,height:6.5})
db.pokemons.insert({name:"Scyther",description:"Um grilo? Um Louva Deus?",attack:60,defense:40,height:1.5})
db.pokemons.insert({name:"Abra",description:"Mister M deles",attack:10,defense:10,height:0.9})

##Listar os pokemons
emerchalegre(mongod-3.0.12) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("578c3c30d6cd81fd2f2d57cc"),
  "name": "Snorlax",
  "description": "Pokemon que dorme e acorda pra comer",
  "attack": 60,
  "defense": 30,
  "height": 2.1
}
{
  "_id": ObjectId("578c3c44d6cd81fd2f2d57cd"),
  "name": "Eevee",
  "description": "Mano esse cachorrinho é muito loko",
  "attack": 30,
  "defense": 20,
  "height": 0.3
}
{
  "_id": ObjectId("578c3c4dd6cd81fd2f2d57ce"),
  "name": "Gyarados",
  "description": "Dragão cobra d'agua",
  "attack": 60,
  "defense": 30,
  "height": 6.5
}
{
  "_id": ObjectId("578c3c57d6cd81fd2f2d57cf"),
  "name": "Scyther",
  "description": "Um grilo? Um Louva Deus?",
  "attack": 60,
  "defense": 40,
  "height": 1.5
}
{
  "_id": ObjectId("578c3c6ad6cd81fd2f2d57d0"),
  "name": "Abra",
  "description": "Mister M deles",
  "attack": 10,
  "defense": 10,
  "height": 0.9
}


##Buscar pokemon 
emerchalegre(mongod-3.0.12) be-mean-pokemons> var query = {name:"Gyarados"}
emerchalegre(mongod-3.0.12) be-mean-pokemons> var poke = db.pokemons.findOne(query)
emerchalegre(mongod-3.0.12) be-mean-pokemons> poke
{
  "_id": ObjectId("578c3c4dd6cd81fd2f2d57ce"),
  "name": "Gyarados",
  "description": "Dragão cobra d'agua",
  "attack": 60,
  "defense": 30,
  "height": 6.5
}
Fetched 1 record(s) in 10ms


##Modificar description do pokemon 
emerchalegre(mongod-3.0.12) be-mean-pokemons> poke
{
  "_id": ObjectId("578c3c4dd6cd81fd2f2d57ce"),
  "name": "Gyarados",
  "description": "Dragão cobra d'agua",
  "attack": 60,
  "defense": 30,
  "height": 6.5
}
emerchalegre(mongod-3.0.12) be-mean-pokemons> poke.description
Dragão cobra d'agua
emerchalegre(mongod-3.0.12) be-mean-pokemons> poke.description = "Isso é um dragão? Uma cobra? Uma cobra-dragão?"
Isso é um dragão? Uma cobra? Uma cobra-dragão?
emerchalegre(mongod-3.0.12) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 163ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

