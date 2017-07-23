# MongoDB - Aula 03 - Exercício
autor: Luciano Silva de Lima

## 1. Pokemons com a altura menor que 0.5

> var filter = {height:{$lt:0.5}}
> db.pokemons.find(filter)
```
{ "_id" : ObjectId("565ccb66e8503ecc1aa4da32"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "defense" : 34 }
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "defense" : 30 }
{ "_id" : ObjectId("565ccda9e8503ecc1aa4da36"), "name" : "Caterpie", "description" : "Larva lutadora", "type"
: "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }
```

## 2. Todos os pokemons com a altura maior ou igual que 0.5

> db.pokemons.find(filter)
```
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando
MANGA de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "defense" : 32 }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "defense" : 33 }
```

## 3. Todos os pokemons com a altura menor ou igual que 0.5 E do tipo grama

> var filter = {$and:[{type:"grama"},{height:{$lte:0.5}}]}
> db.pokemons.find(filter)
```
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "defense" : 30 }
```

## 4. Todos os pokemons com o nome 'Pikachu' OU com attack menor ou igual que 0.5

> var filter = {$or:[{name:"Pickachu"},{attack:{$lte:0.5}}]}
> db.pokemons.find(filter)

## 5. Todos os pokemons com o attack maior ou igual que 48 E com height menor ou igual
##    que 0.5

> var filter = {$or:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
> db.pokemons.find(filter)
```
{ "_id" : ObjectId("565ccb66e8503ecc1aa4da32"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "defense" : 34 }
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "defense" : 30 }
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando
MANGA de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "defense" : 32 }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "defense" : 33 }
{ "_id" : ObjectId("565ccda9e8503ecc1aa4da36"), "name" : "Caterpie", "description" : "Larva lutadora", "type"
: "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }
```