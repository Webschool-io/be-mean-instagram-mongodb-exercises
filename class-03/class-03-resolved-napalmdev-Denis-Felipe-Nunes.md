# MongoDB - Aula 03 - Exercício
autor: Dênis Nunes

## Liste todos Pokemons com a altura **menor que** 0.5;

```javascript
	db.pokedex.find({height: {$lt: 0.5}})
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```javascript
	db.pokedex.find({height: {$gte: 0.5}})
```


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama


```javascript
	db.pokedex.find({$and: [{height: {$lte: 0.5}}, {type:"Grama"}]})
```


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```javascript
	db.pokedex.find({$or: [{name:"Pikachu"}, {attack: {$lte: 0.5}}]})
```


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```javascript
	db.pokedex.find({$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]})
```
