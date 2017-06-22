# MongoDB - Aula 03 - Exercício
autor: Diego Bittencourt Silva


## Liste todos Pokemons com a altura **menor que** 0.5;

```
var query= {height:{$lt:0.5}}
db.pokemons.find(query)


```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
var query= {height:{$gte:0.5}}
db.pokemons.find(query)
{ "_id" : ObjectId("564e01e2a6c083fcd8802ffb"), "name" : "ninetales", "description" : "Pokemon raposa de olhos vermelhos", "type" : "fogo", "attack" : 40, "defense" : 60, "height" : 4 }
{ "_id" : ObjectId("564e01e2a6c083fcd8802ffc"), "name" : "oddish", "description" : "Pokemon rabanete azul", "type" : "veneno", "attack" : 30, "defense" : 40, "height" : 3 }
{ "_id" : ObjectId("564e01e2a6c083fcd8802ffd"), "name" : "persian", "description" : "Evolução do gato da equipe rocket", "type" : "normal", "attack" : 40, "defense" : 50, "height" : 4.8 }
{ "_id" : ObjectId("564e01e2a6c083fcd8802ffe"), "name" : "arcanine", "description" : "Evolução do Growlithe, cachorro loko de fogo", "type" : "fogo", "attack" : 50, "defense" : 30, "height" : 5.3 }
{ "_id" : ObjectId("564e01e2a6c083fcd8802fff"), "name" : "kadabra", "description" : "Pokemon com doença mental", "type" : "psíquico", "attack" : 50, "defense" : 30, "height" : 5.7 }
{ "_id" : ObjectId("565268542f8a27fb770e86ff"), "name" : "Diegao", "description" : "meu pokemon", "type" : "programmer", "attack" : 10000, "defense" : 7000, "height" : 2.87 }
{ "_id" : ObjectId("565268542f8a27fb770e8700"), "name" : "gorilamon", "description" : "gorilinha", "type" : "macaco", "attack" : 2, "defense" : 4, "height" : 3.56 }
{ "_id" : ObjectId("565268542f8a27fb770e8701"), "name" : "ratata", "description" : "ratazana", "type" : "ratao", "attack" : 8777, "defense" : 9999, "height" : 2.58 }
{ "_id" : ObjectId("565268542f8a27fb770e8702"), "name" : "xunda", "description" : "Tocador de axe", "type" : "bandoleiro", "attack" : 6700, "defense" : 9987, "height" : 1.6 }
{ "_id" : ObjectId("565268542f8a27fb770e8703"), "name" : "chimbinha", "description" : "tocador de berimbau", "type" : "joelma", "attack" : 478, "defense" : 444, "height" : 1.8 }


```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
var query= {$and:[{height:{$lte:0.5}},{type:'grama'}]}
db.pokemons.find(query)


```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
var query= {$or:[{name:'Pikachu'},{atack:{$lte:0.5}}]}
db.pokemons.find(query)


```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
var query= {$and:[{atack:{$gte:48}},{height:{$lte:0.5}}]}
db.pokemons.find(query)


```
