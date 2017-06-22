# MongoDB - Aula 03 - Exercício
autor: Samuel Desconsi - Underzzoo

## 	1.	Liste todos Pokemons com a altura **menor que** 0.5;

```
var query = {'height': {$lt: 0.5}}
db.pokemons.find(query);
	{ "_id" : ObjectId("577530b35bb4daceabe68462"), "name" : "Pikachu", "description" : "Rato Elétrico", "type" : "Electric", "attack" : 55, "height" : 0.4 }
	{ "_id" : ObjectId("577533245bb4daceabe68466"), "name" : "Caterpie", "description" : "Corózinho", "type" : "Bug", "attack" : 20, "height" : 0.3 }
	{ "_id" : ObjectId("5775332d5bb4daceabe68467"), "name" : "Caterpie", "description" : "Corózinho", "type" : "Bug", "attack" : 20, "height" : 0.3 }
```

## 	2.	Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
var query = {'height': {$gte: 0.5}}
db.pokemons.find(query);
	{ "_id" : ObjectId("577532fa5bb4daceabe68463"), "name" : "Bulbasaur", "description" : "Couve-Flor", "type" : "Grass", "attack" : 30, "height" : 0.7 }
	{ "_id" : ObjectId("5775330e5bb4daceabe68464"), "name" : "Charmander", "description" : "Dragãozinho", "type" : "Fire", "attack" : 30, "height" : 0.6 }
	{ "_id" : ObjectId("5775331a5bb4daceabe68465"), "name" : "Squirtle", "description" : "Tartaruguinha Fofinha", "type" : "Water", "attack" : 30, "height" : 0.5 }
```


## 	3.	Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
var query = {$and: [{'height': {$lte: 0.5}}, {'type': 'Grass'}]}
db.pokemons.find(query);
```

## 	4.	Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
var query = {$or: [{'name': 'Pikachu'}, {'attack': {$lte: 0.5}}]};
db.pokemons.find(query);
	{ "_id" : ObjectId("577530b35bb4daceabe68462"), "name" : "Pikachu", "description" : "Rato Elétrico", "type" : "Electric", "attack" : 55, "height" : 0.4 }

```

## 	5.	Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
var query = {$and: [{'attack': {$gte: 48}}, {'height': {$lte: 0.5}}]}
db.pokemons.find(query);
	{ "_id" : ObjectId("577530b35bb4daceabe68462"), "name" : "Pikachu", "description" : "Rato Elétrico", "type" : "Electric", "attack" : 55, "height" : 0.4 }
```