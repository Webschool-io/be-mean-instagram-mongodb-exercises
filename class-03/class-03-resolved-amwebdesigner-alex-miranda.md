# MongoDB - Aula 03 - Exercício
autor: Alex de Miranda

## Pokemons com altura menor que 0.5

Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = {height:{$lt:0.5}}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("564beba64b6d7ef94f2db0da"),
    "name": "Weedle",
    "description": "tem o olfato bem apurado",
    "attack": 35,
    "defense": 30,
    "height": 0.3,
    "type": "veneno"
}
Fetched 1 record(s) in 1ms

## Pokemons com altura maior ou igual que 0.5

Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = {height:{$gte:0.5}}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("564beb614b6d7ef94f2db0d9"),
    "name": "Butterfree",
    "description": "tem uma capacidade superior de procurar delicioso mel de flo
res",
    "attack": 45,
    "defense": 50,
    "height": 1.1,
    "type": "vôo"
}
{
    "_id": ObjectId("564bebe04b6d7ef94f2db0db"),
    "name": "Kakuna",
    "description": "permanece parado numa arvore até sua evolução",
    "attack": 25,
    "defense": 50,
    "height": 0.6,
    "type": "veneno"
}
{
    "_id": ObjectId("564bec004b6d7ef94f2db0dc"),
    "name": "Beedrill",
    "description": "Extremamente territorial, ninguém deve se aproximar do seu n
inho",
    "attack": 90,
    "defense": 40,
    "height": 1,
    "type": "veneno"
}
Fetched 3 record(s) in 2ms

## Pokemons com altura menor ou igual que 0.5 E do tipo veneno

Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = {$and:[{height: {$lte:0.5}}, {type:"veneno"}]}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("564beba64b6d7ef94f2db0da"),
    "name": "Weedle",
    "description": "tem o olfato bem apurado",
    "attack": 35,
    "defense": 30,
    "height": 0.3,
    "type": "veneno"
}
Fetched 1 record(s) in 1ms
## Pokemons com nome Beedrill OU com attack menor ou igual que 0.5

Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = {$or:[{name:"Beedrill"}, {attack:{$lte:0.5}}]}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("564bec004b6d7ef94f2db0dc"),
    "name": "Beedrill",
    "description": "Extremamente territorial, ninguém deve se aproximar do seu n
inho",
    "attack": 90,
    "defense": 40,
    "height": 1,
    "type": "veneno"
}
Fetched 1 record(s) in 1ms
## Pokemons com attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5

Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = {$and:[{atta
ck:{$gte:48}}, {height:{$lte:0.5}}]}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms