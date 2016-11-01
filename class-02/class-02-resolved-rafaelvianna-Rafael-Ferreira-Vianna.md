# MongoDB - Aula 02 - Exercício
autor: Rafael Ferreira Vianna

## 1 - Crie uma database chamada de be-mean-pokemons;

  ```
  use be-mean-pokemons

  ```

## 2 - Liste quais databases você possui nesse servidor

  ```
  show dbs
  be-mean-instagram  0.009GB
  local              0.000GB
  test               0.000GB


  ```

## 3 - Liste quais coleções você possui nessa database

  ```
  show collections
  teste

  ```

## 4 - insira pelo menos 5 pokemons **A SUA ESCOLHA** utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;

   ```
   var newPokemons = [
     {
       name: 'Charizard',
       description: 'Pokemon voador de fogo',
       type: 'Fogo',
       attack: 40,
       defense: 30,
       height: 1.7
     },
     {
       name: 'Squirtle',
       description: 'Tartaruga de agua',
       type: 'Agua',
       attack: 30,
       defense: 30,
       height: 0.5
     },
     {
       name: 'Wartortle',
       description: 'Tartaruga de agua boladona',
       type: 'Agua',
       attack: 30,
       defense: 40,
       height: 1.0
     },
     {
       name: 'Blastoise',
       description: 'evolução da tartaruga',
       type: 'Agua',
       attack: 40,
       defense: 40,
       height: 1.6
     },
     {
       name: 'Beedrill ',
       description: 'Abelha boladona',
       type: 'venenoso',
       attack: 50,
       defense: 20,
       height: 1.0
     }
   ]

   db.pokemons.save(newPokemons)
   ```

## 5 - Liste os pokemons existentes na sua coleção

  ```
  db.pokemons.find().pretty()
{
        "_id" : ObjectId("5818caf539d16dd9016d8567"),
        "name" : "Pikachu",
        "description" : "Rato elétrico bem fofinho",
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
        "_id" : ObjectId("5818cbaf39d16dd9016d856b"),
        "name" : "Caterpie",
        "description" : "Larva lutadora",
        "type" : "inseto",
        "attack" : 30,
        "height" : 0.3,
        "defense" : 35
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


  ```

## 6 - Busque o 'pikachu' e armazene-o em uma variável chamada 'poke'

  ```
  var query = {name:'Pikachu'}
  var pikachu = db.pokemons.findOne(query)
  pikachu
  {
          "_id" : ObjectId("5818caf539d16dd9016d8567"),
          "name" : "Pikachu",
          "description" : "Rato elétrico bem fofinho",
          "type" : "electric",
          "attack" : 100,
          "height" : 0.4
  }

  ```

## 7 - Modifique sua 'description' e salvê-o

  ```
  var query = {name:'Pikachu'}
  var pikachu = db.pokemons.findOne(query)
  pikachu
  {
          "_id" : ObjectId("5818caf539d16dd9016d8567"),
          "name" : "Pikachu",
          "description" : "Rato elétrico bem fofinho",
          "type" : "electric",
          "attack" : 100,
          "height" : 0.4
  }
  pikachu.description = "Pokemon mais famoso"
  Pokemon mais famoso
  db.pokemons.save(pikachu)
  WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
>

  ```
