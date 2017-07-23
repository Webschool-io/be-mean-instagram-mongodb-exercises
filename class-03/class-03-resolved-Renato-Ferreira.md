# MongoDB - Aula 03 - Exercício
autor: Renato Ferreira

## Liste todos Pokemons com a altura **menor que** 0.5;

...

> var query = {height: {$lt:0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5648a89028d524f975ef45c8"), "name" : "Pikachu", "description" : "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.", "attack" : 30, "defense" : 20, "height" : 0.4 }
{ "_id" : ObjectId("5648a89028d524f975ef45ca"), "name" : "Nidoran", "description" : "Nidoran? has barbs that secrete a powerful poison.", "attack" : 30, "defense" : 20, "height" : 0.4 }
> 

...


## Liste todos Pokemons com a altura **maior ou igual que** 0.5

...

> var query = {height: {$gte:0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5648a89028d524f975ef45c9"), "name" : "Sandslash", "description" : "Sandslash's body is covered by tough spikes, which are hardened sections of its hide.", "attack" : 50, "defense" : 50, "height" : 1 }
{ "_id" : ObjectId("5648a89028d524f975ef45cb"), "name" : "Raichu", "description" : "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.", "attack" : 50, "defense" : 30, "height" : 0.8 }
{ "_id" : ObjectId("5648a89028d524f975ef45cc"), "name" : "Sandshrew", "description" : "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert.", "attack" : 40, "defense" : 40, "height" : 0.6 }
> 

...

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

...

> var query = {$and : [ { height : {$lte: 0.5} } , { type : "electric" } ] }
> db.pokemons.find(query)
{ "_id" : ObjectId("5648af7c28d524f975ef45d2"), "name" : "Pikachu", "description" : "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.", "attack" : 30, "type" : "electric", "height" : 0.4 }
> 

...

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

var query = {$or : [ { attack : {$lte: 0.5} } , { name : "Pikachu" } ] }
> db.pokemons.find(query)
{ "_id" : ObjectId("5648af7c28d524f975ef45d2"), "name" : "Pikachu", "description" : "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.", "attack" : 30, "type" : "electric", "height" : 0.4 }
> 


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

...

> var query = {$and : [ { height : {$lte: 0.5} } , { attack : {$gte: 48} } ] }
> db.pokemons.find(query)
> 

...