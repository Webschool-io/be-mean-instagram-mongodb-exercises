# MongoDB - Aula 02 - Exercício
autor: Diêgo Bolina

#1 - Crie uma database chamada be-mean-pokemons
Diegos-MacBook-Pro(mongod-3.2.0) test> use be-mean-pokemons

#2 - Liste quais databases você possui nesse servidor
Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> show databases
be-mean-instagram → 0.000GB
be-mean-sky       → 0.004GB
local             → 0.000GB

#3 - Liste quais coleções você possui nessa database
Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> show collections
Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons>

#4 - Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado : name, description, attack, defense e height;

Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> var pokemon = [{"name": "Pikachu","description": "Rato Elétrico bem fofinho","type": "electric","attack": 55, "height": 0.4},{"name": "Diglett","description": "Diglett are raised in most farms","type": "ground","attack": 55,"height": 2},{"name": "Mewtwo","description": "Mewtwo is a Pokémon that was created by genetic manipulation","type": "Physic","attack": 110,"height": 2},{"name": "Abra","description": "Abra sleeps for eighteen hours a day","type": "Physic","attack": 20,"height": 0.9},{"name": "Spearow","description": "Spearow has a very loud cry that can be heard over half a mile away.","type": "Tinybird","attack": 60,"height": 0.3}]

Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 26ms
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

#5 - Liste os pokemons existentes na sua coleção;
Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("566f7a8eabd4340bccd4c61d"),
  "name": "Pikachu",
  "description": "Rato Elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("566f7a8eabd4340bccd4c61e"),
  "name": "Diglett",
  "description": "Diglett are raised in most farms",
  "type": "ground",
  "attack": 55,
  "height": 2
}
{
  "_id": ObjectId("566f7a8eabd4340bccd4c61f"),
  "name": "Mewtwo",
  "description": "Mewtwo is a Pokémon that was created by genetic manipulation",
  "type": "Physic",
  "attack": 110,
  "height": 2
}
{
  "_id": ObjectId("566f7a8eabd4340bccd4c620"),
  "name": "Abra",
  "description": "Abra sleeps for eighteen hours a day",
  "type": "Physic",
  "attack": 20,
  "height": 0.9
}
{
  "_id": ObjectId("566f7a8eabd4340bccd4c621"),
  "name": "Spearow",
  "description": "Spearow has a very loud cry that can be heard over half a mile away.",
  "type": "Tinybird",
  "attack": 60,
  "height": 0.3
}
Fetched 5 record(s) in 3ms


#6 - Busque os pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada 'poke';

Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> var query = {name: "Spearow"}
Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> poke = db.pokemons.findOne(query)

{
  "_id": ObjectId("566f7a8eabd4340bccd4c621"),
  "name": "Spearow",
  "description": "Spearow has a very loud cry that can be heard over half a mile away.",
  "type": "Tinybird",
  "attack": 60,
  "height": 0.3
}

#7 - modifique sua 'description' e salve

Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> poke.description = 'Changing description of Spearow'
Changing description of Spearow

Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("566f7a8eabd4340bccd4c621"),
  "name": "Spearow",
  "description": "Changing description of Spearow",
  "type": "Tinybird",
  "attack": 60,
  "height": 0.3
}
