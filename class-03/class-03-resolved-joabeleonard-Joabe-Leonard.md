# MongoDB - Aula 03 - Exercício
	autor: Joabe Leonard Feitosa

## Listagem de todos os Pokemons com a altura menor que 0.5 (passo 2)

```
> var query = {height:{$lt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5712815693f8f1fb006b1988"), 
  "name" : "Spearow",
  "description" : "Very protective of its territory, it flaps its short wings busily to dart around at high speed.", 
  "type" : "normal", 
  "attack" : 60, 
  "defense" : 30, 
  "height" : 0.3 
 }

{ "_id" : ObjectId("5712817093f8f1fb006b198a"), 
 "name" : "Metapod", 
 "description" : "A steel-hard shell protects its tender body. It quietly endures hardships while awaiting evolution.s", 
 "type" : "bug", 
 "attack" : 20,
 "defense" : "55", 
 "height" : 0.2 
}
>
```

## Listagem de todos os Pokemons com a altura maior ou igual que 0.5 (passo 3)

```
> var query = {height:{$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5712814a93f8f1fb006b1987"), 
  "name" : "Charizard", 
  "description" : "Breathing intense, hot flames, it can melt almost anything. Its breath inflicts terrible pain on enemies.", 
  "type" : "fire", 
  "attack" : 84, 
  "defense" : 78, 
  "height" : 0.6 
}

{ "_id" : ObjectId("5712816093f8f1fb006b1989"), 
  "name" : "Venusaur", 
  "description" : "Venusaur is a squat quadruped Pokémon with bumpy bluish green skin", 
  "type" : "grass", 
  "attack" : 82, 
  "defense" : 83,
  "height" : 0.8 
 }

{ "_id" : ObjectId("5712818093f8f1fb006b198b"), 
  "name" : "Butterfree", 
  "description" : "Water-repellent powder on its wings enables it to collect honey, even in the heaviest of rains.", 
  "type" : "bug", 
  "attack" : 45, 
  "defense" : 50, 
  "height" : 0.9 
}
```
## Listagem de todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama (passo 4)

```
> var query = {$and: [{type:'grass'}, {height:{$lte:0.5}}]}
> db.pokemons.find(query)
>
```
## Listagem de todos os Pokemons com o nome Pikachu ou com attack menor ou igual que 0.5 (passo 5)

```
> var query = {$or: [{name:'Pikachu'}, {attack:{$lte:0.5}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5712896e93f8f1fb006b198c"),
  "name" : "Pikachu",
   "description" : "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. It is the world's most famouse and cute pokemon.",
   "type" : "electric",
   "attack" : 55, 
   "defense" : 40, 
   "height" : 0.4 }
>
```
## Listagem de todos os Pokemons com o attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 6)

```
> var query = {$and: [{attack:{$gte:48}}, {height:{$lte:0.5}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5712815693f8f1fb006b1988"),
  "name" : "Spearow", 
  "description" : "Very protective of its territory, it flaps its short wings busily to dart around at high speed.", 
  "type" : "normal", 
  "attack" : 60, 
  "defense" : 30, 
  "height" : 0.3 
 }
>
```