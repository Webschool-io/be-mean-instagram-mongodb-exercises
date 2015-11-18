# MongoDB -Aula 02 - Exercicio
autor: Dennis Borba

# 1. Crie uma database chamada be-mean-pokemons
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> use be-mean-pokemons
switched to db be-mean-pokemons

# 2. Liste quais databases você possui nesse servidor
Ubuntu-pc(mongod-3.0.7) be-mean-teste> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
be-mean-pokemons  → 0.078GB
local             → 0.078GB

# 3. Liste quais coleções você possui nessa database
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> show collections
pokemon        → 0.001MB / 0.008MB
system.indexes → 0.000MB / 0.008MB

# 4. Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.insert({'name':'Metapod','description':'Casulo','type': 'inseto', 'attack': 20, height: 0.7, 'defense': 55 })
Inserted 1 record(s) in 395ms
WriteResult({
  "nInserted": 1
})
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.insert({'name':'Butterfree','description':'Borboleta','type': 'inseto voador', 'attack': 45, 'height': 1.1, 'defense': 50})
Inserted 1 record(s) in 5ms
WriteResult({
  "nInserted": 1
})
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> 
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.insert({'name':'Kakuna','description':'Inseto que permanece imóvel dentro do casulo','type': 'inseto venenoso', 'attack': 25, 'height': 0.6, 'defense': 50})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.insert({'name':'Pidgey','description':'Pequeno pássaro','type': 'voador', 'attack': 45, 'height': 0.3, 'defense': 40 })
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.insert({'name':'Sandshrew','description':'Roedor','type': 'subterrâneo', 'attack': 75, 'height': 0.6, 'defense': 85})
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.insert({'name':'Nidoking','description':'Broca','type': 'subterrâneo venenoso', 'attack': 102, 'height': 1.4, 'defense': 77})
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

# 5. Liste os pokemons existentes na sua coleção
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.find()
{
  "_id": ObjectId("5645582261e81beac8b5bd75"),
  "name": "Metapod",
  "description": "Casulo",
  "type": "inseto",
  "attack": 20,
  "height": 0.7,
  "defense": 55
}
{
  "_id": ObjectId("5645584461e81beac8b5bd76"),
  "name": "Butterfree",
  "description": "Borboleta",
  "type": "inseto voador",
  "attack": 45,
  "height": 1.1,
  "defense": 50
}
{
  "_id": ObjectId("5645587161e81beac8b5bd77"),
  "name": "Kakuna",
  "description": "Inseto que permanece imóvel dentro do casulo",
  "type": "inseto venenoso",
  "attack": 25,
  "height": 0.6,
  "defense": 50
}
{
  "_id": ObjectId("564558a761e81beac8b5bd78"),
  "name": "Pidgey",
  "description": "Pequeno pássaro",
  "type": "voador",
  "attack": 45,
  "height": 0.3,
  "defense": 40
}
{
  "_id": ObjectId("564558c361e81beac8b5bd79"),
  "name": "Sandshrew",
  "description": "Roedor",
  "type": "subterrâneo",
  "attack": 75,
  "height": 0.6,
  "defense": 85
}
{
  "_id": ObjectId("564558d361e81beac8b5bd7a"),
  "name": "Nidoking",
  "description": "Broca",
  "type": "subterrâneo venenoso",
  "attack": 102,
  "height": 1.4,
  "defense": 77
}
Fetched 6 record(s) in 7ms

# 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemon.findOne({'name': 'Pidgey'})

# 7. Modifique sua `description` e salvê-o
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> poke.description = 'Pequeno pássaro com extremo senso de direção'
Pequeno pássaro com extremo senso de direção
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.save(poke)
Updated 1 existing record(s) in 13ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


