# MongoDB - Aula 03 - Exercício
autor: Bruno Micaela

## 1 - Liste todos Pokemons com a altura **menor que** 0.5;
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb01c"), "name" : "Pikachu", "description" : "Nova Descrição do Pikachu", "type"
: "eletric", "attack" : 55, "defense" : 40, "height" : 0.4 }
```

## 2 - Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb018"), "name" : "Blastoise", "description" : "Blastoise has water spouts that p
rotrude from its shell.", "type" : "Water", "attack" : "40", "defense" : "40", "height" : 1.6 }
{ "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb019"), "name" : "Charizard", "description" : "Charizard flies around the sky in
 search of powerful opponents", "type" : "Fire", "attack" : 40, "defense" : 30, "height" : 1.7 }
{ "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb01a"), "name" : "Venusaur", "description" : "There is a large flower on Venusau
rs back", "type" : "Grass", "attack" : "40", "defense" : 40, "height" : 2 }
{ "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb01b"), "name" : "Butterfree", "description" : "Butterfree has a superior abilit
y to search for delicious honey from flowers", "type" : "Bug", "attack" : "20", "defense" : 20, "height" : 1.1 }
```

## 3 - Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
> var query = {$and: [{height: {$lte: 0.5}}, {type: "Grass"}]}
> db.pokemons.find(query)
```

## 4 - Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb01c"), "name" : "Pikachu", "description" : "Nova Descrição do Pikachu", "type" : "eletric", "attack" : 55, "defense" : 40, "height" : 0.4 }
```
## 5 - Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb01c"), "name" : "Pikachu", "description" : "Nova Descrição do Pikachu", "type" : "eletric", "attack" : 55, "defense" : 40, "height" : 0.4 }
```