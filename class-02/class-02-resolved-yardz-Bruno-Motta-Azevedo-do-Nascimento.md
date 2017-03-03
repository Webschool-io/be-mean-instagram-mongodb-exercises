# MongoDB - Aula 02 - Exercício resolvido
autor: Bruno Motta Azevedo do Nascimento

## 1. Criar uma database chamada be-mean-pokemons

```
MacBook-Pro:class-01 Bruno$ mongo
MongoDB shell version: 3.2.10
connecting to: test
Mongo-Hacker 0.0.14
Server has startup warnings:
2016-10-18T01:19:35.547-0200 I CONTROL  [initandlisten]
2016-10-18T01:19:35.547-0200 I CONTROL  [initandlisten] ** WARNING: soft rlimits too low. Number of files is 256, should be at least 1000
MacBook-Pro(mongod-3.2.10) test> use be-mean-pokemons
switched to db be-mean-pokemons

```

## 2. Liste quais databases você possui nesse servidor

```
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> show dbs;
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
local             → 0.000GB

```

## 3. Liste quais coleções você possui nessa database

```
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> show collections;

```

## 4. Insira pelo menos 5 pokemons

```
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> var pokemon1 = {name:"Charizard",description:"Dragão de fogo",type:"Fire",attack:100,defense:100,height:10.17};
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> var pokemon2 = {name:"Blastoise",description:"Tartaruga Gigante",type:"water",attack:90,defense:90,height:9.80};
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> var pokemon3 = {name:"Zapdos",description:"Passaro Eletrico fodastico",type:"eletryc",attack:150,defense:150,height:10.00};
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> var pokemon4 = {name:"Articuno",description:"Passaro de Gelo",type:"ice",attack:150,defense:100,height:11.00};
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> var pokemon5 = {name:"Moltres",description:"Passaro de Fogo",type:"fire",attack:100,defense:150,height:13.08};
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> 
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.save(pokemon1);
Inserted 1 record(s) in 60ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.save(pokemon2);
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.save(pokemon3);
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.save(pokemon4);
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.save(pokemon5);
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

WriteResult({ "nInserted" : 1 })

```

## 5. Liste os pokemons existentes na sua coleção

```
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.find();
{
  "_id": ObjectId("5805bc1bff84434c5f720a96"),
  "name": "Charizard",
  "description": "Dragão de fogo",
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
Fetched 5 record(s) in 4ms

```

## 6. Busque um pokemon e armazene-o em uma variável chamada "poke"

```
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> var q = {name:"Charizard"}
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> var poke = db.pokemons.findOne(q);
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> poke
{
  "_id": ObjectId("5805bc1bff84434c5f720a96"),
  "name": "Charizard",
  "description": "Dragão de fogo",
  "type": "Fire",
  "attack": 100,
  "defense": 100,
  "height": 10.17
}

```

## 7. Modifique sua "description" e salve-o

```
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> poke.description = "Dragão de fogo, cabuloso, fodastico, super poderoso de todos os tempos";
Dragão de fogo, cabuloso, fodastico, super poderoso de todos os tempos
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.save(poke);
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
MacBook-Pro(mongod-3.2.10) be-mean-pokemons> db.pokemons.find(q);
{
  "_id": ObjectId("5805bc1bff84434c5f720a96"),
  "name": "Charizard",
  "description": "Dragão de fogo, cabuloso, fodastico, super poderoso de todos os tempos",
  "type": "Fire",
  "attack": 100,
  "defense": 100,
  "height": 10.17
}
Fetched 1 record(s) in 2ms

```