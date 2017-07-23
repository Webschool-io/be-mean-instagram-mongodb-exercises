# MongoDB - Aula 03 - Exercício
autor: Mateus Cerezini Gomes

## Liste todos Pokemons com a altura **menor que** 0.5
```
var query = {height: {$lt: 0.5}}
matrix(mongod-3.0.7) be-mean-instagram> query
{
  "height": {
    "$lt": 0.5
  }
}
matrix(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5642781cc41db98ac1c42f13"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56427a13c41db98ac1c42f14"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56427befc41db98ac1c42f17"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 15
}
```
## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
var query = {height: {$gte: 0.5}}
matrix(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56427a37c41db98ac1c42f15"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56427a58c41db98ac1c42f16"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}

```
## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
var query = {$and: [{height: {$lte: 0.5}},{type:'grama'}]}
matrix(mongod-3.0.7) be-mean-instagram> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": "grama"
    }
  ]
}
matrix(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56427a13c41db98ac1c42f14"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}

```
## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
var query = {$or: [{attack: {$lte: 0.5}},{name:'Pikachu'}]}
matrix(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5642781cc41db98ac1c42f13"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}

```
## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
 var query = {$and: [{attack: {$gte: 48}},{height: {$lte: 0.5}}]}
matrix(mongod-3.0.7) be-mean-instagram> query
{
  "$and": [
    {
      "attack": {
        "$gte": 48
      }
    },
    {
      "height": {
        "$lte": 0.5
      }
    }
  ]
}
matrix(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5642781cc41db98ac1c42f13"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56427a13c41db98ac1c42f14"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56427a58c41db98ac1c42f16"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}

```
