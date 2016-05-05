# MongoDB - Aula 03 - Exercício
autor: Wellerson Roberto

## Liste todos Pokemons com a altura **menor que** 0.5;
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
>
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5650a2b9414fed410978a3a7"), "name" : "Ivysaur", "description" : "Um pokemon com uma rosa em cima, bem viadão", "attack" : 62, "defense" : 63, "height" : 10 }
{ "_id" : ObjectId("5650a2b9414fed410978a3a8"), "name" : "Poliwag", "description" : "Um pokemon locão com uma parada no meio da barriga, dahora mesmo", "attack" : 50, "defense" : 40, "height" : 6 }
{ "_id" : ObjectId("5650a2b9414fed410978a3a9"), "name" : "Girafarig", "description" : "Um pokemon que é uma girafa com outra parada aí", "attack" : 80, "defense" : 65, "height" : 15 }
{ "_id" : ObjectId("5650a2b9414fed410978a3aa"), "name" : "Linoone", "description" : "Parece um roedor...", "attack" : 70, "defense" : 61, "height" : 5 }
{ "_id" : ObjectId("5650a2b9414fed410978a3ab"), "name" : "Bibarel", "description" : "Biba...rel", "attack" : 85, "defense" : 60, "height" : 10 }
>
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
> var query = {$and: [{height: {$lte: 0.5}},{type: "grama"}]}
> db.pokemons.find(query)
>
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
> var query = {$or: [{name: "Pikachu"},{height: {$lte: 0.5}}]}
> db.pokemons.find(query)
>
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
> var query = {$and: [{attack: {$gte: 48}},{height: {$lte: 0.5}}]}
> db.pokemons.find(query)
>
```