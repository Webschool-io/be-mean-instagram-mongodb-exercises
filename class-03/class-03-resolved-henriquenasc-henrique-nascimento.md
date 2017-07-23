# MongoDB - Aula 03 - Exercício
autor: Henrique Nascimento

##Listando os pokemons com a altura menor que 0.5 (Passo 1)
    
    be-mean-pokemon> var altMenor = {height:{$lt: 0.5}}
    
    be-mean-pokemon> db.pokemon.find(altMenor)
    Fetched 0 record(s) in 0ms

##Listando os pokemons com a altura maior ou igual que 0.5 (Passo 2)
    
    be-mean-pokemon> var maiorIgual = {height:{$gte: 0.5}}

    be-mean-pokemon> db.pokemon.find(maiorIgual)

    {
    "_id": ObjectId("58641d38c76b2123771671af"),
    "name": "Javascriptmon",
    "description": "Linguagem de programação muito foda",
    "type": "Dinamic",
    "attack": 100,
    "height": 0.7,
    "defense": 90
    }
    {
    "_id": ObjectId("58641d90c76b2123771671b0"),
    "name": "Blastoise",
    "description": "Pokemon aguatico evolução Nº 009 do Squirtle",
    "type": "Water",
    "attack": 40,
    "height": 1.6,
    "defense": 40
    }
    {
    "_id": ObjectId("58641d90c76b2123771671b1"),
    "name": "Batterfree",
    "description": "Pokemon voador",
    "type": "Bug",
    "attack": 20,
    "height": 1.1,
    "defense": 20
    }
    {
    "_id": ObjectId("58641d90c76b2123771671b2"),
    "name": "Abra",
    "description": "Pokemon que usa a mente",
    "type": "Psychic",
    "attack": 10,
    "height": 0.9,
    "defense": 10
    }
    {
    "_id": ObjectId("58641d90c76b2123771671b3"),
    "name": "Aipom",
    "description": "Pokemon macaco",
    "type": "Normal",
    "attack": 40,
    "height": 0.8,
    "defense": 30
    }
    {
    "_id": ObjectId("58641d90c76b2123771671b4"),
    "name": "Absol",
    "description": "Pokemon Dark",
    "type": "Dark",
    "attack": 70,
    "height": 1.2,
    "defense": 30
    }
    Fetched 6 record(s) in 2ms

##Listando os pokemons com a altura menor ou igual que 0.5 e do tipo grama (Passo 3)
    
    be-mean-pokemon> var query = {$and:[{height:{$lte: 0.5}},{type: 'grass'}]}

    be-mean-pokemon> db.pokemon.find(query)
    Fetched 0 record(s) in 0ms

##Listando os pokemons com o name 'Pikachu' ou com attack menor ou igual que 0.5(Passo 4)
    
    be-mean-pokemon> var query = {$or:[{name:'Pikachu'},{attack:{$lte: 0.5}}]}

    be-mean-pokemon> db.pokemon.find(query)
    Fetched 0 record(s) in 18ms

##Listando os pokemons com attack maior ou igual que 48 e com height menor ou igual que 0.5 (Passo 5)

    be-mean-pokemon> var query = {$and:[{attack:{gte:48}},{height:{lte:0.5}}]}

    be-mean-pokemon> db.pokemon.find(query)
    Fetched 0 record(s) in 0ms