# MongoDB - Aula 03 - Exercício
autor: Edison Ferraz


## Liste todos Pokemons com a altura menor que 0.5;
```
var query = {height: {$lt: 0.5}}
db.pokemons.find(query)

{ "_id" : ObjectId("58b334f42a7c86562c34f77f"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("58b335242a7c86562c34f780"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("58b335fb2a7c86562c34f783"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }
```


## Liste todos Pokemons com a altura maior ou igual que 0.5;
```
var query = {height: {$gte: 0.5}}
db.pokemons.find(query)

{ "_id" : ObjectId("58b335332a7c86562c34f781"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("58b335972a7c86562c34f782"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
```


## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;
```
var height = {height: {$lte: 0.5}}
var type = {type: 'grama'}
db.pokemons.find({$and: [height, type]})

{ "_id" : ObjectId("58b335242a7c86562c34f780"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
```


## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;
```
var name = {name: 'Pikachu'}
var attack = {attack: {$lte: 0.5}}
db.pokemons.find({$or: [name, attack]})

{ "_id" : ObjectId("58b334f42a7c86562c34f77f"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4 }
```


## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;
```
var attack = {attack: { $gte: 48 }}
var height = {height: { $lte: 0.5 }}
db.pokemons.find({$and: [attack, height]})

{ "_id" : ObjectId("58b334f42a7c86562c34f77f"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("58b335242a7c86562c34f780"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("58b335972a7c86562c34f782"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
```