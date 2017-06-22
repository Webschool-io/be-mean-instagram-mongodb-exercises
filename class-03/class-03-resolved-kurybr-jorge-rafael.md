# MongoDB - Aula 03 - Exercício
autor: Jorge Rafael

## Listar todos Pokemons com a altura menor que 0.5;

```
> var query  = { height : { $lt : 0.5 } }
> db.pokemons.find(query)
{ "_id" : ObjectId("564284a8920a9673a775bb0d"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("564284d1920a9673a775bb0e"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("564288cacc052955701cf5b0"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }
>
```

## Listar todos Pokemons com a altura maior ou igual que 0.5;

```
> var query  = { height : { $gte : 0.5 } }
> db.pokemons.find(query)
{ "_id" : ObjectId("56428532920a9673a775bb0f"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("56428573920a9673a775bb10"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
>

```

## Listar todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
> var query  = {$and: [ {height : { $lte : 0.5 }},{ type : /grama/i } ] }
> db.pokemons.find(query)
{ "_id" : ObjectId("564284d1920a9673a775bb0e"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
>

```

## Listar todos Pokemons com name 'Pikachu' OU com attack menor ou igual que 0.5

```
> var query  = { $or: [ { name : /pikachu/i },{ attack : { $lte : 0.5 } } ] }
> db.pokemons.find(query)
{ "_id" : ObjectId("564284a8920a9673a775bb0d"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4 }
>
```

## Listar todos Pokemons com attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 5)

```
> var query  = { $and: [ { attack : { $gte : 48 } } ], {height: { $lte: 0.5}} ] }
> db.pokemons.find(query)
{ "_id" : ObjectId("564284a8920a9673a775bb0d"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("564284d1920a9673a775bb0e"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("56428573920a9673a775bb10"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
>

```
