# MongoDB - Aula 03 - Exercício
autor: Janaína P. dos Santos

## 1. Lista todos os Pokemos com altura menor que 0.5
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
```

## 2. Lista todos os Pokemos com altura maior ou igual que 0.5
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
```

## 3. Lista todos os Pokemos com altura menor ou igual que 0.5 e do tipo grama;
```
> var query = {$and:[{height:{$lte: 0.5}},{type:"grama"}]}
> db.pokemons.find(query)
```

## 4. Lista todos os Pokemos com nome 'Pikachu' ou com attack menor ou igual que 0.5
```
> var query = {$or:[{name:"Pikachu"},{attack:{$lte: 0.5}}]}
> db.pokemons.find(query)	
```

## 5. Lista todos os Pokemos com attack maior ou igual que 48 E
 com height menor ou igual que 0.5
``` 
var query = {$and:[{attack:{$gte:48},height:{$lte:0.5}}]}
> db.pokemons.find(query)
```

	

 
 


