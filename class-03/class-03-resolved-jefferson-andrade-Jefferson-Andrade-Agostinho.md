# MongoDB - Aula 03 - Exercício
Autor: Jefferson Andrade Agostinho

## 1. Lista de pokemons com o height `MENOR QUE` 0.5

```
dev(mongod-3.0.7) be-mean-instagram> var q = {height: {$lt: 0.5}}
dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(q)
{
  "_id": ObjectId("56449e834d97fd165a5e4f36"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56449f5d4d97fd165a5e4f37"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 19,
  "height": 0.4
}
{
  "_id": ObjectId("5644a0874d97fd165a5e4f3a"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 1ms
```

## 2. Lista de pokemons com o height `MAIOR OU IGUAL QUE` 0.5

```
dev(mongod-3.0.7) be-mean-instagram> var q = {height: {$gte: 0.5}}
dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(q)
{
  "_id": ObjectId("56449f924d97fd165a5e4f38"),
  "name": "Chamander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56449fc34d97fd165a5e4f39"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 5ms
```

## 3. Lista de pokemons com o height `MENOR OU IGUAL QUE` 0.5 `E` do tipo grama

```
dev(mongod-3.0.7) be-mean-instagram> var q = {$and: [{height : {$lte : 0.5 }}, {type : 'grama'}] }
dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(q)
{
  "_id": ObjectId("56449f5d4d97fd165a5e4f37"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 19,
  "height": 0.4
}
Fetched 1 record(s) in 2ms
```

## 4. Lista de pokemons com o name Pikachu `OU` com attack `MENOR OU IGUAL` QUE 0.5

```
dev(mongod-3.0.7) be-mean-instagram> var q = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(q)
{
  "_id": ObjectId("56449e834d97fd165a5e4f36"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## 5. Lista de pokemons com o attack `MAIOR OU IGUAL QUE` 48 `E` com height `MENOR OU IGUAL QUE` 0.5

```
dev(mongod-3.0.7) be-mean-instagram> var q = {$and: [{attack : {$gte : 48 }}, {height: {$lte: 0.5}}] }
dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(q)
{
  "_id": ObjectId("56449e834d97fd165a5e4f36"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56449fc34d97fd165a5e4f39"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 3ms
```
