# MongoDB - Aula 03 - Exercício autor: Matheus Jose Krumenauer Weber

Listando Pokemons com altura menor que 0.5

```
   > var query = {"height" : {$lt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5647834a771dc8af7806b262"), "name" : "Mew", "description" : "Pequeninho e bonitinho", "type" : "psychic", "attack" : 110, "height" : 0.3 }


```
Listando todos os Pokemons com a altura maior que 0.5

```
> var query = {"height" : {$gt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56478345771dc8af7806b25f"), "name" : "Charmeleon", "description" : "Salamandra de fogo evoluida", "type" : "fire", "attack" : 100, "height" : 5.2 }
{ "_id" : ObjectId("56478346771dc8af7806b260"), "name" : "Charizard", "description" : "Salamandra de fogo evoluida suprema", "type" : "fire", "attack" : 160, "height" : 17 }
{ "_id" : ObjectId("56478348771dc8af7806b261"), "name" : "Mewtwo", "description" : "O senhor supremo do mundo pokemon", "type" : "psychic", "attack" : 130, "height" : 5 }
> 

```
Listando todos os Pokemons com a altura maior ou igual a 0.5 e do tipo grama

``` 
> var query = {$and : [{"height" : {$gt: 0.5}}, {"type" :  "grama"}]}
> db.pokemons.find(query)

```    
Listando todos os pokemons com o nome Pikachu ou ataque menor ou igual a 0.5

```
> var query = {$or : [{"attack" : {$lte: 0.5}}, {"name" :  "Pikachu"}]}
> db.pokemons.find(query)
> 

```    
Lista os pokemons com o attack maior ou igual a 48 e o height menor ou igual a 0.5

```
> var query = {$and: [{"attack" : {$gte: 48}}, {"height" : {$lte : 0.5}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("56478343771dc8af7806b25e"), "name" : "Charmander", "description" : "Salamandra de fogo", "type" : "fire", "attack" : 60, "height" : 0.5 }
{ "_id" : ObjectId("5647834a771dc8af7806b262"), "name" : "Mew", "description" : "Pequeninho e bonitinho", "type" : "psychic", "attack" : 110, "height" : 0.3 }
> 
```

