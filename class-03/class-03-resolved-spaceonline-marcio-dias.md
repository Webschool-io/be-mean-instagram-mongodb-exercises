# MongoDB - Aula 03 - Exercício
autor: Márcio Dias


## Liste todos Pokemons com a altura **menor que** 0.5;
```
> var query = {height:{$lt:5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564a182589845c2ec6557f0f"), "name" : "Suissamon", "description" : "Pokemon Hacker", "type" : "hacker", "attack" : 8001, "defense" : 8000, "height" : 1.69 }
{ "_id" : ObjectId("564a182589845c2ec6557f10"), "name" : "Dilmamon", "description" : "Pokemon presidANTA", "type" : "besta", "attack" : 1, "defense" : 1, "height" : 1.6 }
{ "_id" : ObjectId("564a182589845c2ec6557f11"), "name" : "Cunhamon", "description" : "Filho da puta", "type" : "besta", "attack" : 9990, "defense" : 9999, "height" : 1.8 }
{ "_id" : ObjectId("564a182589845c2ec6557f12"), "name" : "Calheirosmon", "description" : "Irmão do filho da PUTA", "type" : "besta", "attack" : 8500, "defense" : 9999, "height" : 1.79 }
{ "_id" : ObjectId("564a182589845c2ec6557f13"), "name" : "FeliciANUS", "description" : "Pastor baitola", "type" : "besta", "attack" : 666, "defense" : 666, "height" : 1.7 }
{ "_id" : ObjectId("564a187622c6bbd0daedff4b"), "name" : "Suissamon", "description" : "Pokemon Hacker", "type" : "hacker", "attack" : 8001, "defense" : 8000, "height" : 1.69 }
{ "_id" : ObjectId("564a187622c6bbd0daedff4c"), "name" : "Dilmamon", "description" : "Pokemon presidANTA", "type" : "besta", "attack" : 1, "defense" : 1, "height" : 1.6 }
{ "_id" : ObjectId("564a187622c6bbd0daedff4d"), "name" : "Cunhamon", "description" : "Filho da puta", "type" : "besta", "attack" : 9990, "defense" : 9999, "height" : 1.8 }
{ "_id" : ObjectId("564a187622c6bbd0daedff4e"), "name" : "Calheirosmon", "description" : "Irmão do filho da PUTA", "type" : "besta", "attack" : 8500, "defense" : 9999, "height" : 1.79 }
{ "_id" : ObjectId("564a187622c6bbd0daedff4f"), "name" : "FeliciANUS", "description" : "Pastor baitola", "type" : "besta", "attack" : 666, "defense" : 666, "height" : 1.7 }
> 


## 2. Liste todos Pokemons com a altura maior ou igual que 0.5
> var query = {heigth: {$gte: 0.5}}
> db.pokemons.find(query, field)
