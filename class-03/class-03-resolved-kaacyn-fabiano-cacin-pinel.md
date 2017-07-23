# MongoDB - Aula 02 - Exercício
autor: Fabiano Cacin Pinel

## 1. Liste todos Pokemons com a altura menor que 0.5;
```
db.pokemons.find()

{ "_id" : ObjectId("5642aae859e08c5d4f034060"), "name" : "Bulbasaur", "description" : "Bichinho verdinho e feinho", "attack" : 12, "defense" : 55, "height" : 0.7 }

{ "_id" : ObjectId("5642ab73b195b651ecf3cf7e"), "name" : "Ivysaur", "description" : "Mesmo bichinho verdinho e feinho mas tem asas", "attack" : 25, "defense" : 56, "height" : 4 }

{ "_id" : ObjectId("5642ab7bb195b651ecf3cf7f"), "name" : "Venusaur", "description" : "Bichinho feinho com um abacaxi na cabeÃ§a", "attack" : 24, "defense" : 58, "height" : 2 }

{ "_id" : ObjectId("5642ab85b195b651ecf3cf80"), "name" : "Charmander", "description" : "Tartaruga pokemon", "attack" : 32, "defense" : 10, "height" : 0.6 }

{ "_id" : ObjectId("5642ab8db195b651ecf3cf81"), "name" : "Charmeleon", "description" : "Tartaruga pokemon do mal", "attack" : 50, "defense" : 60, "height" : 1.1 }

{ "_id" : ObjectId("5642ab94b195b651ecf3cf82"), "name" : "Charizard", "description" : "muito doido", "attack" : 34, "defense" : 16, "height" : 1.7 }

var query = { height: { $lt: 0.5 } } ;
db.pokemons.find(query)


```
## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;
```

db.pokemons.find(query)
var query = { height: { $gte: 0.5 } } ;
db.pokemons.find(query)
{ "_id" : ObjectId("5642aae859e08c5d4f034060"), "name" : "Bulbasaur", "description" : "Bichinho verdinho e feinho", "attack" : 12, "defense" : 55, "height" : 0.7 }
{ "_id" : ObjectId("5642ab73b195b651ecf3cf7e"), "name" : "Ivysaur", "description" : "Mesmo bichinho verdinho e feinho mas tem asas", "attack" : 25, "defense" : 56, "height" : 4 }
{ "_id" : ObjectId("5642ab7bb195b651ecf3cf7f"), "name" : "Venusaur", "description" : "Bichinho feinho com um abacaxi na cabeÃ§a", "attack" : 24, "defense" : 58, "height" : 2 }
{ "_id" : ObjectId("5642ab85b195b651ecf3cf80"), "name" : "Charmander", "description" : "Tartaruga pokemon", "attack" : 32, "defense" : 10, "height" : 0.6 }
{ "_id" : ObjectId("5642ab8db195b651ecf3cf81"), "name" : "Charmeleon", "description" : "Tartaruga pokemon do mal", "attack" : 50, "defense" : 60, "height" : 1.1 }
{ "_id" : ObjectId("5642ab94b195b651ecf3cf82"), "name" : "Charizard", "description" : "muito doido", "attack" : 34, "defense" : 16, "height" : 1.7 }

     
```

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
var query = { name: "Bulbasaur" } ;
var p = db.pokemons.findOne(query)
p.type = "grama";
p.height = 0.4;
db.pokemons.save(p);

var query = { $and: [ {height: $lte : {0.5}}, {type: 'grama']} } ;
db.pokemons.find(query)
    
{ "_id" : ObjectId("5642aae859e08c5d4f034060"), "name" : "Bulbasaur", "description" : "Bichinho verdinho e feinho", "attack" : 12, "defense" : 55, "height" : 0.4, "type" : "grama" }

```

## 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

```
var query = { $or: [ {name: 'Bulbasaur'}, {attack: { $lte: 0.5 }} ]} ;
db.pokemons.find(query)
{ "_id" : ObjectId("5642aae859e08c5d4f034060"), "name" : "Bulbasaur", "description" : "Bichinho verdinho e feinho", "attack" : 12, "defense" : 55, "height" : 0.4, "type" : "grama" }

```
## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

var query = { $and: [ {attack: { $gte : 48 }}, {height: { $lte: 0.5 }} ]} ;
db.pokemons.find(query);
{ "_id" : ObjectId("5642aae859e08c5d4f034060"), "name" : "Bulbasaur", "description" : "Bichinho verdinho e feinho", "attack" : 60, "defense" : 55, "height" : 0.4, "type" : "grama" }
```