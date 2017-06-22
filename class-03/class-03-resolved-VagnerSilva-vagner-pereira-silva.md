# MongoDB - Aula 03 - Exercício
autor: Vagner Pereira Silva

## 1. Lista todos os Pokemos com altura menor que 0.5
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("567b7b6a19e6c47b0b11c1a7"), "name" : "Pikachu", "description" : "Pica-pikachu", "type" : "electric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("567b7c3319e6c47b0b11c1a8"), "name" : "Bulbassauro", "description" : "Buba-Bulbassauro", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("567b7db719e6c47b0b11c1ab"), "name" : "Caterpie", "description" : "pie-pie", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35}

```

## 2. Lista todos os Pokemos com altura maior ou igual que 0.5
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("567b7c6d19e6c47b0b11c1a9"), "name" : "Charmander", "description" : "Chaaaaarmander", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("567b7cc619e6c47b0b11c1aa"), "name" : "Squirtle", "description" : "Squirtle-Squirtle", "type" : "água", "attack" : 48, "height" : 0.5 }

```

## 3. Lista todos os Pokemos com altura menor ou igual que 0.5 e do tipo grama;
```
> var query = {$and: [{height: {$lte: 0.5}}, {type:'grama'}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("567b7c3319e6c47b0b11c1a8"), "name" : "Bulbassauro", "description" : "Buba-Bulbassauro", "type" : "grama", "attack" : 49, "height" : 0.4 }

```

## 4. Lista todos os Pokemos com nome 'Pikachu' ou com attack menor ou igual que 0.5
```
> var query = { $or: [{name: /pikachu/i},{attack: { $lte: 0.5} }]}
> db.pokemons.find(query)
{ "_id" : ObjectId("567b7b6a19e6c47b0b11c1a7"), "name" : "Pikachu", "description" : "Pica-pikachu", "type" : "electric", "attack" : 55, "height" : 0.4 }
	
```

## 5. Lista todos os Pokemos com attack maior ou igual que 48 E com height menor ou igual que 0.5
``` 
> var query = {$and: [
... {attack: { $gte: 48 } },
... {height: { $lte: 0.5} }
...  ] };
> db.pokemons.find(query)
{ "_id" : ObjectId("567b7b6a19e6c47b0b11c1a7"), "name" : "Pikachu", "description" : "Pica-pikachu", "type" : "electric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("567b7c3319e6c47b0b11c1a8"), "name" : "Bulbassauro", "description" : "Buba-Bulbassauro", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("567b7cc619e6c47b0b11c1aa"), "name" : "Squirtle", "description" : "Squirtle-Squirtle", "type" : "água", "attack" : 48, "height" : 0.5 }

```

	

 
 


