# MongoDB - Aula 03 - Exercício
autor: Dayvson Sales

## Listando todos os Pokemóns com a altura menor que 0.5

    ```
    	> var query = {height: {$lt: 0.5}}  
	> db.pokemons.find(query)  
	{ "_id" : ObjectId("564287cdbc66beda1d9c4146"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }  
	{ "_id" : ObjectId("564286febc66beda1d9c4145"), "name" : "Pikachu", "description" : "Rato elétrico", "type" : "eletric", "attack" : 55, "height" : 0.4, "defense" : 35 }  
	{ "_id" : ObjectId("5642a86ebc66beda1d9c414a"), "name" : "Bulbasaur", "description" : "joga aguinha, eu acho", "type" : "water", "attack" : 65, "height" : 0.4 }  
	{ "_id" : ObjectId("5642a86ebc66beda1d9c414b"), "name" : "Charmeleon", "description" : "não achei", "type" : "fire", "attack" : 80, "height" : 0.4 }  
	{ "_id" : ObjectId("5642a86ebc66beda1d9c414c"), "name" : "Charizard", "description" : "solta fogo", "type" : "fire", "attack" : 109, "height" : 0.4 }  
	{ "_id" : ObjectId("5642a86ebc66beda1d9c414d"), "name" : "Wartortle", "description" : "não achei", "type" : "terra", "attack" : 65, "height" : 0.4 }  

    ```

## Listando todos os Pokemóns com a altura maior ou igual que 0.5

    ```
	> var query = {height: {$gte: 0.5}}  
	> db.pokemons.find(query)  
	{ "_id" : ObjectId("564287fbbc66beda1d9c4148"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }  
	{ "_id" : ObjectId("5642a86ebc66beda1d9c4149"), "name" : "Voltorb", "description" : "It was discovered when POK BALLS were introduced. It is said that there is some connection.", "type" : "electric", "attack" : 30, "height" : 5 }  

    ```

## Listando todos os Pokemóns com a altura maior ou igual que 0.5 e do tipo grama

```
	> var query = {$and: [{height: {$gte: 0.5}}, {type: "grama"}]}  
	> db.pokemons.find(query)  
```

## Listando todos os Pokemóns com o name Pikachu ou com attack menor ou igual que 0.5
```
	> var query = {$or: [{name: "Pikachu"}, {$lte: ["attack", 0.5]}]}  
	> db.pokemons.find(query)  
{ "_id" : ObjectId("564286febc66beda1d9c4145"), "name" : "Pikachu", "description" : "Rato elétrico", "type" : "eletric", "attack" : 55, "height" : 0.4, "defense" : 35 }  

```
## Listando todos os Pokemóns com o attack maior ou igual que 48 e com height menor ou igual que 0.5
```
	> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}  
	> db.pokemons.find(query)  
	{ "_id" : ObjectId("564287cdbc66beda1d9c4146"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }  
	{ "_id" : ObjectId("564286febc66beda1d9c4145"), "name" : "Pikachu", "description" : "Rato elétrico", "type" : "eletric", "attack" : 55, "height" : 0.4, "defense" : 35 }  
	{ "_id" : ObjectId("5642a86ebc66beda1d9c414a"), "name" : "Bulbasaur", "description" : "joga aguinha, eu acho", "type" : "water", "attack" : 65, "height" : 0.4 }  
	{ "_id" : ObjectId("5642a86ebc66beda1d9c414b"), "name" : "Charmeleon", "description" : "não achei", "type" : "fire", "attack" : 80, "height" : 0.4 }  
	{ "_id" : ObjectId("5642a86ebc66beda1d9c414c"), "name" : "Charizard", "description" : "solta fogo", "type" : "fire", "attack" : 109, "height" : 0.4 }  
	{ "_id" : ObjectId("5642a86ebc66beda1d9c414d"), "name" : "Wartortle", "description" : "não achei", "type" : "terra", "attack" : 65, "height" : 0.4 }  
```
