# MongoDB - Aula 02 - Exercício
autor: Kalyane Lordao

## Criando database be-mean-pokemons
```
McProKaneLordao:~ KalyaneLordao$ mongo
MongoDB shell version: 3.2.6
connecting to: test
Mongo-Hacker 0.0.13
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) test> use be-mean-pokemons
switched to db be-mean-pokemons
```
## Listando databases
```
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> show dbs
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
be-mean-pokemons  → 0.000GB
```
## Listando Collections
```
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> show collections
pokemons → 0.001MB / 0.016MB
```
## Cadastrando Pokemons
```
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> db.pokemons.insert({'name': 'Charizard', 'description': 'Largatão macho crescido com fogo no rabo', 'type':'Fogo', attack:84 , height: 1.7 })
Inserted 1 record(s) in 11ms
WriteResult({
  "nInserted": 1
})

Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> db.pokemons.insert({'name': 'Arbok', 'description': 'Cobra do mal', 'type':'Peçonhenta', attack:85 , height: 3.5})
Inserted 1 record(s) in 12ms
WriteResult({
  "nInserted": 1
})

Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> db.pokemons.insert({'name': 'Raticate', 'description': 'Ratinho fofinho', 'type':'Normal', attack:81 , height: 0.7 })
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})

Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> db.pokemons.insert({'name': 'Blastoise', 'description': 'Um brutal pokémon aquático', 'type':'Água', attack:83 , height: 1.6 })
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> db.pokemons.insert({'name': 'Pidgeotto', 'description': 'Um passarinho muito brabo', 'type':'Voador', attack:60 , height: 1.09 })
Inserted 1 record(s) in 6ms
WriteResult({
  "nInserted": 1
})
```
## Listagem dos Pokemons
```
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("579cebc1f7a15b9683241d6d"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("579ceda3f7a15b9683241d6e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("579cee1ff7a15b9683241d6f"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("579cee41f7a15b9683241d70"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5
}
{
  "_id": ObjectId("579cf1d0a2c8c6550de3cd6f"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
{
  "_id": ObjectId("579d0d58771cc61fbc9550bd"),
  "name": "Charizard",
  "description": "Largatão macho crescido com fogo no rabo",
  "type": "Fogo",
  "attack": 84,
  "height": 1.7
}
{
  "_id": ObjectId("579d0e8b771cc61fbc9550be"),
  "name": "Arbok",
  "description": "Cobra do mal",
  "type": "Peçonhenta",
  "attack": 85,
  "height": 3.5
}
{
  "_id": ObjectId("579d0f4a771cc61fbc9550bf"),
  "name": "Raticate",
  "description": "Ratinho fofinho",
  "type": "Normal",
  "attack": 81,
  "height": 0.7
}
{
  "_id": ObjectId("579d0ff5771cc61fbc9550c0"),
  "name": "Blastoise",
  "description": "Um brutal pokémon aquático",
  "type": "Água",
  "attack": 83,
  "height": 1.6
}
{
  "_id": ObjectId("579d10cc771cc61fbc9550c1"),
  "name": "Pidgeotto",
  "description": "Um passarinho muito brabo",
  "type": "Voador",
  "attack": 60,
  "height": 1.09
}
```
## Buscando Pokemon e armazenando na variável poke
```
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> var query = {name:'Blastoise'}
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> poke
{
  "_id": ObjectId("579d0ff5771cc61fbc9550c0"),
  "name": "Blastoise",
  "description": "Um forte pokémon aquático",
  "type": "Água",
  "attack": 83,
  "height": 1.6
}
```
## Atualização da description
```
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> poke.description = "Um brutal pokemon aquatico"
Um brutal pokemon aquatico
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 9ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
