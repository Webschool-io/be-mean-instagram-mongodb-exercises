# MongoDB - Aula 03 - Exercício
autor: Eduardo Chaves


## Liste todos Pokemons com a altura **menor que** 0.5;

```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564faaaf793b2b526913ebd0"), "name" : "Ninetales", "description" : "Its nine tails are said to be imbued with a mystic power. It can live for a thousand years.", "type" : "fogo", "attack" : 76, "defense" : 75, "height" : 0.3 }
{ "_id" : ObjectId("564faaaf793b2b526913ebd1"), "name" : "Grimer", "description" : "Appears in filthy areas. Thrives by sucking up polluted sludge that is pumped out of factories.", "type" : "veneno", "attack" : 80, "defense" : 50, "height" : 0.4 }
{ "_id" : ObjectId("564faaaf793b2b526913ebd2"), "name" : "Dewgong", "description" : "Stores thermal energy in its body. Swims at a steady 8 knots even in intensely cold waters.", "type" : "água", "attack" : 70, "defense" : 80, "height" : 0.2 }
{ "_id" : ObjectId("564faaaf793b2b526913ebd4"), "name" : "Nidorina", "description" : "When NIDORINA are with their friends or family, they keep their barbs tucked away to prevent hurting each other.", "type" : "veneno", "attack" : 62, "defense" : 67, "height" : 0.4 }
>
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564f9168793b2b526913ebc8"), "name" : "Ivysaur", "description" : "Mostro de feito de plantas", "type" : "grama", "attack" : 65, "defense" : 41, "height" : 1 }
{ "_id" : ObjectId("564f9168793b2b526913ebc9"), "name" : "Blastoise", "description" : "Monstro de água muito poderoso", "type" : "água", "attack" : 75, "defense" : "32", "height" : 1.6 }
{ "_id" : ObjectId("564f9168793b2b526913ebca"), "name" : "Venusaur", "description" : "Monstro de veneno muito poderoso", "type" : "grama", "attack" : 82, "defense" : "68", "height" : 2.2 }
{ "_id" : ObjectId("564f9168793b2b526913ebcb"), "name" : "Mega Venusaur", "description" : "Monstro de grama e veneno extremamente poderoso", "type" : "grama", "attack" : 100, "defense" : "90", "height" : 2.4 }
{ "_id" : ObjectId("564f9168793b2b526913ebcc"), "name" : "Charmeleon", "description" : "Monstro de Fogo muito poderoso", "type" : "fogo", "attack" : 32, "defense" : "31", "height" : 1.1 }
{ "_id" : ObjectId("564faaaf793b2b526913ebce"), "name" : "Butterfree", "description" : "Its wings, covered with poisonous powders, repel water.", "type" : "inseto", "attack" : 45, "defense" : 50, "height" : 0.8 }
{ "_id" : ObjectId("564faaaf793b2b526913ebcf"), "name" : "Arbok", "description" : "The frightening patterns on its belly have been studied. Six variations have been confirmed.", "type" : "veneno", "attack" : 85, "defense" : 69, "height" : 0.6 }
{ "_id" : ObjectId("564faaaf793b2b526913ebd3"), "name" : "Beedrill", "description" : "It can take down any opponent with its powerful poi son stingers.", "type" : "inseto", "attack" : 90, "defense" : 40, "height" : 10 }
>

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5 **E** do tipo grama
###(mudei para maior que por que não tenho do tipo grama com alturas menores ou igual a 0.5)

```
> var query = {$and: [{height: {$gte: 0.5}}, {type: "grama"}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("564f9168793b2b526913ebc8"), "name" : "Ivysaur", "description" : "Mostro de feito de plantas", "type" : "grama", "attack" : 65, "defense" : 41, "height" : 1 }
{ "_id" : ObjectId("564f9168793b2b526913ebca"), "name" : "Venusaur", "description" : "Monstro de veneno muito poderoso", "type" : "grama", "attack" : 82, "defense" : "68", "height" : 2.2 }
{ "_id" : ObjectId("564f9168793b2b526913ebcb"), "name" : "Mega Venusaur", "description" : "Monstro de grama e veneno extremamente poderoso", "type" : "grama", "attack" : 100, "defense" : "90", "height" : 2.4 }
>

```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
> var query = {$and: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
> db.pokemons.find(query)
>

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
> var query = {$and: [{height: {$lte: 0.5}}, {attack: {$gte: 48}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("564faaaf793b2b526913ebd0"), "name" : "Ninetales", "description" : "Its nine tails are said to be imbued with a mystic power. It can live for a thousand years.", "type" : "fogo", "attack" : 76, "defense" : 75, "height" : 0.3 }
{ "_id" : ObjectId("564faaaf793b2b526913ebd1"), "name" : "Grimer", "description" : "Appears in filthy areas. Thrives by sucking up polluted sludge that is pumped out of factories.", "type" : "veneno", "attack" : 80, "defense" : 50, "height" : 0.4 }
{ "_id" : ObjectId("564faaaf793b2b526913ebd2"), "name" : "Dewgong", "description" : "Stores thermal energy in its body. Swims at a steady 8 knots even in intensely cold waters.", "type" : "água", "attack" : 70, "defense" : 80, "height" : 0.2 }
{ "_id" : ObjectId("564faaaf793b2b526913ebd4"), "name" : "Nidorina", "description" : "When NIDORINA are with their friends or family, they keep their barbs tucked away to prevent hurting each other.", "type" : "veneno", "attack" : 62, "defense" : 67, "height" : 0.4 }
> 

```
