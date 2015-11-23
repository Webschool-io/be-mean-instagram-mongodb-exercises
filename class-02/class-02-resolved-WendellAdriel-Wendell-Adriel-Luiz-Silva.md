# MongoDB - Aula 02 - Exercício

Autor: Wendell Adriel Luiz Silva

## Criando Database

  ```
  use be-mean-pokemons
    switched to db be-mean-pokemons
  ```
  
## Listando Databases

  ```
  show dbs
    local             → 0.078GB
    test              → 0.078GB
    be-mean           → 0.078GB
    be-mean-instagram → 0.078GB
  ```

## Listando Collections

  ```
  show collections
  ```

## Criando Objetos de Pokémons

  ```
  var pokemons = [
    {'name' : 'Feraligatr', 'description' : 'Great Crocodile', 'type' : 'Water', 'attack' : 105, 'defense' : 100, height: 23},
    {'name' : 'Scizor', 'description' : 'Insect of Metal', 'type' : 'Bug/Steel', 'attack' : 130, 'defense' : 100, height: 18},
    {'name' : 'Salamence', 'description' : 'A Dragon...', 'type' : 'Flying/Dragon', 'attack' : 135, 'defense' : 80, height: 15},
    {'name' : 'Charizard', 'description' : 'Fire breathing and flying lizard', 'type' : 'Flying/Fire', 'attack' : 84, 'defense' : 78, height: 17},
    {'name' : 'Alakazam', 'description' : 'Hungry, always with two spoons', 'type' : 'Psychic', 'attack' : 50, 'defense' : 45, height: 15},
    {'name' : 'Tyranitar', 'description' : 'Looks like Godzilla a lil bit', 'type' : 'Rock/Dark', 'attack' : 134, 'defense' : 110, height: 20},
    {'name' : 'Lugia', 'description' : 'Lendary big bird', 'type' : 'Flying/Psychic', 'attack' : 90, 'defense' : 130, height: 52},
    {'name' : 'Rayquaza', 'description' : 'Lendary motherfucker dragon', 'type' : 'Flying/Dragon', 'attack' : 150, 'defense' : 90, height: 70}
  ]
  ```

## Inserindo registros na Database

  ```
  db.pokemons.insert(pokemons)
    Inserted 1 record(s) in 424ms
    BulkWriteResult({
      "writeErrors": [ ],
      "writeConcernErrors": [ ],
      "nInserted": 8,
      "nUpserted": 0,
      "nMatched": 0,
      "nModified": 0,
      "nRemoved": 0,
      "upserted": [ ]
    })
  ```

## Listando Registros da Collection

  ```
  db.pokemons.find()
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
      "description": "Lendary big bird",
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
    Fetched 8 record(s) in 3ms
  ```

## Criando Query de pesquisa

  ```
  var query = {'name' : 'Lugia'}
  ```

## Buscando Registro na Database

  ```
  var poke = db.pokemons.findOne(query)
  ```

## Alterando registro buscado

  ```
  poke.description = 'Motherfucker Legendary Psychic Bird'
  ```

## Modificando Registro na Database

  ```
  db.pokemons.save(poke)
    Updated 1 existing record(s) in 6ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
  ```
