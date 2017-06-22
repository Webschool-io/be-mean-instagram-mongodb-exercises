# MongoDB - Aula 03 - Exercício
Autor: *Pablo Zaniolo*

## 1. Liste todos Pokemons com a altura menor que 0.5

```
var query = {height: {$lt: 0.5}}
db.pokemons.find(query)
```

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5

```
var query = {height: {$gte: 0.5}}
db.pokemons.find(query)
```

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama

```
var query = {$or: [{height: {$lte: 0.5}}], $and: [{type: "grama"}]}
db.pokemons.find(query)
```

## 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5

```
var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
db.pokemons.find(query)
```

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5

```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
db.pokemons.find(query)
```


