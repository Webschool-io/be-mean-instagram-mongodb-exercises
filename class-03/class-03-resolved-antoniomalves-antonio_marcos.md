# MongoDB - Aula 03 - Exercicio
autor: Antonio Marcos Alves

## Liste todos os pokemons com a altura menor que 0.5 - passo 01

'''
var query = {height: {$lt: 0.5}}
db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("5646679d3cfcf0bc03ef60c5"),
	"name" : "Pikachu",
	"description" : "Rato eletrico bem fofinho",
	"type" : "electric",
	"attack" : 100,
	"height" : 0.4
}
{
	"_id" : ObjectId("564669263cfcf0bc03ef60c6"),
	"name" : "Bulbassauro",
	"description" : "Chicote de trepadeira",
	"type" : "grama",
	"attack" : 49,
	"height" : 0.4
}
{
	"_id" : ObjectId("56468a713cfcf0bc03ef60c9"),
	"name" : "Caterpie",
	"description" : "Larva lutadora",
	"type" : "inseto",
	"attack" : 30,
	"height" : 0.3,
	"defense" : 35
}
'''

## Listar todos os pokemons com altura maior ou igual que 0.5 - passo 02

'''
var query = {height:{$gte: 0.5}}
db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("564669293cfcf0bc03ef60c7"),
	"name" : "Charmander",
	"description" : "Esse é o cão chupando manga de fofinho",
	"type" : "fogo",
	"attack" : 52,
	"height" : 0.6
}
{
	"_id" : ObjectId("5646692b3cfcf0bc03ef60c8"),
	"name" : "Squirtle",
	"description" : "Ejeta água que passarinho não bebe",
	"type" : "água",
	"attack" : 48,
	"height" : 0.5
}
'''

## Listar todos os pokemons com a altura menor ou igual que 0.5 e do tipo grama - passo 03

'''
var query = {$and:[{height:{$lte: 0.5}},{type:"grama"}]}
db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("564669263cfcf0bc03ef60c6"),
	"name" : "Bulbassauro",
	"description" : "Chicote de trepadeira",
	"type" : "grama",
	"attack" : 49,
	"height" : 0.4

}
'''

## Listar todos os pokemons com o name 'Pikachu' ou com o attack menor ou igual que 0.5 - passo 04

'''
var query = {$or:[{name: "Pikachu"},{attack:{$lte:0.5}}]}
db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("5646679d3cfcf0bc03ef60c5"),
	"name" : "Pikachu",
	"description" : "Rato eletrico bem fofinho",
	"type" : "electric",
	"attack" : 100,
	"height" : 0.4
}
'''

## Listar todos os pokemons com o attack maior ou igual que 48 e com height menor ou igual que 0.5 - passo 05

'''
var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("5646679d3cfcf0bc03ef60c5"),
	"name" : "Pikachu",
	"description" : "Rato eletrico bem fofinho",
	"type" : "electric",
	"attack" : 100,
	"height" : 0.4
}
{
	"_id" : ObjectId("564669263cfcf0bc03ef60c6"),
	"name" : "Bulbassauro",
	"description" : "Chicote de trepadeira",
	"type" : "grama",
	"attack" : 49,
	"height" : 0.4
}
{
	"_id" : ObjectId("5646692b3cfcf0bc03ef60c8"),
	"name" : "Squirtle",
	"description" : "Ejeta água que passarinho não bebe",
	"type" : "água",
	"attack" : 48,
	"height" : 0.5
}
'''
