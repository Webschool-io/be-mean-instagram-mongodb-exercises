## MongoDB - Aula 03 - Exercício
Author: Wellington Pinho

## 01 ==> Listar todos pokemons com height $lt:0.5
```
var query = {height: {$lt: 0.5} }

well(mongod-3.2.10) aula3> db.aula3.find(query)
{
  "_id": ObjectId("57f90876f884222f4ad899a9"),
  "name": "Pikachu",
  "description": "Rato Eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("57f90876f884222f4ad899aa"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57f90876f884222f4ad899ab"),
  "name": "Caterpiee",
  "description": "Larva lutadora ",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
{
  "_id": ObjectId("57f9089ef884222f4ad899ad"),
  "name": "Pikachu",
  "description": "Rato Eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("57f9089ef884222f4ad899ae"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57f9089ef884222f4ad899af"),
  "name": "Caterpiee",
  "description": "Larva lutadora ",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 6 record(s) in 8ms

```
## 02 ==> Listar todos pokemons com height $gte:0.5
```
well(mongod-3.2.10) aula3> var mi = {height: {$gte:0.5}}
well(mongod-3.2.10) aula3> db.aula3.find(mi)
Fetched 0 record(s) in 2ms

```

## 03 ==> Listar todos pokemons com height $lte:0.5 and tipo "grama"
```
well(mongod-3.2.10) aula3> var and = {$and: [{height: {$lte:0.5}}, {"type":"grama"}] }
well(mongod-3.2.10) aula3> db.aula3.find(and)
{
  "_id": ObjectId("57f90876f884222f4ad899aa"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57f9089ef884222f4ad899ae"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 3ms
```
## 04 ==> Listar todos pokemons com nome "Pikachu" ou com "attack" $lte:0.5
```
well(mongod-3.2.10) aula3> var ou = {$or: [{"name":"Pikachu"}, {"attack":{$lte:0.5}}] }
well(mongod-3.2.10) aula3> db.aula3.find(ou)
{
  "_id": ObjectId("57f90876f884222f4ad899a9"),
  "name": "Pikachu",
  "description": "Rato Eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("57f9089ef884222f4ad899ad"),
  "name": "Pikachu",
  "description": "Rato Eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 2 record(s) in 4ms

```
## 05 ==> Liste todos os pokemons com o attack $gte:48 e com height $lte:0.5
```
well(mongod-3.2.10) aula3> var and = {$and: [  {"attack":{$gte:48}}, {"height": {$lte: 0.5}} ] }
well(mongod-3.2.10) aula3> db.aula3.find(and)
{
  "_id": ObjectId("57f90876f884222f4ad899a9"),
  "name": "Pikachu",
  "description": "Rato Eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("57f90876f884222f4ad899aa"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57f9089ef884222f4ad899ad"),
  "name": "Pikachu",
  "description": "Rato Eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("57f9089ef884222f4ad899ae"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 4 record(s) in 4ms
```



