
# MongoDB - Aula 02 - Exercicio
autor: Antonio Marcos Alves

## Criação do database - passo 01
'''
antonio@antonio:~$ mongo be-mean-pokemons
MongoDB shell version: 3.0.7
connecting to: be-mean-pokemons
'''

## Listagem dos databases - passo 02
'''
show databases
be-mean            0.078GB
be-mean-instagram  0.078GB
local              0.078GB
'''

## Listagem das colecoes - passo 03
'''
show collections
'''
## Cadastro de pokemons(incluir 5) - passo 04
'''
var pokemons = [{name:'Roger' , description:'Esquecido pela musica agora tenta chegar a midia falando merdas no palco' , type:'ex-cantor' , attack:1.6 , defense: 1, height: 1.78},{name: 'Sheherazade', description: 'Esperar pra ver quando ela vai adotar o bandido do Cunh', type:'jornalista', attack:2.15, defense: 1.6, height: 1.70}, {name:'Danilo', description:'Acha que fazer piadas com a desgraca alheia e engracado', type: 'bobao', attack: 1.65, defense: 1.1, height: 1.90},{name:'Olavao', description: 'Astrologo, acredita que a pepsi e adocada com fetos humanos, e acredita que o PT e comunista', type: 'maluco', attack:0.75, defense:0, height: 0.50}, {name: 'Lobao', description: 'Nao consegue mais fazer sucesso com shows e musica e se juntou aos malucos que pedem intervencao militar', type: 'maluco', attack: 0.1, defense: 0.2, height: 2.34}]

pokemons
[
	{
		"name" : "Roger",
		"description" : "Esquecido pela musica agora tenta chegar a midia falando merdas no palco",
		"type" : "ex-cantor",
		"attack" : 1.6,
		"defense" : 1,
		"height" : 1.78
	
	},
	{
		"name" : "Sheherazade",
		"description" : "Esperar pra ver quando ela vai adotar o bandido do Cunh",
		"type" : "jornalista",
		"attack" : 2.15,
		"defense" : 1.6,
		"height" : 1.7
	
	},
	{
		"name" : "Danilo",
		"description" : "Acha que fazer piadas com a desgraca alheia e engracado",
		"type" : "bobao",
		"attack" : 1.65,
		"defense" : 1.1,
		"height" : 1.9
	
	},
	{
		"name" : "Olavao",
		"description" : "Astrologo, acredita que a pepsi e adocada com fetos humanos, e acredita que o PT e comunista",
		"type" : "maluco",
		"attack" : 0.75,
		"defense" : 0,
		"height" : 0.5
	
	},
	{
		"name" : "Lobao",
		"description" : "Nao consegue mais fazer sucesso com shows e musica e se juntou aos malucos que pedem intervencao militar",
		"type" : "maluco",
		"attack" : 0.1,
		"defense" : 0.2,
		"height" : 2.34
	
	}
]

db.pokemons.insert(pokemons)
	BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 5,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]

})

'''

## Listar os pokemons - passo 05


db.pokemons.find().pretty()
{
	"_id" : ObjectId("56487e04e165a08b8c667172"),
	"name" : "Roger",
	"description" : "Esquecido pela musica agora tenta chegar a midia falando merdas no palco",
	"type" : "ex-cantor",
	"attack" : 1.6,
	"defense" : 1,
	"height" : 1.78

}
{
	"_id" : ObjectId("56487e04e165a08b8c667173"),
	"name" : "Sheherazade",
	"description" : "Esperar pra ver quando ela vai adotar o bandido do Cunh",
	"type" : "jornalista",
	"attack" : 2.15,
	"defense" : 1.6,
	"height" : 1.7

}
{
	"_id" : ObjectId("56487e04e165a08b8c667174"),
	"name" : "Danilo",
	"description" : "Acha que fazer piadas com a desgraca alheia e engracado",
	"type" : "bobao",
	"attack" : 1.65,
	"defense" : 1.1,
	"height" : 1.9

}
{
	"_id" : ObjectId("56487e04e165a08b8c667175"),
	"name" : "Olavao",
	"description" : "Astrologo, acredita que a pepsi e adocada com fetos humanos, e acredita que o PT e comunista",
	"type" : "maluco",
	"attack" : 0.75,
	"defense" : 0,
	"height" : 0.5

}
{
	"_id" : ObjectId("56487e04e165a08b8c667176"),
	"name" : "Lobao",
	"description" : "Nao consegue mais fazer sucesso com shows e musica e se juntou aos malucos que pedem intervencao militar",
	"type" : "maluco",
	"attack" : 0.1,
	"defense" : 0.2,
	"height" : 2.34

}

'''

## Buscar um 'pickachu' e armazenar em uma variavel poke - passo 06

'''
var query = {name: 'Olavao'}
var poke = db.pokemons.findOne(query)
poke
{
	"_id" : ObjectId("56487e04e165a08b8c667175"),
	"name" : "Olavao",
	"description" : "Astrologo, acredita que a pepsi e adocada com fetos humanos, e acredita que o PT e comunista",
	"type" : "maluco",
	"attack" : 0.75,
	"defense" : 0,
	"height" : 0.5
}

'''

## Modificar a 'description' e salvar - passo 07

'''
poke.description
Astrologo, acredita que a pepsi e adocada com fetos humanos, e acredita que o PT e comunista

poke.description = "Ele e as olavetes acreditam que ele é filosofo! rsrsrrs"
Ele e as olavetes acreditam que ele é filosofo! rsrsrrs
db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1  })
db.pokemons.findOne(query)
{
	"_id" : ObjectId("56487e04e165a08b8c667175"),
	"name" : "Olavao",
	"description" : "Ele e as olavetes acreditam que ele é filosofo! rsrsrrs",
	"type" : "maluco",
	"attack" : 0.75,
	"defense" : 0,
	"height" : 0.5

}

'''
