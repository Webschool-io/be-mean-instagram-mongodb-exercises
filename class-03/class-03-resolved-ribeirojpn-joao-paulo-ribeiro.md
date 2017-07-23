# MongoDB - Aula 03 - Exercício
autor: João Paulo Ribeiro


## Liste todos Pokemons com a altura menor que 0.5

  ```
  joao-Inspiron-5437(mongod-2.4.9) be-mean-instagram> var query = {height:{$lt:0.5}}
  joao-Inspiron-5437(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
  {
    "_id": ObjectId("5643a29682df34495fb683a0"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "height": 0.4
  }
  {
    "_id": ObjectId("5643a2e882df34495fb683a1"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
  }
  {
    "_id": ObjectId("5643a42a82df34495fb683a4"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35
  }
  Fetched 3 record(s) in 3ms

  ```

## Liste todos Pokemons com a altura maior ou igual que 0.5

  ```
  joao-Inspiron-5437(mongod-2.4.9) be-mean-instagram> var query = {height:{$gte:0.5}}
  joao-Inspiron-5437(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
  {
    "_id": ObjectId("5643a3a482df34495fb683a2"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6
  }
  {
    "_id": ObjectId("5643a3ab82df34495fb683a3"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5
  }
  Fetched 2 record(s) in 3ms

  ```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama

  ```
  joao-Inspiron-5437(mongod-2.4.9) be-mean-instagram> var query = {$and:[{height:{$lte:0.5}},{type:'grama'}]}
  joao-Inspiron-5437(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
  {
    "_id": ObjectId("5643a2e882df34495fb683a1"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
  }
  Fetched 1 record(s) in 0ms

  ```
## Liste todos Pokemons com o name 'Pikachu' OU com attack menor ou igual que 0.5

  ```
  joao-Inspiron-5437(mongod-2.4.9) be-mean-instagram> var query = {$or:[{name:'Pikachu'},{attack:{$lte:0.5}}]}
  joao-Inspiron-5437(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
  {
    "_id": ObjectId("5643a29682df34495fb683a0"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "height": 0.4
  }
  Fetched 1 record(s) in 1ms

  ```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5

  ```
  joao-Inspiron-5437(mongod-2.4.9) be-mean-instagram> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
  joao-Inspiron-5437(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
  {
    "_id": ObjectId("5643a29682df34495fb683a0"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "height": 0.4
  }
  {
    "_id": ObjectId("5643a2e882df34495fb683a1"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
  }
  {
    "_id": ObjectId("5643a3ab82df34495fb683a3"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5
  }
  Fetched 3 record(s) in 5ms

  ```
