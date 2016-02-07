```md
#MongoDB - Aula 04 - Exercício
autor: Cristyan Rossi

##1. Liste todos Pokemons com a altura menor que 4.0;

var query = {height: {$lt: 4.0}}
db.pokemons.find(query)

{
    "_id": ObjectId("56abaa3b9cae02d3cf9535b2"),
    "name": "Rattata",
    "description": "rato perigoso",
    "type": "roedor",
    "attack": 10,
    "height": 3.5
}
Fetched 2 record(s) in 3ms

##2. Liste todos Pokemons com a altura maior ou igual que 4.0;

var query = {height: {$lte: 4.0}}

db.pokemons.find(query)
{
    "_id": ObjectId("56abaa3b9cae02d3cf9535b2"),
    "name": "Rattata",
    "description": "rato perigoso",
    "type": "roedor",
    "attack": 10,
    "height": 3.5
}
{
    "_id": ObjectId("56abaa75e1c6b275ce180812"),
    "name": "Vulpix",
    "description": "raposa filhote com cauda",
    "type": "canino",
    "attack": 10,
    "height": 4.5
}
Fetched 4 record(s) in 3ms

##3. Liste todos Pokemons com a altura menor ou igual que 3.5 E do tipo roedor;

var query = {$and: [{height: {$lte: 4.5}}, {type: 'roedor'}]}
db.pokemons.find(query)
{
    "_id": ObjectId("56abaa3b9cae02d3cf9535b2"),
    "name": "Rattata",
    "description": "rato perigoso",
    "type": "roedor",
    "attack": 10,
    "height": 3.5
}
Fetched 1 record(s) in 1ms

##4. Liste todos Pokemons com o name `Kakuna` OU com attack menor ou igual que 10;

var query = {$or: [{name: 'Kakuna'i},{attack: 10}]}
db.pokemons.find(query)
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a54"),
    "name": "Pidgeotto",
    "description": "Passáro voador",
    "type": "ave",
    "attack": 10,
    "height": 30,
    "defense": 25
}
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a55"),
    "name": "Kakuna",
    "description": "inseto imóvel",
    "type": "inseto",
    "attack": 3,
    "height": 10,
    "defense": 9
}
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a56"),
    "name": "Rattata",
    "description": "rato perigoso",
    "type": "roedor",
    "attack": 10,
    "height": 3.5,
    "defense": 5
}
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a57"),
    "name": "Vulpix",
    "description": "raposa filhote",
    "type": "canino",
    "attack": 10,
    "height": 4.5,
    "defense": 6
}
Fetched 4 record(s) in 3ms

##5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 4.0;


var query = {$and: [{attack: {$gte: 30}},{height: {$lte: 4.0}}]}
db.pokemons.find(query)
Fetched 0 record(s) in 0ms
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a53"),
    "name": "Charizard",
    "description": "Dragão voador",
    "type": "inseto",
    "attack": 30,
    "height": 4.0,
    "defense": 80
}
Fetched 3 record(s) in 3ms
