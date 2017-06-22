# MongoDB - Aula 03 - Exercício
autor(a): KÉSSIA CASTRO

## Liste todos Pokemons com a altura **menor que** 0.5;

-> var query = {height: {$lt: 0.5}}

-> db.pokemons.find(query)
{
  "_id": ObjectId("56431e1f3cb17616b8b398a8"),
  "name": "Pikachu",
  "description": "Rato do tinhoso",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 4ms


## Liste todos Pokemons com a altura **maior ou igual que** 0.5

-> var query = {height: {$gte: 0.5}}

-> db.pokemons.find(query)
{
  "_id": ObjectId("56431f6a3cb17616b8b398a9"),
  "name": "Charizard",
  "description": "Diabo do fogo",
  "type": "fire",
  "attack": 84,
  "defense": 78,
  "height": 17
}
{
  "_id": ObjectId("564321083cb17616b8b398aa"),
  "name": "Jigglypuff",
  "description": "Rainha do deserto",
  "type": "fairy",
  "attack": 45,
  "defense": 20,
  "height": 5
}
{
  "_id": ObjectId("564321743cb17616b8b398ab"),
  "name": "Snorlax",
  "description": "Bicho preguiça",
  "type": "normal",
  "attack": 110,
  "defense": 65,
  "height": 21
}
{
  "_id": ObjectId("564321c93cb17616b8b398ac"),
  "name": "Ditto",
  "description": "Jogo da Imitação",
  "type": "normal",
  "attack": 48,
  "defense": 48,
  "height": 3
}
{
  "_id": ObjectId("5643222f3cb17616b8b398ad"),
  "name": "Psyduck",
  "description": "Duuuuuuh",
  "type": "water",
  "attack": 52,
  "defense": 48,
  "height": 8
}
{
  "_id": ObjectId("564322a73cb17616b8b398ae"),
  "name": "Meowth",
  "description": "Sneaky Gangsta",
  "type": "normal",
  "attack": 45,
  "defense": 35,
  "height": 4
}
Fetched 6 record(s) in 9ms

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

-> var query = {$and: [{type: 'Grass'}, {height: {$lte: 0.5}}]}

-> db.pokemons.find(query)
Fetched 0 record(s) in 0ms


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

-> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}

-> be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56431e1f3cb17616b8b398a8"),
  "name": "Pikachu",
  "description": "Rato do tinhoso",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 2ms


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

-> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}

-> db.pokemons.find(query)
{
  "_id": ObjectId("56431e1f3cb17616b8b398a8"),
  "name": "Pikachu",
  "description": "Rato do tinhoso",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 11ms

