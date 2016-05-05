# MongoDB - Aula 02 - Exercício
autor: Alison Monteiro

## Crie uma database chamada be-mean-pokemons;

```
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> use be-mean-pokemons
switched to db be-mean-pokemons
```


## 2. Liste quais databases você possui nesse servidor;

```
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> show dbs
be-mean → 0.078GB
local   → 0.078GB
test    → 0.078GB
```


## 3. Liste quais coleções você possui nessa database;

Obs.: Criando a coleção antes pra ficar mais show.

```
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> db.createCollection('pokemons')
{
  "ok": 1
}

MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> show collections
pokemons       → 0.000MB / 0.008MB
system.indexes → 0.000MB / 0.008MB
```


## 4. Insira pelo menos 5 pokemons A SUA ESCOLHA 

```
var pokemons = { name:'Nidorino', description:'Chifre tão duro quanto um diamante', type: 'poison-pin', atack:40, height:0.9 };

var pokemons = { name:'Clefable', description:'Se move saltando levemente', type: 'fairy', atack:40, height:1.3 };

var pokemons = { name:'Weedle', description:'Olfato agudo', type: 'hairy-bug', atack:20, height:0.3 };

var pokemons = { name:'Ekans', description:'Fica em espiral enquanto descança', type: 'snake', atack:30, height:2.0 };

var pokemons = { name:'Nidoking', description:'Poder na calda', type: 'drill', atack:50, height:1.4 };

MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> db.pokemons.insert(pokemons);
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
```


## 5. Liste os pokemons existentes na sua coleção;
```
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> db.pokemons.find();
{
  "_id": ObjectId("564510a0909feebcd301cad3"),
  "name": "Nidorino",
  "description": "Chifre tão duro quanto um diamante",
  "type": "poison-pin",
  "atack": 40,
  "height": 0.9
}
{
  "_id": ObjectId("564510a9909feebcd301cad4"),
  "name": "Clefable",
  "description": "Se move saltando levemente",
  "type": "fairy",
  "atack": 40,
  "height": 1.3
}
{
  "_id": ObjectId("564510ae909feebcd301cad5"),
  "name": "Weedle",
  "description": "Olfato agudo",
  "type": "hairy-bug",
  "atack": 20,
  "height": 0.3
}
{
  "_id": ObjectId("564510b3909feebcd301cad6"),
  "name": "Ekans",
  "description": "Fica em espiral enquanto descança",
  "type": "snake",
  "atack": 30,
  "height": 2
}
{
  "_id": ObjectId("564510ba909feebcd301cad7"),
  "name": "Nidoking",
  "description": "Poder na calda",
  "type": "drill",
  "atack": 50,
  "height": 1.4
}
Fetched 5 record(s) in 5ms
```


## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;
```
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> var query = { name: 'Ekans' }
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> var poke = db.pokemons.findOne(query)
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> poke
{
  "_id": ObjectId("564510b3909feebcd301cad6"),
  "name": "Ekans",
  "description": "Fica em espiral enquanto descança",
  "type": "snake",
  "atack": 30,
  "height": 2
}
```


## 7. Modifique sua `description` e salvê-o

```
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> poke.description = 'Fica em espiral enquanto descança para ter mais agilidade quando precisar'

MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> poke
{
  "_id": ObjectId("564510b3909feebcd301cad6"),
  "name": "Ekans",
  "description": "Fica em espiral enquanto descança para ter mais agilidade quando precisar",
  "type": "snake",
  "atack": 30,
  "height": 2
}

MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
