# MongoDB - Aula 03 - Exercício
autor: Wladek Zacharski

## Listagem de todos os pokemons com a altura MENOR QUE 0.5 (passo 1)

```
> var query = {heigth: { $lt: 0.5 } }
> db.pokemons.find(query)
> 
```

## Listagem de todos os pokemons com a altura MAIOR OU IGUAL QUE 0.5 (passo 2)

```
> var query = {heigth: { $gte: 0.5}}
> db.pokemons.find()
{ "_id" : ObjectId("56678e6a0d5830549257b42e"), "attack" : 84, "defense" : 78, "description" : "Pokemon mais foda para mim", "height" : 5.1, "name" : "Charizard", "type" : "Fire / Flying" }
{ "_id" : ObjectId("56678e950d5830549257b430"), "attack" : 110, "defense" : 90, "description" : "Pokemon sinistro do mau", "height" : 6, "name" : "Mewtwo", "type" : "Psychic" }
{ "_id" : ObjectId("56678e7f0d5830549257b42f"), "attack" : 55, "defense" : 25, "description" : "Pokemon minhoca", "height" : 0.6, "name" : "Diglett", "type" : "Ground" }
{ "_id" : ObjectId("56678ea70d5830549257b431"), "attack" : 130, "defense" : 90, "description" : "Pokemon Raro", "height" : 11.5, "name" : "Ho-oh", "type" : "Fire /  Flying" }
{ "_id" : ObjectId("56678e480d5830549257b42d"), "attack" : 49, "defense" : 49, "description" : "Pokemon inseto", "height" : 0.7, "name" : "Bulbasaur", "type" : "Grass" }
```

## Listagem de todos os pokemons com a altura MENOR OU IGUAL QUE 0.5 E do tipo grama (passo 3)

```	
> var query = { $and:[ { height:{ $lte:0.5} }, {type: "Grass"} ] }
> db.pokemons.find(query)
> 
```

## Listagem de todos os pokemons com o name 'Pikachu' OU com attack MENOR OU IGUAL QUE 0.5 (passo 4)

```
> var query = { $or:[ { name:"Pikachu" }, {attack:{$lte:0.5 }} ]}
> db.pokemons.find(query)
> 
```


## Listar todos os pokemons com attack MAIOR OU IGUAL QUE 8 E com height MENOR OU IGUAL QUE 0.5 (passo 5)
	
```
> var query = { $and:[ { attack:{ $gte:48} }, {height:{$lte:0.5 }} ]}
> db.pokemons.find(query)
> 
```
