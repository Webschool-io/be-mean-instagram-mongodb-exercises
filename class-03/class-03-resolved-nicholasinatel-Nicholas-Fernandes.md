# MongoDB - Aula 03 - Exercício
autor: Nicholas Fernandes de Almeida Paolillo
## Liste todos Pokemons com a altura **menor que** 0.5;
```
be-mean-instagram> var query = {height: {$lt: 0.5}}
be-mean-instagram> query
{
  "height": {
    "$lt": 0.5
  }
}
```
```
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5678403db851c1d5742cb98f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("567840acb851c1d5742cb990"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("567844c4b851c1d5742cb993"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 3ms
```
## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
be-mean-instagram> var query = {height: {$gte: 0.5}}
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("567840e6b851c1d5742cb991"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5678416eb851c1d5742cb992"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 6ms
```
## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
be-mean-instagram> var query = {$and:[{height: {$lte: 0.5}},{type: "grama"}]}
be-mean-instagram> query
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
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("567840acb851c1d5742cb990"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 4ms
```
## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
be-mean-instagram> var query = {$or:[{height: {$lte: 0.5}},{name: /pikachu/i"}]}
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5678403db851c1d5742cb98f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("567840acb851c1d5742cb990"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5678416eb851c1d5742cb992"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("567844c4b851c1d5742cb993"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 4 record(s) in 4ms
```
## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
be-mean-instagram> var query = {$and:[{attack:{$gte: 48}},{height:{$lte: 0.5}}]}
be-mean-instagram> query
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
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5678403db851c1d5742cb98f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("567840acb851c1d5742cb990"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5678416eb851c1d5742cb992"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 4ms
```
