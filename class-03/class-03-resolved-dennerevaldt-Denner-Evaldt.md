
# MongoDB - Aula 03 - Exercício
autor: Denner Evaldt Machado

## Liste todos Pokemons com a altura **menor que** 0.5;

```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5642827c5978a2317b17a1e2"), "name" : "Rattata", "description" : "Ratinho louco", "type" : "Normal", "attack" : 30, "height" : 0.3 }

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56427c825978a2317b17a1df"), "name" : "Metapod", "description" : "Baguio loco de pedra e ferro", "type" : "Bug", "attack" : 10, "height" : 0.7 }
{ "_id" : ObjectId("56427d5e5978a2317b17a1e0"), "name" : "Butterfree", "description" : "Borboleta colorida bonitinha", "type" : "Butterfly", "attack" : 20, "height" : 1.1 }
{ "_id" : ObjectId("564281df5978a2317b17a1e1"), "name" : "Charizard", "description" : "Fogo na bomba", "type" : "Fire", "attack" : 40, "height" : 1.7 }
{ "_id" : ObjectId("564283105978a2317b17a1e3"), "name" : "Raichu", "description" : "Pokemon elétrico parecido com pikachu", "type" : "electric", "attack" : 50, "height" : 0.8 }

```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
> var query = {$and: [{height: {$gte: 0.5}} , {type: "grama"}]}
> db.pokemons.find(query)
> 

// Nenhum encontrado

```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
> db.pokemons.find(query)
> 

// Nenhum encontrado

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
> 

// Nenhum encontrado

```

