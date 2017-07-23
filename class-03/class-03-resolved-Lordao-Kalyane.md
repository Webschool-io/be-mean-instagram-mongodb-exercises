# MongoDB - Aula 03 - Exercício
autor: Kalyane Lordao


## Listar todos os Pokémons com altura menor que 0.5.
```
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> var query = {height: {$lt:0.5}}
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("579cebc1f7a15b9683241d6d"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
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
  "_id": ObjectId("579cf1d0a2c8c6550de3cd6f"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 17ms
```
## Listar todos os Pokémons com altura maior/igual a 0.5.
```
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> var query = {height: {$gte:0.5}}
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> query
{
  "height": {
    "$gte": 0.5
  }
}
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("579ceda3f7a15b9683241d6e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
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
  "description": "Um brutal pokemon aquatico",
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
Fetched 7 record(s) in 9ms
```
## Listar todos os Pokémons com altura menor/igual a 0.5 e do tipo Grama.
```
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> var query = {$and: [{height:0.5} , {type:'grama'}]}
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> query
{
  "$and": [
    {
      "height": 0.5
    },
    {
      "type": "grama"
    }
  ]
}
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 10ms
```
### Listar todos os Pokémons com nome Pikachu ou com ataque menor ou igual a 0.5.
```
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> var query = {$or: [{name:'Pikachu'} , { type:'grama'}]}
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> query
{
  "$or": [
    {
      "name": "Pikachu"
    },
    {
      "type": "grama"
    }
  ]
}
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("579cebc1f7a15b9683241d6d"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("579cee1ff7a15b9683241d6f"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 23ms
``
## Listar todos os Pokémons com ataque maior que 48 e com altura menor/igual a 0.5.
```
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> var query = {$and: [{attack: {$gt:48}}, {height: {$lte:0.4}}]}
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> query
{
  "$and": [
    {
      "attack": {
        "$gt": 48
      }
    },
    {
      "height": {
        "$lte": 0.4
      }
    }
  ]
}
Mc-Pro-Kalyane-Lordao(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("579cebc1f7a15b9683241d6d"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("579cee1ff7a15b9683241d6f"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 12ms
```
