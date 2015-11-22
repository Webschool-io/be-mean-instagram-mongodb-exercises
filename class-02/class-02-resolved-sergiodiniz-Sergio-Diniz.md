# MongoDB - Aula 02 - Exercício
autor: SERGIO DINIZ CORREIA

## Listagem das databases (passo 2)
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB

## Listagem das coleções (passo 3)
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> show collections
pokemons       → 0.002MB / 0.008MB
system.indexes → 0.000MB / 0.008MB


## Cadastro dos pokemons (passo 4)
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Krabby','description':'Krabby live on beaches, burrowed inside holes dug into the sand. On sandy beaches with little in the way of food, these Pokémon can be seen squabbling with each other over territory.','type': 'Water', attack: 55, height: 0.4 }
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 194ms
WriteResult({
  "nInserted": 1
})
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Kingler','description':'Kingler has an enormous, oversized claw. It waves this huge claw in the air to communicate with others. However, because the claw is so heavy, the Pokémon quickly tires.','type': 'Water', attack: 55, height: 1.3 }
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Voltorb','description':'Voltorb was first sighted at a company that manufactures Poké Balls. The link between that sighting and the fact that this Pokémon looks very similar to a Poké Ball remains a mystery.','type': 'Water', attack: 55, height: 0.5 }
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Electrode','description':'Electrode eats electricity in the atmosphere. On days when lightning strikes, you can see this Pokémon exploding all over the place from eating too much electricity.','type': 'Water', attack: 55, height: 1.2 }
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Exeggcute','description':'This Pokémon consists of six eggs that form a closely knit cluster. The six eggs attract each other and spin around. When cracks increasingly appear on the eggs, Exeggcute is close to evolution.','type': 'Water', attack: 55, height: 0.4 }
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

## Lista dos pokemons (passo 5)

Sergios-MBP(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564b2cc2de86e4e06dfe93b3"),
  "name": "Krabby",
  "description": "Krabby live on beaches, burrowed inside holes dug into the sand. On sandy beaches with little in the way of food, these Pokémon can be seen squabbling with each other over territory.",
  "type": "Water",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564b2d18de86e4e06dfe93b4"),
  "name": "Kingler",
  "description": "Kingler has an enormous, oversized claw. It waves this huge claw in the air to communicate with others. However, because the claw is so heavy, the Pokémon quickly tires.",
  "type": "Water",
  "attack": 55,
  "height": 1.3
}
{
  "_id": ObjectId("564b2d42de86e4e06dfe93b5"),
  "name": "Voltorb",
  "description": "Voltorb was first sighted at a company that manufactures Poké Balls. The link between that sighting and the fact that this Pokémon looks very similar to a Poké Ball remains a mystery.",
  "type": "Water",
  "attack": 55,
  "height": 0.5
}
{
  "_id": ObjectId("564b2d66de86e4e06dfe93b6"),
  "name": "Electrode",
  "description": "Electrode eats electricity in the atmosphere. On days when lightning strikes, you can see this Pokémon exploding all over the place from eating too much electricity.",
  "type": "Water",
  "attack": 55,
  "height": 1.2
}
{
  "_id": ObjectId("564b2d8cde86e4e06dfe93b7"),
  "name": "Exeggcute",
  "description": "This Pokémon consists of six eggs that form a closely knit cluster. The six eggs attract each other and spin around. When cracks increasingly appear on the eggs, Exeggcute is close to evolution.",
  "type": "Water",
  "attack": 55,
  "height": 0.4
}
Fetched 5 record(s) in 10ms

## Voltorb (passo 6)
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> var query = {name: 'Voltorb'}
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.find(query)
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("564b2d42de86e4e06dfe93b5"),
  "name": "Voltorb",
  "description": "Voltorb was first sighted at a company that manufactures Poké Balls. The link between that sighting and the fact that this Pokémon looks very similar to a Poké Ball remains a mystery.",
  "type": "Water",
  "attack": 55,
  "height": 0.5
}
Fetched 1 record(s) in 5ms

## Atualização do Voltorb (passo 6)
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> poke.description
Voltorb was first sighted at a company that manufactures Poké Balls. The link between that sighting and the fact that this Pokémon looks very similar to a Poké Ball remains a mystery.
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> poke.description = 'nova descricao :)'
nova descricao :)
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 8ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Sergios-MBP(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("564b2d42de86e4e06dfe93b5"),
  "name": "Voltorb",
  "description": "nova descricao :)",
  "type": "Water",
  "attack": 55,
  "height": 0.5
}


