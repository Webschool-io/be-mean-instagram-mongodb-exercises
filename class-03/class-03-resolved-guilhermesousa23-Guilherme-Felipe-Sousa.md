# MongoDB - Aula 03 - Exercício
autor: Guilherme Felipe de Sousa

## Listando pokemons com altura menor que 0.5

```
fedora(mongod-3.0.8) be-mean-pokemons> var query = {height: {$lt: 0.5}}
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ad072b4484bcd68498514f"),
  "name": "Spearow",
  "description": "Galisé minuscula que machuca",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "Voador"
}
Fetched 1 record(s) in 1ms
```

## Listando pokemons com altura maior ou igual a 0.5

```
fedora(mongod-3.0.8) be-mean-pokemons> var query = {height: {$gte: 0.5}}
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ad056653448d2fab7f1dfd"),
  "name": "Charmander",
  "description": "Tem uma chama na ponta da calda, a chama queima mais forte quando ele fica furioso",
  "attack": 30,
  "defense": 20,
  "height": 8.5,
  "type": "fogo"
}
{
  "_id": ObjectId("56ad06b64484bcd68498514e"),
  "name": "Raticate",
  "description": "Tem presas grandes e elas crescem de forma constatante, ele mastiga até paredes",
  "attack": 40,
  "defense": 30,
  "height": 18.5,
  "type": "Normal"
}
{
  "_id": ObjectId("56ad07954484bcd684985150"),
  "name": "Ekans",
  "description": "A famosa cascavel (sogra)",
  "attack": 30,
  "defense": 20,
  "height": 6.9,
  "type": "Terra"
}
{
  "_id": ObjectId("56ad07d54484bcd684985151"),
  "name": "Sandshrew",
  "description": "Tatu bolinha manso",
  "attack": 40,
  "defense": 40,
  "height": 12,
  "type": "Terra"
}
{
  "_id": ObjectId("56ad0a1740706acf8c2cc9c1"),
  "name": "Vileplume",
  "description": "Cogumelo azul do ventania",
  "attack": 40,
  "defense": 40,
  "height": 18.6,
  "type": "Grama"
}
Fetched 5 record(s) in 3ms
```

## Listando pokemons com altura menor ou igual a 0.5 e do tipo grama

```
fedora(mongod-3.0.8) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: "Grama"}]}
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Listando os pokemons com o nome 'Pikachu' ou com attack menor ou igual a 0.5

```
fedora(mongod-3.0.8) be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ad07d54484bcd684985151"),
  "name": "Sandshrew",
  "description": "Tatu bolinha manso",
  "attack": 0.5,
  "defense": 40,
  "height": 12,
  "type": "Terra"
}
Fetched 1 record(s) in 1ms
```

## Listando os pokemons com o Attack maior ou igual que 48 e com heigth menor que 0.5

```
fedora(mongod-3.0.8) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```