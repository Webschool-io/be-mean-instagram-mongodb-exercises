# MongoDB - Aula 03 - Exercício
autor: Bruno Motta Azevedo do Nascimento

##Lista completa de pokemons na base de dados
```
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.find();
{
  "_id": ObjectId("5805bc1bff84434c5f720a96"),
  "name": "Charizard",
  "description": "Dragão de fogo, cabuloso, fodastico, super poderoso de todos os tempos",
  "type": "Fire",
  "attack": 100,
  "defense": 100,
  "height": 10.17
}
{
  "_id": ObjectId("5805bc1eff84434c5f720a97"),
  "name": "Blastoise",
  "description": "Tartaruga Gigante",
  "type": "water",
  "attack": 90,
  "defense": 90,
  "height": 9.8
}
{
  "_id": ObjectId("5805bc21ff84434c5f720a98"),
  "name": "Zapdos",
  "description": "Passaro Eletrico fodastico",
  "type": "eletryc",
  "attack": 150,
  "defense": 150,
  "height": 10
}
{
  "_id": ObjectId("5805bc24ff84434c5f720a99"),
  "name": "Articuno",
  "description": "Passaro de Gelo",
  "type": "ice",
  "attack": 150,
  "defense": 100,
  "height": 11
}
{
  "_id": ObjectId("5805bc27ff84434c5f720a9a"),
  "name": "Moltres",
  "description": "Passaro de Fogo",
  "type": "fire",
  "attack": 100,
  "defense": 150,
  "height": 13.08
}
```

## Listando Pokemons com altura menor que 0.5 (Passo 1)
```
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> var query = {height:{$lt:0.5}}
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 0ms

```

## Listando Pokemons com altura maior ou igual que 0.5 (Passo 2)
```
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> var query = {height:{$gte:0.5}}
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5805bc1bff84434c5f720a96"),
  "name": "Charizard",
  "description": "Dragão de fogo, cabuloso, fodastico, super poderoso de todos os tempos",
  "type": "Fire",
  "attack": 100,
  "defense": 100,
  "height": 10.17
}
{
  "_id": ObjectId("5805bc1eff84434c5f720a97"),
  "name": "Blastoise",
  "description": "Tartaruga Gigante",
  "type": "water",
  "attack": 90,
  "defense": 90,
  "height": 9.8
}
{
  "_id": ObjectId("5805bc21ff84434c5f720a98"),
  "name": "Zapdos",
  "description": "Passaro Eletrico fodastico",
  "type": "eletryc",
  "attack": 150,
  "defense": 150,
  "height": 10
}
{
  "_id": ObjectId("5805bc24ff84434c5f720a99"),
  "name": "Articuno",
  "description": "Passaro de Gelo",
  "type": "ice",
  "attack": 150,
  "defense": 100,
  "height": 11
}
{
  "_id": ObjectId("5805bc27ff84434c5f720a9a"),
  "name": "Moltres",
  "description": "Passaro de Fogo",
  "type": "fire",
  "attack": 100,
  "defense": 150,
  "height": 13.08
}
Fetched 5 record(s) in 2ms

```

## Listando Pokemons com altura menor ou igual que 0.5 E do tipo grama (Passo 3)
```
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> var query = {$and:[{height:{$lte:0.5}},{type:"grass"}]}
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 1ms

```

## Listando Pokemons com o name 'Pìkachu' OU com attack menor ou igual que 0.5 (Passo 4)
```
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> var query = {$or:[{name:"Pikachu"},{attack:{$lte:0.5}}]}
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 0ms

```

## Listando Pokemons com attack maior ou igual que 48 E com altura menor ou igual que 0.5 (Passo 5)
```
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 0ms

```