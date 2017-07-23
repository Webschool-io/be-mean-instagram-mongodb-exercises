# MongoDB - Aula 03 - Exercício
autor: Átila Delcanton Rampazo

## Liste todos Pokemons com a altura **menor que** 0.5
```
arampazo(mongod-3.0.8) be-mean-instagram> var query = {height:{$lt:0.5}}
arampazo(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("568041b5fa9be201c4c3a4b0"),
  "name": "Pikachu",
  "descriptionn": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("568042cffa9be201c4c3a4b1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 1ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
arampazo(mongod-3.0.8) be-mean-instagram> var query = {height:{$gte:0.5}}
arampazo(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("568042e7fa9be201c4c3a4b2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56804317fa9be201c4c3a4b3"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("568043cbfa9be201c4c3a4b4"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "fogo",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5680452cfa9be201c4c3a4b5"),
  "name": "Ekans",
  "description": "Cobrinha da equipe Rocket",
  "type": "Poison",
  "attack": 30,
  "height": 2,
  "defense": 35
}
Fetched 4 record(s) in 2ms

```
## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
arampazo(mongod-3.0.8) be-mean-instagram> var  query = {$and :[{height: {$lte: 0.5}}, {type:'grama'}] }
arampazo(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("568042cffa9be201c4c3a4b1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
arampazo(mongod-3.0.8) be-mean-instagram> var query = {$or:[{name:'Pikachu'},{attack:{$lte:0.5}}]
arampazo(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("568041b5fa9be201c4c3a4b0"),
  "name": "Pikachu",
  "descriptionn": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 0ms

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que**  0.5

```
arampazo(mongod-3.0.8) be-mean-instagram> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}] }
arampazo(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("568041b5fa9be201c4c3a4b0"),
  "name": "Pikachu",
  "descriptionn": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("568042cffa9be201c4c3a4b1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("568043cbfa9be201c4c3a4b4"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "fogo",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 1ms

```
