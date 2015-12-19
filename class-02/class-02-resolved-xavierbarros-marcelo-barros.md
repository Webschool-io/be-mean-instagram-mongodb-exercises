# MongoDB - Aula 02 - Exercício

autor: Marcelo Barros

## Crie uma database chamada be-mean-pokemons

maba(mongod-3.0.7) be-mean-instagram> use be-mean-pokemons

## Liste quais databases você possui nesse servidor

maba(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean → 0.078GB
local   → 0.078GB

## Liste quais coleções você possui nessa database

maba(mongod-3.0.7) be-mean-pokemons> use be-mean
switched to db be-mean

maba(mongod-3.0.7) be-mean> show collections
pokemons       →  0.001MB /  0.008MB
restaurantes   → 14.012MB / 21.465MB
system.indexes →  0.000MB /  0.008MB
teste          →  0.000MB /  0.008MB

maba(mongod-3.0.7) be-mean> use local
switched to db local
maba(mongod-3.0.7) local> show collections
startup_log    → 0.005MB / 10.000MB
system.indexes → 0.000MB /  0.008MB

maba(mongod-3.0.7) local> use be-mean-pokemons
switched to db be-mean-pokemons

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height

maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Bulbasaur','description':'Introduzido na Geração 1, é conhecido como Pokémon Semente', attack: 49, defense: 49, height: 0.71}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 135ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Charmander','description':'Introduzido na Geração 1, é conhecido como Pokémon Lagarto', attack: 52, defense: 43, height: 0.61}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Squirtle','description':'Introduzido na Geração 1, é conhecido como Pequena Tartaruga Pokémon', attack: 48, defense: 65, height: 0.51}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Caterpie','description':'Introduzido na Geração 1, é conhecido como Verme Pokémon', attack: 30, defense: 35, height: 0.30}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Weedle','description':'Introduzido na Geração 1, é conhecido como Pokémon Inseto Peludo', attack: 35, defense: 30, height: 0.30}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Pidgey','description':'Introduzido na Geração 1, é conhecido como Pokémon Passarinho', attack: 45, defense: 40, height: 0.30}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Rattata','description':'Introduzido na Geração 1, é conhecido como Pokémon Rato', attack: 56, defense: 35, height: 0.30}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Spearow','description':'Introduzido na Geração 1, é conhecido como Pokémon Passarinho', attack: 60, defense: 30, height: 0.30}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Ekans','description':'Introduzido na Geração 1, é conhecido como Pokémon Cobra', attack: 60, defense: 44, height: 2.01}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Pikachu','description':'Introduzido na Geração 1, é conhecido como Pokémon Rato', attack: 55, defense: 40, height: 0.41}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Sandshrew','description':'Introduzido na Geração 1, é conhecido como Pokémon Rato', attack: 75, defense: 85, height: 0.61}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Nidoran','description':'Introduzido na Geração 1, é conhecido como Pokémon do Espinho Venenoso', attack: 47, defense: 52, height: 0.41}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Clefairy','description':'Introduzido na Geração 1, é conhecido como Pokémon Fada', attack: 45, defense: 48, height: 0.61}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Vulpix','description':'Introduzido na Geração 1, é conhecido como Pokémon Raposa', attack: 41, defense: 40, height: 0.61}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Jigglypuff','description':'Introduzido na Geração 1, é conhecido como Pokémon Balão', attack: 45, defense: 20, height: 0.51}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Zubat','description':'Introduzido na Geração 1, é conhecido como Pokémon Morcego', attack: 45, defense: 35, height: 0.79}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Oddish','description':'Introduzido na Geração 1, é conhecido como Pokémon Erva-Daninha', attack: 50, defense: 55, height: 0.51}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Paras','description':'Introduzido na Geração 1, é conhecido como Pokémon Cogumelo', attack: 70, defense: 55, height: 0.30}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Venonat','description':'Introduzido na Geração 1, é conhecido como Pokémon Inseto', attack: 55, defense: 50, height: 0.99}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

## Liste os pokemons existentes na sua coleção

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564919d5d6663c31c553380a"),
  "name": "Bulbasaur",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Semente",
  "attack": 49,
  "defense": 49,
  "height": 0.71
}

{
  "_id": ObjectId("56491a36d6663c31c553380b"),
  "name": "Charmander",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Lagarto",
  "attack": 52,
  "defense": 43,
  "height": 0.61
}

{
  "_id": ObjectId("56491aa0d6663c31c553380c"),
  "name": "Squirtle",
  "description": "Introduzido na Geração 1, é conhecido como Pequena Tartaruga Pokémon",
  "attack": 48,
  "defense": 65,
  "height": 0.51
}

{
  "_id": ObjectId("56491afdd6663c31c553380d"),
  "name": "Caterpie",
  "description": "Introduzido na Geração 1, é conhecido como Verme Pokémon",
  "attack": 30,
  "defense": 35,
  "height": 0.3
}

{
  "_id": ObjectId("56491b8bd6663c31c553380e"),
  "name": "Weedle",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Inseto Peludo",
  "attack": 35,
  "defense": 30,
  "height": 0.3
}

{
  "_id": ObjectId("56491c19d6663c31c553380f"),
  "name": "Pidgey",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 45,
  "defense": 40,
  "height": 0.3
}

{
  "_id": ObjectId("56491c70d6663c31c5533810"),
  "name": "Rattata",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 56,
  "defense": 35,
  "height": 0.3
}

{
  "_id": ObjectId("56491cadd6663c31c5533811"),
  "name": "Spearow",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 60,
  "defense": 30,
  "height": 0.3
}

{
  "_id": ObjectId("56491d2dd6663c31c5533812"),
  "name": "Ekans",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cobra",
  "attack": 60,
  "defense": 44,
  "height": 2.01
}

{
  "_id": ObjectId("56491d6ad6663c31c5533813"),
  "name": "Pikachu",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}

{
  "_id": ObjectId("56491d9fd6663c31c5533814"),
  "name": "Sandshrew",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 75,
  "defense": 85,
  "height": 0.61
}

{
  "_id": ObjectId("56491e0ad6663c31c5533815"),
  "name": "Nidoran",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon do Espinho Venenoso",
  "attack": 47,
  "defense": 52,
  "height": 0.41
}

{
  "_id": ObjectId("56491e50d6663c31c5533816"),
  "name": "Clefairy",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Fada",
  "attack": 45,
  "defense": 48,
  "height": 0.61
}

{
  "_id": ObjectId("56491e7fd6663c31c5533817"),
  "name": "Vulpix",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Raposa",
  "attack": 41,
  "defense": 40,
  "height": 0.61
}

{
  "_id": ObjectId("56491ec2d6663c31c5533818"),
  "name": "Jigglypuff",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Balão",
  "attack": 45,
  "defense": 20,
  "height": 0.51
}

{
  "_id": ObjectId("56491f1cd6663c31c5533819"),
  "name": "Zubat",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Morcego",
  "attack": 45,
  "defense": 35,
  "height": 0.79
}

{
  "_id": ObjectId("56491f6bd6663c31c553381a"),
  "name": "Oddish",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Erva-Daninha",
  "attack": 50,
  "defense": 55,
  "height": 0.51
}

{
  "_id": ObjectId("56491fabd6663c31c553381b"),
  "name": "Paras",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cogumelo",
  "attack": 70,
  "defense": 55,
  "height": 0.3
}

{
  "_id": ObjectId("56491fe1d6663c31c553381c"),
  "name": "Venonat",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Inseto",
  "attack": 55,
  "defense": 50,
  "height": 0.99
}

Fetched 19 record(s) in 5ms

## Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`

maba(mongod-3.0.7) be-mean-pokemons> var query = {name:'Nidoran'}

maba(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.find(query)

maba(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("56491e0ad6663c31c5533815"),
  "name": "Nidoran",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon do Espinho Venenoso",
  "attack": 47,
  "defense": 52,
  "height": 0.41
}

Fetched 1 record(s) in 1ms

## Modifique sua `description` e salvê-o

maba(mongod-3.0.7) be-mean-pokemons> poke.description = 'Introduzido na Geração 1, é conhecido como Pokemón Venenoso'

Introduzido na Geração 1, é conhecido como Pokemón Venenoso

maba(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("56491e0ad6663c31c5533815"),
  "name": "Nidoran",
  "description": "Introduzido na Geração 1, é conhecido como Pokemón Venenoso",
  "attack": 47,
  "defense": 52,
  "height": 0.41
}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms

WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})