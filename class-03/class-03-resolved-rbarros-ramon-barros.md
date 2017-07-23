# MongoDB - Aula 03 - Exercício
autor: Ramon Barros

## Liste todos Pokemons com a altura **menor que** 0.5;
```
> var query = {height: {$lt: 0.5 }}
> db.pokemons.find(query)
{ 
    "_id" : ObjectId("564312e2af9b736e94f81e54"), 
    "name" : "Pidgey", 
    "description" : "Esse sabe onde fica o Alegrete",
    "attack" : 35, 
    "defense" : 35, 
    "height" : 0.3,
    "type": "bird"
}
{ 
    "_id" : ObjectId("564315c8af9b736e94f81e57"),
    "name" : "Ninetales",
    "description" : "Dizem que pode viver até mil anos.",
    "attack" : 81,
    "defense" : 100,
    "height" : 0.2,
    "type" : "fire"
}
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ 
    "_id" : ObjectId("56431288af9b736e94f81e53"), 
    "name" : "Blastoise", 
    "description" : "Ele pode dispara balas de águas com precisão.", 
    "attack" : 85, 
    "defense" : 105, 
    "height" : 0.5,
    "type" : "water"
}
{ 
    "_id" : ObjectId("564315a6af9b736e94f81e55"), 
    "name" : "Sandslash", 
    "description" : "Um rato com espinhos pontiagudos", 
    "attack" : 45, 
    "defense" : 55, 
    "height" : 0.7,
    "type" : "ground"
}
{ 
    "_id" : ObjectId("564315baaf9b736e94f81e56"), 
    "name" : "Jigglypuff", 
    "description" : "Faz o inimigo dormir como um anjo.", 
    "attack" : 45, 
    "defense" : 25, 
    "height" : 0.5,
    "type": "fairy"
}
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
> var query = { $and: [{height: {$lte: 0.5}}, {type: 'grama'}]}
> db.pokemons.find(query)
>
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
> var query = { $or: [{name: 'Pikachu'}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
{ 
    "_id" : ObjectId("56431288af9b736e94f81e53"), 
    "name" : "Blastoise", 
    "description" : "Ele pode dispara balas de águas com precisão.", 
    "attack" : 85, 
    "defense" : 105, 
    "height" : 0.5,
    "type" : "water"
}
{ 
    "_id" : ObjectId("564312e2af9b736e94f81e54"), 
    "name" : "Pidgey", 
    "description" : "Esse sabe onde fica o Alegrete", 
    "attack" : 45, 
    "defense" : 40, 
    "height" : 0.3, 
    "type" : "bird" 
}
{ 
    "_id" : ObjectId("564315baaf9b736e94f81e56"), 
    "name" : "Jigglypuff", 
    "description" : "Faz o inimigo dormir como um anjo.", 
    "attack" : 45, 
    "defense" : 25, 
    "height" : 0.5,
    "type": "fairy"
}
{ 
    "_id" : ObjectId("564315c8af9b736e94f81e57"), 
    "name" : "Ninetales", 
    "description" : "Dizem que pode viver até mil anos.", 
    "attack" : 81, 
    "defense" : 100, 
    "height" : 0.2, 
    "type" : "fire" 
}
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
> var query = { $and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
> db.pokemons.find(query)
{ 
    "_id" : ObjectId("56431288af9b736e94f81e53"), 
    "name" : "Blastoise", 
    "description" : "Ele pode dispara balas de águas com precisão.", 
    "attack" : 85, 
    "defense" : 105, 
    "height" : 0.5, 
    "type" : "water" 
}
{ 
    "_id" : ObjectId("564315c8af9b736e94f81e57"), 
    "name" : "Ninetales", 
    "description" : "Dizem que pode viver até mil anos.", 
    "attack" : 81, 
    "defense" : 100, 
    "height" : 0.2, 
    "type" : "fire" 
}
```
