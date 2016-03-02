MongoDB - Aula 03 - Exercício
autor: Henrique Liberato

## 1
var query = {height:{$lt: 0.5}}
db.pokemons.find(query)

## 2
var query = {height:{$gte: 0.5}}
db.pokemons.find(query)

## 3
var query = {$and: [{height:{$lte: 0.5}},{type:"Eletric"}]}
db.pokemons.find(query)

## 4
var query = {$or: [{attack:{$lte: 0.5}},{name:"Pikachu"}]}
db.pokemons.find(query)

## 5
var query = {$and: [{attack:{$gte: 48}},{height:{$lte: 0.5}}]}
db.pokemons.find(query)
