## 1. Liste todos Pokemons com a altura menor que 0.5;
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> var query = {height: {$lt: 0.5}}
blsrocks(mongod-3.2.8) be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
blsrocks(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57af6f3292ac5d57da5217bb"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("57af6f4192ac5d57da5217bc"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57af6f7692ac5d57da5217bf"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3
}
Fetched 3 record(s) in 4ms

```
## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> query = {height: {$gte: 0.5}}
{
  "height": {
    "$gte": 0.5
  }
}
blsrocks(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57af6f5092ac5d57da5217bd"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("57af6f6292ac5d57da5217be"),
  "name": "Squirtle",
  "description": "Ejeta água zikada",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 33ms

```
## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]}
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": /grama/
    }
  ]
}
blsrocks(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57af6f4192ac5d57da5217bc"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 71ms

```
## 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> query = {$or: [{name: /pikachu/i}, {attack: {$lte: 0.5}}]}
{
  "$or": [
    {
      "name": /pikachu/i
    },
    {
      "attack": {
        "$lte": 0.5
      }
    }
  ]
}
blsrocks(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57af6f3292ac5d57da5217bb"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 3ms

```
## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> query = {$and: [{attack: {$gte: 48}},{height: {$lte: 0.5}}]}
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
blsrocks(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57af6f3292ac5d57da5217bb"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("57af6f4192ac5d57da5217bc"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57af6f6292ac5d57da5217be"),
  "name": "Squirtle",
  "description": "Ejeta água zikada",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 4ms

```