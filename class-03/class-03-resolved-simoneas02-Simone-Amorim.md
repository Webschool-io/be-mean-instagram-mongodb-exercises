# MongoDB - Aula 03 - Exercício
Autor: Simone Amorim

## Liste todos Pokemons com a altura **menor que** 0.5;

```
var query = {height:{$lt: 0.5}}
> query
{ "height" : { "$lt" : 0.5 } }
db.pokemons.find(query)
{ "_id" : ObjectId("56b0dbb8d50150923e9d15af"), "name" : "Mew", "description" : "Gatinho mais fofinho que já vi!", "type" : "psíquico", "attack" : 100, "height" : 0.41 }

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
var query = {height:{$gte: 0.5}}
db.pokemons.find(query)
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b0"), "name" : "Raikou", "description" : "A fera lendária do raio", "type" : "elétrico", "attack" : 85, "height" : 1.91 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b1"), "name" : "Entei", "description" : "Veloz pokemon do fogo", "type" : "fogo", "attack" : 115, "height" : 2.11 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b2"), "name" : "Suicine", "description" : "Cão lendário que controla as águas", "type" : "água", "attack" : 75, "height" : 2.01 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b3"), "name" : "Charizard", "description" : "Conhecido como dragão inimigo de são jorge", "type" : "fogo", "attack" : 84, "height" : 1.7 }
```
## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo psíquico

```
var query = {$and: [{height:{$lte: 0.5}}, {type: "psíquico"}]}
db.pokemons.find(query)
{ "_id" : ObjectId("56b0dbb8d50150923e9d15af"), "name" : "Mew", "description" : "Gatinho mais fofinho que já vi!", "type" : "psíquico", "attack" : 100, "height" : 0.41 }

```

## Liste todos Pokemons com o name `Raikou` **OU** com attack **menor ou igual que** 87

```
var query = {$or: [{attack:{$lte: 87}}, {name: "Raikou"}]}
db.pokemons.find(query)
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b0"), "name" : "Raikou", "description" : "A fera lendária do raio", "type" : "elétrico", "attack" : 85, "height" : 1.91 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b2"), "name" : "Suicine", "description" : "Cão lendário que controla as águas", "type" : "água", "attack" : 75, "height" : 2.01 }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b3"), "name" : "Charizard", "description" : "Conhecido como dragão inimigo de são jorge", "type" : "fogo", "attack" : 84, "height" : 1.7 }
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
var query = {$and: [{attack:{$gte: 48}}, {height: {$lte: 0.5}}]}
db.pokemons.find(query)
{ "_id" : ObjectId("56b0dbb8d50150923e9d15af"), "name" : "Mew", "description" : "Gatinho mais fofinho que já vi!", "type" : "psíquico", "attack" : 100, "height" : 0.41 }
```