# MongoDB - Aula 02 - Exercício
autor: Anderson da Silva Souza

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

var query  = {name: {$in: [/pikachu/i, /squirtle/i, /charmander/i, /Bulbassauro/i]}}
var attaks = ["velocidade do trovão","Drible"]
var mod    = {$pushAll:{moves:attaks}}
var opts   = {multi:true}
db.pokemons.update(query,mod,opts)


db.pokemons.find(query)
{
  "_id": ObjectId("56439757ea6cf42d7e5395c6"),
  "name": "Charmander",
  "description": "Cao super forte",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 43,
  "active": false,
  "moves": [
    "velocidade do trovão",
    "Drible"
  ]
}
{
  "_id": ObjectId("56439766ea6cf42d7e5395c7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65,
  "active": false,
  "moves": [
    "velocidade do trovão",
    "Drible"
  ]
}
{
  "_id": ObjectId("564f266800f4df0c43d1f06f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "Eletric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "velocidade do trovão",
    "Drible"
  ]
}
{
  "_id": ObjectId("56439740ea6cf42d7e5395c5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 49,
  "active": false,
  "moves": [
    "velocidade do trovão",
    "Drible"
  ]
}


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

	be-mean-pokemons> var query = {}
	be-mean-pokemons> var attacks = ['desvio']
	be-mean-pokemons> opt = {multi:true}
	var mod = {$pushAll:{moves:attacks}}
	db.pokemons.update(query,mod,opt)

be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56439714ea6cf42d7e5395c3"),
  "name": "Zubat",
  "description": "Morcego troll",
  "type": "flying",
  "attack": 45,
  "height": 8,
  "defense": 35,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56439733ea6cf42d7e5395c4"),
  "name": "Nidoqueen",
  "description": "Cantor de banda famosa",
  "type": "poison",
  "attack": 92,
  "height": 13,
  "defense": 87,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56439757ea6cf42d7e5395c6"),
  "name": "Charmander",
  "description": "Cao super forte",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 43,
  "active": false,
  "moves": [
    "velocidade do trovão",
    "Drible",
    "desvio"
  ]
}
{
  "_id": ObjectId("56439766ea6cf42d7e5395c7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65,
  "active": false,
  "moves": [
    "velocidade do trovão",
    "Drible",
    "desvio"
  ]
}
{
  "_id": ObjectId("564f1db100f4df0c43d1f06e"),
  "description": "Pokemon de Teste",
  "name": "Testemon",
  "attack": 8001,
  "defense": 8000,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564f266800f4df0c43d1f06f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "Eletric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "velocidade do trovão",
    "Drible",
    "desvio"
  ]
}
{
  "_id": ObjectId("56439740ea6cf42d7e5395c5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 49,
  "active": false,
  "moves": [
    "desvio"
  ]
}



## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

	be-mean-pokemons> var query = {name:/AindaNaoExisteMon/i}

	query
		{
		  "name": /AindaNaoExisteMon/i
		}

		be-mean-pokemons> var mod = {$set:{active:true},$setOnInsert:{}}
	    be-mean-pokemons> var mod = {$set:{active:true},$setOnInsert:{name:"AindaNaoExisteMon",attack:null,defense:null,height:null,description:"Sem maiores informações"}}

	    be-mean-pokemons> mod
		{
		  "$set": {
		    "active": true
		  },
		  "$setOnInsert": {
		    "name": "AindaNaoExisteMon",
		    "attack": null,
		    "defense": null,
		    "height": null,
		    "description": "Sem maiores informações"
		  }
		}

		be-mean-pokemons> db.pokemos.update(query,mod,options)
			Updated 1 existing record(s) in 1ms
			WriteResult({
			  "nMatched": 1,
			  "nUpserted": 0,
			  "nModified": 0
			})

			be-mean-pokemons> db.pokemos.find(query)
			{
			  "_id": ObjectId("564e2d4a89eef972abd85c9c"),
			  "active": true,
			  "name": "AindaNaoExisteMon",
			  "attack": null,
			  "defense": null,
			  "height": null,
			  "description": "Sem maiores informações"
			}
			Fetched 1 record(s) in 0ms


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

be-mean-pokemons> var query = {moves:{$in:[/investida/,/choque do trovão/]}}


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

			be-mean-pokemons> db.pokemons.find(query)
			{
			  "_id": ObjectId("56439757ea6cf42d7e5395c6"),
			  "name": "Charmander",
			  "description": "Cao super forte",
			  "type": "fogo",
			  "attack": 52,
			  "height": 0.6,
			  "defense": 43,
			  "active": false,
			  "moves": [
			    "velocidade do trovão",
			    "Drible",
			    "desvio",
			    "investida"
			  ]
			}
			{
			  "_id": ObjectId("564f266800f4df0c43d1f06f"),
			  "name": "Pikachu",
			  "description": "Rato elétrico bem fofinho",
			  "type": "Eletric",
			  "attack": 100,
			  "height": 0.4,
			  "moves": [
			    "velocidade do trovão",
			    "Drible",
			    "desvio",
			    "investida"
			  ]
			}
			{
			  "_id": ObjectId("56439766ea6cf42d7e5395c7"),
			  "name": "Squirtle",
			  "description": "Ejeta água que passarinho não bebe",
			  "type": "água",
			  "attack": 48,
			  "height": 0.5,
			  "defense": 65,
			  "active": false,
			  "moves": [
			    "velocidade do trovão",
			    "Drible",
			    "desvio",
			    "investida"
			  ]
			}


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

 be-mean-pokemons> var query = {type:{$nin:[/elétrico/i]}}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56439714ea6cf42d7e5395c3"),
  "name": "Zubat",
  "description": "Morcego troll",
  "type": "flying",
  "attack": 45,
  "height": 8,
  "defense": 35,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56439733ea6cf42d7e5395c4"),
  "name": "Nidoqueen",
  "description": "Cantor de banda famosa",
  "type": "poison",
  "attack": 92,
  "height": 13,
  "defense": 87,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564f1db100f4df0c43d1f06e"),
  "description": "Pokemon de Teste",
  "name": "Testemon",
  "attack": 8001,
  "defense": 8000,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564f266800f4df0c43d1f06f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "Eletric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "velocidade do trovão",
    "Drible",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("56439740ea6cf42d7e5395c5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 49,
  "active": false,
  "moves": [
    "desvio",
    "ínvestida"
  ]
}
{
  "_id": ObjectId("564e20bc89eef972abd85c9a"),
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564e211f89eef972abd85c9b"),
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56439766ea6cf42d7e5395c7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65,
  "active": false,
  "moves": [
    "velocidade do trovão",
    "Drible",
    "desvio",
    "investida"
  ]
}


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

be-mean-pokemons> var query1 = {moves:{$in:[/investida/i]}}
be-mean-pokemons> var query2 = {defense:{$not:{$lte:49}}}
be-mean-pokemons> var query3 = {$and:[query1,query2]}
db.pokemons.find(query3)
{
  "_id": ObjectId("564f266800f4df0c43d1f06f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "Eletric",
  "attack": 100,
  "height": 0.4,
  "defense": 68,
  "moves": [
    "velocidade do trovão",
    "Drible",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("56439766ea6cf42d7e5395c7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65,
  "active": false,
  "moves": [
    "velocidade do trovão",
    "Drible",
    "desvio",
    "investida"
  ]
}

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
var query1	 = {type:/água/i}
var query2 = {attack:{$lt:50}}
var query3 = {$and:[query1,query2]}
db.pokemons.find(query3)
{
  "_id": ObjectId("56439766ea6cf42d7e5395c7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65,
  "active": false,
  "moves": [
    "velocidade do trovão",
    "Drible",
    "desvio",
    "investida"
  ]
}
Fetched 1 record(s) in 57ms

db.pokemons.remove(query1)
Removed 1 record(s) in 578ms
WriteResult({
  "nRemoved": 1
})
be-mean-pokemons> db.pokemons.find(query1)
Fetched 0 record(s) in 0ms