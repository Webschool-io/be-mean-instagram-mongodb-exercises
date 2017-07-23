# MongoDB - Aula 03 - Exercício
autor: Maurício Guedes

## Listagem de todos os pokemons com a altura MENOR QUE 0.5 (passo 1)
```
var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5646231ba485bd420f9e58fc"), "name" : "Mauricio", "description" : " o bixo", "attack" : 84, "defense" : 78, "height" : 0.2 }
>	
```

## Listagem de todos os pokemons com a altura MAIOR OU IGUAL QUE 0.5 (passo 2)
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5643c6c703acdc55ec079516"), "name" : "Bulbasaur", "description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", "attack" : 49, "defense" : 49, "height" : 7 }
{ "_id" : ObjectId("5643c6d103acdc55ec079517"), "name" : "Metapod", "description" : "The shell covering this Pokmon's body is as hard as an iron slab. Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.", "attack" : 20, "defense" : 55, "height" : 7 }
{ "_id" : ObjectId("5643c6d803acdc55ec079518"), "name" : "Ivysaur", "description" : "There is a bud on this Pokmon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.", "attack" : 62, "defense" : 63, "height" : 10 }
{ "_id" : ObjectId("5643c6e503acdc55ec079519"), "name" : "Charmeleon", "description" : "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.", "attack" : 64, "defense" : 58, "height" : 11 }
{ "_id" : ObjectId("5643c6ec03acdc55ec07951a"), "name" : "Charizard", "description" : "Charizard é o bixão", "attack" : 84, "defense" : 78, "height" : 17 }
```

## Listagem de todos os pokemons com a altura MENOR OU IGUAL QUE 0.5 E do tipo grama (passo 3)
```
> var query = {$and: [{height: {$lte: 0.5}}, {type: "grama"}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("56462cf30f4ef44513a3ebf6"), "name" : "Mauricio tipo Grama", "description" : "o bixo da grama", "attack" : 84, "defense" : 78, "height" : 0.2, "type" : "grama" }
```

## Listando todos os Pokemons com o nome Pikachu OU com attack menor ou igual que 50 (passo 3)
```
> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 50}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5643c6c703acdc55ec079516"), "name" : "Bulbasaur", "description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", "attack" : 49, "defense" : 49, "height" : 7 }
{ "_id" : ObjectId("5643c6d103acdc55ec079517"), "name" : "Metapod", "description" : "The shell covering this Pokmon's body is as hard as an iron slab. Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.", "attack" : 20, "defense" : 55, "height" : 7 }
```

## Listar todos os pokemons com attack MAIOR OU IGUAL QUE 8 E com height MENOR OU IGUAL QUE 0.5 (passo 5)
```
> var query = {$and: [{attack: {$gte: 8}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5646231ba485bd420f9e58fc"), "name" : "Mauricio", "description" : " o bixo", "attack" : 84, "defense" : 78, "height" : 0.2 }
{ "_id" : ObjectId("56462cf30f4ef44513a3ebf6"), "name" : "Mauricio tipo Grama", "description" : "o bixo da grama", "attack" : 84, "defense" : 78, "height" : 0.2, "type" : "grama" }
```