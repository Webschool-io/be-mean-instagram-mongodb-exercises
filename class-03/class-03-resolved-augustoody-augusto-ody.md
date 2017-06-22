# MongoDB - Aula 03 - Exercício
autor: Augusto Ody

## Listagem de todos os pokemons com a altura MENOR QUE 0.5 (passo 1)
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564632c8d2b185d9685a165a"), "name" : "Texugao", "description" : "Porra loca", "type" : "grama", "attack" : 0.5, "height" : 0.2, "defense" : 95 }
```

## Listagem de todos os pokemons com a altura MAIOR OU IGUAL QUE 0.5 (passo 2)
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5643ba4eb4bf61eba67a67a9"), "name" : "Blastoise", "description" : "A brutal POKMON with pressurized water jets on its shell. They are used for high speed tackles", "type" : "água", "attack" : 83, "height" : 16, "defense" : 100 }
{ "_id" : ObjectId("5643ba51b4bf61eba67a67aa"), "name" : "Sandslash", "description" : "Sandslash's body is covered by tough spikes, which are hardened sections of its hide", "type" : "terra", "attack" : 100, "height" : 10, "defense" : 110 }
{ "_id" : ObjectId("5643ba55b4bf61eba67a67ab"), "name" : "Ninetales", "description" : "Ninetales casts a sinister light from its bright red eyes to gain total control over its foe's minde", "type" : "fogo", "attack" : 76, "height" : 11, "defense" : 75 }
{ "_id" : ObjectId("5643ba57b4bf61eba67a67ac"), "name" : "Machamp", "description" : "Machamp has the power to hurl anything aside", "type" : "lutador", "attack" : 130, "height" : 16, "defense" : 80 }
{ "_id" : ObjectId("5643ba5ab4bf61eba67a67ad"), "name" : "Tauros", "description" : "This Pokémon is not satisfied unless it is rampaging at all times", "type" : "normal", "attack" : 100, "height" : 14, "defense" : 95 }
```

## Listagem de todos os pokemons com a altura MENOR OU IGUAL QUE 0.5 E do tipo grama (passo 3)
```
> var query = {$and: [{height: {$lte: 0.5}}, {type: 'grama'}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("564632c8d2b185d9685a165a"), "name" : "Texugao", "description" : "Porra loca", "type" : "grama", "attack" : 0.5, "height" : 0.2, "defense" : 95 }
```

## Listando todos os Pokemons com o nome Pikachu OU com attack menor ou igual que 50 (passo 3)
```
> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 50}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("564632c8d2b185d9685a165a"), "name" : "Texugao", "description" : "Porra loca", "type" : "grama", "attack" : 0.5, "height" : 0.2, "defense" : 95 }
```

## Listar todos os pokemons com attack MAIOR OU IGUAL QUE 8 E com height MENOR OU IGUAL QUE 0.5 (passo 5)
```
> var query = {$and: [{attack: {$gte: 8}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
```
