
# MongoDB - Aula 03 - Exercício
autor: Roland Gabriel

## Liste todos Pokemons com a altura **menor que** 0.5;
    var query = {height: {$lt: 0.5}}

```
Roland(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56480b9de7df842a0d3aaaf7"),
  "name": "Weedle",
  "description": "Weedle has an extremely acute sense of smell.",
  "attack": 20,
  "defense": 20,
  "height": 0.3
}
Fetched 1 record(s) in 0ms
```
## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
Roland(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56480cc6e7df842a0d3aaaf8"),
  "name": "Kakuna",
  "description": "Kakuna remains virtually immobile as it clings to a tree",
  "attack": 10,
  "defense": 20,
  "height": 0.6
}
{
  "_id": ObjectId("56480d32e7df842a0d3aaaf9"),
  "name": "Weepinbell",
  "description": "Weepinbell has a large hook on its rear end.",
  "attack": 5,
  "defense": 20,
  "height": 1
}
{
  "_id": ObjectId("56480d9be7df842a0d3aaafa"),
  "name": "Tentacool",
  "description": "O corpo do Tentacool é largamente composto por água.",
  "attack": 20,
  "defense": 20,
  "height": 0.9
}
{
  "_id": ObjectId("56480e30e7df842a0d3aaafb"),
  "name": "Golem",
  "description": "Golem live up on mountains.",
  "attack": 60,
  "defense": 60,
  "height": 1.4
}
Fetched 4 record(s) in 2ms

```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
    var query =  {$and: [{height:{$lte:0.5}},{type:"Grama"}]}

```
Roland(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56480b9de7df842a0d3aaaf7"),
  "name": "Weedle",
  "description": "Weedle has an extremely acute sense of smell.",
  "attack": 20,
  "defense": 20,
  "height": 0.3,
  "type": "Grama"
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
    var query =  {$or: [{name:"Pikachu"},{attack:{$lte:0.5}}]}

```
Roland(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```
##### Alterando um pouco pra receber algo
* var query =  {$or: [{name:"Pikachu"},{attack:{$lte:**50**}}]}
```
{
  "_id": ObjectId("56480b9de7df842a0d3aaaf7"),
  "name": "Weedle",
  "description": "Weedle has an extremely acute sense of smell.",
  "attack": 20,
  "defense": 20,
  "height": 0.3,
  "type": "Grama"
}
{
  "_id": ObjectId("56480cc6e7df842a0d3aaaf8"),
  "name": "Kakuna",
  "description": "Kakuna remains virtually immobile as it clings to a tree",
  "attack": 10,
  "defense": 20,
  "height": 0.6
}
{
  "_id": ObjectId("56480d32e7df842a0d3aaaf9"),
  "name": "Weepinbell",
  "description": "Weepinbell has a large hook on its rear end.",
  "attack": 5,
  "defense": 20,
  "height": 1
}
{
  "_id": ObjectId("56480d9be7df842a0d3aaafa"),
  "name": "Tentacool",
  "description": "O corpo do Tentacool é largamente composto por água.",
  "attack": 20,
  "defense": 20,
  "height": 0.9
}
Fetched 4 record(s) in 1ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
    var query = {$and: [{attack: {$gte:48}},{height:{$lte: 0.5}}]}
```
Roland(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56480b9de7df842a0d3aaaf7"),
  "name": "Weedle",
  "description": "Weedle has an extremely acute sense of smell.",
  "attack": 60,
  "defense": 20,
  "height": 0.3,
  "type": "Grama"
}
Fetched 1 record(s) in 0ms

```
