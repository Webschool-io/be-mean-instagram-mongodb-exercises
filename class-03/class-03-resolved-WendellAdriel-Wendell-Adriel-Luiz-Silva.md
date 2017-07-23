# MongoDB - Aula 03 - Exercício

Autor: Wendell Adriel Luiz Silva

#### FORA DA AULA, APENAS INSERINDO ALGUNS POKEMONS PARA A AULA

  ```
  var pokemons = [
    {'name' : 'Pikachu', 'description' : 'Litlle electric rat', 'type' : 'Electric', 'attack' : 55, 'defense' : 40, height: 0.4},
    {'name' : 'CrazyCrazy', 'description' : 'WTF?', 'type' : 'Unknown', 'attack' : 0.2, 'defense' : 1000, height: 10},
    {'name' : 'Ignotum', 'description' : '???', 'type' : 'God', 'attack' : 9999, 'defense' : 9999, height: 0.3},
    {'name' : 'Green Monkey', 'description' : 'A green monkey', 'type' : 'Grama', 'attack' : 15, 'defense' : 10, height: 0.4}
  ]
  db.pokemons.insert(pokemons)
  ```
  
## Primeira Busca - Pokémons com Altura menor que 0.5

  ```
  var query = {height : {$lt : 0.5}}
  db.pokemons.find(query)
    {
      "_id": ObjectId("5650e591e7ee21934619f40c"),
      "name": "Pikachu",
      "description": "Litlle electric rat",
      "type": "Electric",
      "attack": 55,
      "defense": 40,
      "height": 0.4
    }
    {
      "_id": ObjectId("5650e591e7ee21934619f40e"),
      "name": "Ignotum",
      "description": "???",
      "type": "God",
      "attack": 9999,
      "defense": 9999,
      "height": 0.3
    }
    {
      "_id": ObjectId("5650e591e7ee21934619f40f"),
      "name": "Green Monkey",
      "description": "A green monkey",
      "type": "Grama",
      "attack": 15,
      "defense": 10,
      "height": 0.4
    }
    Fetched 3 record(s) in 1ms
  ```

## Segunda Busca - Pokémons com Altura maior ou igual a 0.5

  ```
  var query = {height : {$gte : 0.5}}
  db.pokemons.find(query)
    {
      "_id": ObjectId("5650d23912f8327a9f2708c2"),
      "name": "Feraligatr",
      "description": "Great Crocodile",
      "type": "Water",
      "attack": 105,
      "defense": 100,
      "height": 23
    }
    {
      "_id": ObjectId("5650d23912f8327a9f2708c3"),
      "name": "Scizor",
      "description": "Insect of Metal",
      "type": "Bug/Steel",
      "attack": 130,
      "defense": 100,
      "height": 18
    }
    {
      "_id": ObjectId("5650d23912f8327a9f2708c4"),
      "name": "Salamence",
      "description": "A Dragon...",
      "type": "Flying/Dragon",
      "attack": 135,
      "defense": 80,
      "height": 15
    }
    {
      "_id": ObjectId("5650d23912f8327a9f2708c5"),
      "name": "Charizard",
      "description": "Fire breathing and flying lizard",
      "type": "Flying/Fire",
      "attack": 84,
      "defense": 78,
      "height": 17
    }
    {
      "_id": ObjectId("5650d23912f8327a9f2708c6"),
      "name": "Alakazam",
      "description": "Hungry, always with two spoons",
      "type": "Psychic",
      "attack": 50,
      "defense": 45,
      "height": 15
    }
    {
      "_id": ObjectId("5650d23912f8327a9f2708c7"),
      "name": "Tyranitar",
      "description": "Looks like Godzilla a lil bit",
      "type": "Rock/Dark",
      "attack": 134,
      "defense": 110,
      "height": 20
    }
    {
      "_id": ObjectId("5650d23912f8327a9f2708c8"),
      "name": "Lugia",
      "description": "Motherfucker Legendary Psychic Bird",
      "type": "Flying/Psychic",
      "attack": 90,
      "defense": 130,
      "height": 52
    }
    {
      "_id": ObjectId("5650d23912f8327a9f2708c9"),
      "name": "Rayquaza",
      "description": "Lendary motherfucker dragon",
      "type": "Flying/Dragon",
      "attack": 150,
      "defense": 90,
      "height": 70
    }
    {
      "_id": ObjectId("5650e591e7ee21934619f40d"),
      "name": "CrazyCrazy",
      "description": "WTF?",
      "type": "Unknown",
      "attack": 0.2,
      "defense": 1000,
      "height": 10
    }
    Fetched 9 record(s) in 6ms
  ```

## Terceira Busca - Pokémons com Altura menor ou igual a 0.5 E do Tipo Grama

  ```
  var query = {$and : [{type : 'Grama'}, {height : {$lte : 0.5}}]}
  db.pokemons.find(query)
    {
      "_id": ObjectId("5650e591e7ee21934619f40f"),
      "name": "Green Monkey",
      "description": "A green monkey",
      "type": "Grama",
      "attack": 15,
      "defense": 10,
      "height": 0.4
    }
    Fetched 1 record(s) in 0ms
  ```

## Quarta Busca - Pokémons com nome 'Pikachu' OU Ataque menor ou igual a 0.5

  ```
  var query = {$or : [{name : 'Pikachu'}, {attack : {$lte : 0.5}}]}
  db.pokemons.find(query)
    {
      "_id": ObjectId("5650e591e7ee21934619f40c"),
      "name": "Pikachu",
      "description": "Litlle electric rat",
      "type": "Electric",
      "attack": 55,
      "defense": 40,
      "height": 0.4
    }
    {
      "_id": ObjectId("5650e591e7ee21934619f40d"),
      "name": "CrazyCrazy",
      "description": "WTF?",
      "type": "Unknown",
      "attack": 0.2,
      "defense": 1000,
      "height": 10
    }
    Fetched 2 record(s) in 1ms
  ```

## Quinta Busca - Pokémons com Ataque maior ou igual a 48 E Altura menor ou igual a 0.5

  ```
  var query = {$and : [{attack : {$gte : 48}}, {height : {$lte : 0.5}}]}
  db.pokemons.find(query)
    {
      "_id": ObjectId("5650e591e7ee21934619f40c"),
      "name": "Pikachu",
      "description": "Litlle electric rat",
      "type": "Electric",
      "attack": 55,
      "defense": 40,
      "height": 0.4
    }
    {
      "_id": ObjectId("5650e591e7ee21934619f40e"),
      "name": "Ignotum",
      "description": "???",
      "type": "God",
      "attack": 9999,
      "defense": 9999,
      "height": 0.3
    }
    Fetched 2 record(s) in 1ms
  ```
