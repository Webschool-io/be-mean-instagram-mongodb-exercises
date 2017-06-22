# MongoDB - Aula 03 - Exercício
autor: Rafael Ferreira Vianna

## 1 - Liste todos Pokemons com a altura **menor que** 0.5;

  ```
  > var query = {height: {$lt:0.5}}
  > db.pokemons.find(query).pretty()
  {
          "_id" : ObjectId("5818caf539d16dd9016d8567"),
          "name" : "Pikachu",
          "description" : "Pokemon mais famoso",
          "type" : "electric",
          "attack" : 100,
          "height" : 0.4
  }
  {
          "_id" : ObjectId("5818cb5c39d16dd9016d8568"),
          "name" : "Bulbassauro",
          "description" : "Chicote de trepadeira",
          "type" : "grama",
          "attack" : 49,
          "height" : 0.4
  }
  {
          "_id" : ObjectId("5818cbaf39d16dd9016d856b"),
          "name" : "Caterpie",
          "description" : "Larva lutadora",
          "type" : "inseto",
          "attack" : 30,
          "height" : 0.3,
          "defense" : 35
  }


  ```

## 2 - Liste todos Pokemons com a altura **maior ou igual que** 0.5

  ```
  > var query = {height: {$gte: 0.5}}
  > db.pokemons.find(query).pretty()
  {
          "_id" : ObjectId("5818cb5c39d16dd9016d8569"),
          "name" : "Charmander",
          "description" : "Esse é o cão chupando manga de fofinho",
          "type" : "fogo",
          "attack" : 52,
          "height" : 0.6
  }
  {
          "_id" : ObjectId("5818cb5c39d16dd9016d856a"),
          "name" : "Squirtle",
          "description" : "Ejeta água que passarinho não bebe",
          "type" : "água",
          "attack" : 48,
          "height" : 0.5
  }
  {
          "_id" : ObjectId("5818d9ffbe62272d70ee984d"),
          "name" : "Charizard",
          "description" : "Pokemon voador de fogo",
          "type" : "Fogo",
          "attack" : 40,
          "defense" : 30,
          "height" : 1.7
  }
  {
          "_id" : ObjectId("5818d9ffbe62272d70ee984e"),
          "name" : "Squirtle",
          "description" : "Tartaruga de agua",
          "type" : "Agua",
          "attack" : 30,
          "defense" : 30,
          "height" : 0.5
  }
  {
          "_id" : ObjectId("5818dbbbbe62272d70ee9850"),
          "name" : "Charizard",
          "description" : "Pokemon voador de fogo",
          "type" : "Fogo",
          "attack" : 40,
          "defense" : 30,
          "height" : 1.7
  }
  {
          "_id" : ObjectId("5818dbbbbe62272d70ee9851"),
          "name" : "Squirtle",
          "description" : "Tartaruga de agua",
          "type" : "Agua",
          "attack" : 30,
          "defense" : 30,
          "height" : 0.5
  }
  {
          "_id" : ObjectId("5818dbbbbe62272d70ee9852"),
          "name" : "Wartortle",
          "description" : "Tartaruga de agua boladona",
          "type" : "Agua",
          "attack" : 30,
          "defense" : 40,
          "height" : 1
  }
  {
          "_id" : ObjectId("5818dbbbbe62272d70ee9853"),
          "name" : "Blastoise",
          "description" : "evolução da tartaruga",
          "type" : "Agua",
          "attack" : 40,
          "defense" : 40,
          "height" : 1.6
  }
  {
          "_id" : ObjectId("5818dbbbbe62272d70ee9854"),
          "name" : "Beedrill ",
          "description" : "Abelha boladona",
          "type" : "venenoso",
          "attack" : 50,
          "defense" : 20,
          "height" : 1
  }
  >         0.000GB


  ```

## 3 - Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama;

  ```
  var query = {$and: [{height: {$lte: 0.5}} , {type: 'Grama'}]}
  db.pokemons.find(query).pretty()

  ```

## 4 - Liste todos Pokemons com o name 'Pikachu' **OU** com attack **menor ou igual que** 0.5

   ```
   > var query = {$or: [{name: 'Pikachu'} , {attack: {$lte: 0.5}}]}
   > db.pokemons.find(query).pretty()
   {
            "_id" : ObjectId("5818caf539d16dd9016d8567"),
            "name" : "Pikachu",
            "description" : "Pokemon mais famoso",
            "type" : "electric",
            "attack" : 100,
            "height" : 0.4
   }
   >

   ```

## 5 - Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com height **menor ou igual que** 0.5

  ```
  >   var query = {$and: [{attack: {$gte: 48}} , {height: {$lte: 0.5}}]}
  > db.pokemons.find(query).pretty()
  {
          "_id" : ObjectId("5818caf539d16dd9016d8567"),
          "name" : "Pikachu",
          "description" : "Pokemon mais famoso",
          "type" : "electric",
          "attack" : 100,
          "height" : 0.4
  }
  {
          "_id" : ObjectId("5818cb5c39d16dd9016d8568"),
          "name" : "Bulbassauro",
          "description" : "Chicote de trepadeira",
          "type" : "grama",
          "attack" : 49,
          "height" : 0.4
  }
  {
          "_id" : ObjectId("5818cb5c39d16dd9016d856a"),
          "name" : "Squirtle",
          "description" : "Ejeta água que passarinho não bebe",
          "type" : "água",
          "attack" : 48,
          "height" : 0.5
  }
  >

  ```
