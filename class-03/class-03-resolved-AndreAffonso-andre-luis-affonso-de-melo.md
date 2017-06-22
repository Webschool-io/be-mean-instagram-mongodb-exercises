# MongoDB - Aula 03 - Exercício

# 1º Listar todos os pokemons com altura menor que 0.5
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("588650a2a54af3de72f609c2"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 100, "height" : 0.4 }
{ "_id" : ObjectId("5886518da54af3de72f609c3"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("5886534ba54af3de72f609c6"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }

```

#2º Listar todos os pokemons com altura maior ou igual que 0.5
```
> var query = {height: {$lte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("588650a2a54af3de72f609c2"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 100, "height" : 0.4 }
{ "_id" : ObjectId("5886518da54af3de72f609c3"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("58865276a54af3de72f609c5"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
{ "_id" : ObjectId("5886534ba54af3de72f609c6"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }

```

# 3º Listar todos os pokemons com a altura menor ou igual que 0.5 e do tipo grama 
```
> var query = {$and:[ {height: {$lte: 0.5}}, {type: /grama/} ]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5886518da54af3de72f609c3"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }

```

## 4º Listar todos os pokemons com o name "Pikachu" ou com attack menor ou igual que 0.5
```
> var query = {$or: [{attack: {$lte: 0.5}}, {name: /pikachu/i}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("588650a2a54af3de72f609c2"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 100, "height" : 0.4 }

``` 

## 5º Listar todos os Pokemons com attack maior ou igual a 48 e com height menor ou igual a 0.5
```
> var query =  {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("588650a2a54af3de72f609c2"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 100, "height" : 0.4 }
{ "_id" : ObjectId("5886518da54af3de72f609c3"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("58865276a54af3de72f609c5"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }


```


