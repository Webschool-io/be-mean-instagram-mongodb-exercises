# MongoDB - Aula 03 - Exercício
Autor: Alison Monteiro

## Liste todos Pokemons com a altura **menor que** 0.5
```
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> var query = { height: {'$lt': 0.5} }
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564510ae909feebcd301cad5"),
  "name": "Weedle",
  "description": "Olfato agudo",
  "type": "hairy-bug",
  "atack": 20,
  "height": 0.3
}
Fetched 1 record(s) in 28ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> var query = { height: {'$gte': 0.5} }
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
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
  "_id": ObjectId("564510b3909feebcd301cad6"),
  "name": "Ekans",
  "description": "Fica em espiral enquanto descança para ter mais agilidade quando precisar",
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
Fetched 4 record(s) in 4ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> var query = {'$and': [{ height: {'$lte': 0.5} }, {tipo: 'grama'}]}
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> var query = {'$or': [{ name: 'Pikachu'}, {attack: {'$lte': 0.5}}]}
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com height **menor ou igual que** 0.5
```
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> var query = {'$and': [{attack: {'$gte': 48}}, {height: {'$lte': 0.5}}]}
MacBook-Pro-de-Alison-monteiro(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```
