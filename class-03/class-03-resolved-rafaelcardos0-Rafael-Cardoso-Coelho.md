# MongoDB - Aula 03 - Exercício
autor: RAFAEL CARDOSO COELHO

## 1. Listar todos os pokemons com altura menor que 0.5
```
var query = {height: {$lt: 0.5}}
db.pokemons.find(query)

{
    "_id": ObjectId("567d940bdc3c391d5ec3769b"),
    "name": "Pikachu",
    "description": "Ratinho elétrico amarelo",
    "attack": 55,
    "defense": 40,
    "height": 0.41
}
{
    "_id": ObjectId("567d94d1dc3c391d5ec3769d"),
    "name": "Cartepie",
    "description": "Lagartinha marota",
    "attack": 30,
    "defense": 35,
    "height": 0.3
}
Fetched 2 record(s) in 51ms
```

## 2. Listar todos os pokemons com altura maior ou igual que 0.5
```
var query = {height: {$gte: 0.5}}
db.pokemons.find(query)

{
    "_id": ObjectId("567d9484dc3c391d5ec3769c"),
    "name": "Charizard",
    "description": "Dragão foda cuspidor de fogo",
    "attack": 84,
    "defense": 78,
    "height": 1.7
}
{
    "_id": ObjectId("567d952cdc3c391d5ec3769e"),
    "name": "Jigglypuff",
    "description": "Kirby de franja cantor",
    "attack": 45,
    "defense": 20,
    "height": 0.51
}
{
    "_id": ObjectId("567d9581dc3c391d5ec3769f"),
    "name": "Snorlax",
    "description": "Pokemon gordinho",
    "attack": 110,
    "defense": 65,
    "height": 2.11
}
Fetched 3 record(s) in 4ms
```

## 3. Listar todos os pokemons com altura menor ou igual que 0.5 e do tipo grama 
```
var query = {$and: [{height: {lte: 0.5}}, {tipo: "grama"}]}
db.pokemons.find(query)

Fetched 0 record(s) in 1ms
```

## 4. Listar todos os pokemons com o nome Pikachu ou com attack menor ou igual que 0.5
```
var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
db.pokemons.find(query)

{
    "_id": ObjectId("567d940bdc3c391d5ec3769b"),
    "name": "Pikachu",
    "description": "Ratinho elétrico amarelo",
    "attack": 55,
    "defense": 40,
    "height": 0.41
}
Fetched 1 record(s) in 1ms
```

## 5. Listar todos os pokemons com o attack maior ou igual que 48 e com height menor ou igual que 0.5
```
var query = {$or: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
db.pokemons.find(query)

{
    "_id": ObjectId("567d940bdc3c391d5ec3769b"),
    "name": "Pikachu",
    "description": "Ratinho elétrico amarelo",
    "attack": 55,
    "defense": 40,
    "height": 0.41
}
{
    "_id": ObjectId("567d9484dc3c391d5ec3769c"),
    "name": "Charizard",
    "description": "Dragão foda cuspidor de fogo",
    "attack": 84,
    "defense": 78,
    "height": 1.7
}
{
    "_id": ObjectId("567d94d1dc3c391d5ec3769d"),
    "name": "Cartepie",
    "description": "Lagartinha marota",
    "attack": 30,
    "defense": 35,
    "height": 0.3
}
{
    "_id": ObjectId("567d9581dc3c391d5ec3769f"),
    "name": "Snorlax",
    "description": "Pokemon gordinho",
    "attack": 110,
    "defense": 65,
    "height": 2.11
}
Fetched 4 record(s) in 4ms
```
