# MongoDB - Aula 03 - Exercício
**autor:** Igor Vidotto Felipe

**1 -** Liste todos Pokemons com a altura **menor que** 0.5
```
be-mean-instagram> var query = {height: {$lt: 0.5}};
be-mean-instagram> db.pokemons.find(query);
```

#### Saída
>```
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5648cf46b2b455d5cd60fd7f"),
  "name": "Caterpie",
  "description": "Larva lutadora lixosa",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
{
  "_id": ObjectId("564dc38c3e726cf185f8809d"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 3 record(s) in 1ms
```

**2 -** Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
be-mean-instagram> var query = {height: {$gte: 0.5}};
be-mean-instagram> db.pokemons.find(query);
```

#### Saída
>```
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7d"),
  "name": "Charmander",
  "description": "Queima a rosca 4ever",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("564dc6463e726cf185f8809e"),
  "name": "Ninetales",
  "description": "Cachorro/Lobo que possui nove caldas (ah vá)",
  "type": "fogo",
  "attack": 76,
  "defense": 75,
  "height": 1.1
}
{
  "_id": ObjectId("564dc6463e726cf185f8809f"),
  "name": "Jigglypuff",
  "description": "Uma bolinha de pelos rosa que canta",
  "type": "normal/fada",
  "attack": 45,
  "defense": 20,
  "height": 0.5
}
{
  "_id": ObjectId("564dc6463e726cf185f880a0"),
  "name": "Charizard",
  "description": "Dragão fodelão motherfucker que AshNoob abandona",
  "type": "fogo/voador",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}
{
  "_id": ObjectId("564dc6463e726cf185f880a1"),
  "name": "ButterFree",
  "description": "Última evolução do Caterpie, nesse estágio se torna uma borboleta (Ash também abandona)",
  "type": "inseto/voador",
  "attack": 45,
  "defense": 50,
  "height": 1.1
}
{
  "_id": ObjectId("564dc6463e726cf185f880a2"),
  "name": "Pidgeot",
  "description": "Pássaro muito grande, um dos pokémons normais/voadores mais fortes",
  "type": "normal/voador",
  "attack": 80,
  "defense": 75,
  "height": 1.5
}
Fetched 7 record(s) in 2ms
```

**3 -** Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
be-mean-instagram> var x = {height: {$lte: 0.5}};
be-mean-instagram> var y = {type: "grama"};
be-mean-instagram> var query = {$and: [x,y]};
be-mean-instagram> db.pokemons.find(query);
```

#### Saída
>```
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

**4 -** Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 50
```
be-mean-instagram> var x = {name: "Pikachu"};
be-mean-instagram> var y = {attack: {$lte: 50}};
be-mean-instagram> var query = {$or: [x,y]};
be-mean-instagram> db.pokemons.find(query);
```

#### Saída
>```
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5648cf46b2b455d5cd60fd7f"),
  "name": "Caterpie",
  "description": "Larva lutadora lixosa",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
{
  "_id": ObjectId("564dc38c3e726cf185f8809d"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564dc6463e726cf185f8809f"),
  "name": "Jigglypuff",
  "description": "Uma bolinha de pelos rosa que canta",
  "type": "normal/fada",
  "attack": 45,
  "defense": 20,
  "height": 0.5
}
{
  "_id": ObjectId("564dc6463e726cf185f880a1"),
  "name": "ButterFree",
  "description": "Última evolução do Caterpie, nesse estágio se torna uma borboleta (Ash também abandona)",
  "type": "inseto/voador",
  "attack": 45,
  "defense": 50,
  "height": 1.1
}
Fetched 6 record(s) in 7ms
```

**5 -** Liste todos Pokemons com o attack **maior ou igual que** 48 **E** com height **menor ou igual que** 0.5;
```
be-mean-instagram> var x = {attack: {$gte: 48}};
be-mean-instagram> var y = {height: {$lte: 0.5}};
be-mean-instagram> var query = {$and: [x,y]};
be-mean-instagram> db.pokemons.find(query);
```

#### Saída
>```
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("564dc38c3e726cf185f8809d"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 3 record(s) in 3ms
```
