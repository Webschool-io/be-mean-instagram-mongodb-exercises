#MongoDB - Aula 03 - Exercício
autor: Werner Eduard Gutschow
## Liste todos Pokemons com a altura **menor que** 0.5;
    ```
wernerlinux(mongod-3.0.8) be-mean-instagram> var query = {height: {$lt: 0.5}}
wernerlinux(mongod-3.0.8) be-mean-instagram> db.pokemon.find(query)
    ```
{
  "_id": ObjectId("5681bb4b54a52731d0c76d43"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "Type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5681bbc554a52731d0c76d44"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "Type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5681bd3d54a52731d0c76d47"),
  "name": "Carterpie",
  "description": "Larva lutadora",
  "Type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 0ms
## Liste todos Pokemons com a altura **maior ou igual que** 0.5
    ```
wernerlinux(mongod-3.0.8) be-mean-instagram> var query = {height:{$gte: 0.5}}
wernerlinux(mongod-3.0.8) be-mean-instagram> db.pokemon.find(query)
    ```
{
  "_id": ObjectId("5681bc0b54a52731d0c76d45"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "Type": "Fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5681bc4254a52731d0c76d46"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "Type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 1ms
## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
    ```
wernerlinux(mongod-3.0.8) be-mean-instagram> var query = {$and:[{height:{$lte: 0.5 }},{Type:"grama"}]}
wernerlinux(mongod-3.0.8) be-mean-instagram> db.pokemon.find(query)
    ```
{
  "_id": ObjectId("5681bbc554a52731d0c76d44"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "Type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 0ms

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
    ```
wernerlinux(mongod-3.0.8) be-mean-instagram> var query = {$or:[{name:"Pikachu"},{attack:{$lte:0.5}}]}
wernerlinux(mongod-3.0.8) be-mean-instagram> db.pokemon.find(query)
'''
{
  "_id": ObjectId("5681bb4b54a52731d0c76d43"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "Type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 0ms

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
    ```
wernerlinux(mongod-3.0.8) be-mean-instagram> var query = {$or:[{name:"Pikachu"},{attack:{$lte:0.5}}]}
wernerlinux(mongod-3.0.8) be-mean-instagram> db.pokemon.find(query)
    ```
{
  "_id": ObjectId("5681bb4b54a52731d0c76d43"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "Type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

