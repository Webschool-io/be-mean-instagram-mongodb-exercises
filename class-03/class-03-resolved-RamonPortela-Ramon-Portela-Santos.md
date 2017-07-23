# MongoDB - Aula 03 - Exercício
autor: Ramon Portela Santos

## Liste todos Pokemons com a altura **menor que** 0.5;
```
Ramon-PC(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}
Ramon-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5653b457fa99ff3fb905d720"),
  "name": "Pidgey",
  "description": "Um passarinho",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "type": "Voador"
}
Fetched 1 record(s) in 5ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
Ramon-PC(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
Ramon-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565231fe6c327d14f3798b58"),
  "name": "Sudowoodo",
  "description": "Uma árvore engraçada",
  "attack": 100,
  "defense": 115,
  "height": 1.2,
  "type": "Pedra"
}
{
  "_id": ObjectId("565232466c327d14f3798b59"),
  "name": "Arbok",
  "description": "Mata a cobra e mostra o pau",
  "attack": 85,
  "defense": 69,
  "height": 3.5,
  "type": "Veneno"
}
{
  "_id": ObjectId("565232996c327d14f3798b5a"),
  "name": "Nidoran",
  "description": "Um rato com chifre de unicórnio",
  "attack": 57,
  "defense": 40,
  "height": 0.5,
  "type": "Veneno"
}
{
  "_id": ObjectId("565232ee6c327d14f3798b5b"),
  "name": "Jynx",
  "description": "Filha do senhor popo",
  "attack": 50,
  "defense": 35,
  "height": 1.4,
  "type": "Psiquico"
}
{
  "_id": ObjectId("565233746c327d14f3798b5c"),
  "name": "Doduo",
  "description": "Duas cabeças pensam melhor que uma",
  "attack": 85,
  "defense": 45,
  "height": 1.4,
  "type": "Voador"
}
Fetched 5 record(s) in 11ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo voador
```
Ramon-PC(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: "Voador"}]}
Ramon-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5653b457fa99ff3fb905d720"),
  "name": "Pidgey",
  "description": "Um passarinho",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "type": "Voador"
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
Ramon-PC(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: "Arbok"}, {attack: {$lte: 0.5}}]}
Ramon-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565232466c327d14f3798b59"),
  "name": "Arbok",
  "description": "Mata a cobra e mostra o pau",
  "attack": 85,
  "defense": 69,
  "height": 3.5,
  "type": "Veneno"
}
Fetched 1 record(s) in 2ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
Ramon-PC(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
Ramon-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("565232996c327d14f3798b5a"),
  "name": "Nidoran",
  "description": "Um rato com chifre de unicórnio",
  "attack": 57,
  "defense": 40,
  "height": 0.5,
  "type": "Veneno"
}
Fetched 1 record(s) in 1ms
```