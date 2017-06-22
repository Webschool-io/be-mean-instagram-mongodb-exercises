# MongoDB - Aula 03 - Exercício
autor: sirrommer - Rômulo Brasil

## Liste todos Pokemons com a altura **menor que** 0.5:

```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query);
{ 
  "_id" : ObjectId("564a467a740cc428f1f83908"), 
  "name" : "Pikachu", 
  "description" : "Rato elétrico bem fofinho", 
  "type" : "electric", 
  "attack" : 100, 
  "height" : 0.4 
}
{ 
  "_id" : ObjectId("564a467f740cc428f1f83909"), 
  "name" : "Bulbassauro", 
  "description" : "Chicote de trepadeira", 
  "type" : "grama", 
  "attack" : 49, 
  "height" : 0.4 
}
{ 
  "_id" : ObjectId("564a4696740cc428f1f8390b"), 
  "name" : "Caterpie", 
  "description" : "Larva Lutadora", 
  "type" : "inseto", 
  "attack" : 30, 
  "height" : 0.3 
}
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5:

```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query);
{ 
  "_id" : ObjectId("564a4685740cc428f1f8390a"), 
  "name" : "Charmander", 
  "description" : "Esse é o cão chupando manga de fofinho", 
  "type" : "fogo", 
  "attack" : 52, 
  "height" : 0.6 
}
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama:

```
> var query1 = {height: {$lte: 0.5}}
> var query2 = {type: "grama"}
> db.pokemons.find({$and: [query1,query2]});
{ 
  "_id" : ObjectId("564a467f740cc428f1f83909"), 
  "name" : "Bulbassauro", 
  "description" : "Chicote de trepadeira", 
  "type" : "grama", 
  "attack" : 49, 
  "height" : 0.4 
}
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5:

```
> var query1 = {name: "Pikachu"}
> var query2 = {attack: {$lte: 0.5}}
> db.pokemons.find({$or: [query1,query2]});
{ 
  "_id" : ObjectId("564a467a740cc428f1f83908"), 
  "name" : "Pikachu", 
  "description" : "Rato elétrico bem fofinho", 
  "type" : "electric", 
  "attack" : 100, 
  "height" : 0.4 
}
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5:

```
> var query1 = {attack: {$gte: 48}}
> var query2 = {height: {$lte: 0.5}}
> db.pokemons.find({$and: [query1,query2]});
{ 
  "_id" : ObjectId("564a467a740cc428f1f83908"), 
  "name" : "Pikachu", 
  "description" : "Rato elétrico bem fofinho", 
  "type" : "electric", 
  "attack" : 100, 
  "height" : 0.4 
}
{ 
  "_id" : ObjectId("564a467f740cc428f1f83909"), 
  "name" : "Bulbassauro", 
  "description" : "Chicote de trepadeira", 
  "type" : "grama", 
  "attack" : 49, 
  "height" : 0.4 
}
```