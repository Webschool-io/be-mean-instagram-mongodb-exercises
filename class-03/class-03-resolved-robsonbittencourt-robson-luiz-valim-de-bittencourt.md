# MongoDB - Aula 03 - Exercício
autor: Robson Luiz Valim de Bittencourt

## Liste todos Pokemons com a altura **menor que** 0.5;

```
vostro(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt:0.5}}
vostro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648f2eef178d68ddbb81801"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "attack": 100,
  "defense": 90,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
vostro(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte:0.5}}
vostro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648c5d2e509dc2b3e263851"),
  "name": "Mewtwo",
  "description": "Because its battle abilities were raised to the ultimate level, it thinks only of de feating its foes.",
  "attack": 110,
  "defense": 90,
  "height": 20
}
{
  "_id": ObjectId("5648c5e1e509dc2b3e263852"),
  "name": "Mew",
  "description": "So rare that it is still said to be a mirage by many experts. Only a few people have seen it worldwide.",
  "attack": 100,
  "defense": 100,
  "height": 4
}
{
  "_id": ObjectId("5648c5efe509dc2b3e263853"),
  "name": "Bibarel",
  "description": "A river dammed by Bibarel will never overflow its banks, which is appreciated by people nearby.",
  "attack": 85,
  "defense": 60,
  "height": 10
}
{
  "_id": ObjectId("5648c5f9e509dc2b3e263854"),
  "name": "Feebas",
  "description": "It is the shabbiest Pokmon of all. It forms in schools and lives at the bottom of rivers.",
  "attack": 15,
  "defense": 20,
  "height": 6
}
{
  "_id": ObjectId("5648c603e509dc2b3e263855"),
  "name": "Lugia",
  "description": "O rei dos mares",
  "attack": 90,
  "defense": 130,
  "height": 52
}
Fetched 5 record(s) in 9ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
vostro(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte:0.5}}, {type: "grama"}]}
vostro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648f57c50cae306167f229b"),
  "name": "Bulbasaur",
  "description": "Dinosauro verde",
  "attack": 100,
  "defense": 100,
  "height": 0.5,
  "type": "grama"
}
Fetched 1 record(s) in 5ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
vostro(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{attack: {$lte:0.5}}, {name: "Pikachu"}]}
vostro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648f2eef178d68ddbb81801"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "attack": 100,
  "defense": 90,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
vostro(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte:48}}, {height: {$lte:0.5}}]}
vostro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648f2eef178d68ddbb81801"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "attack": 100,
  "defense": 90,
  "height": 0.4
}
{
  "_id": ObjectId("5648f57c50cae306167f229b"),
  "name": "Bulbasaur",
  "description": "Dinosauro verde",
  "attack": 100,
  "defense": 100,
  "height": 0.5,
  "type": "grama"
}
Fetched 2 record(s) in 7ms
```

