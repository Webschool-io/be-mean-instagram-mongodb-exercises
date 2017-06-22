# MongoDB - Aula 03 - Exercício
autor: Valdir Pereira Júnior

Base de dados:
[
{
        "name" : "Pikachu",
        "description" : "Rato elétrico bem fofinho",
        "type" : "electric",
        attack : 55,
        defense : 20,
        height : 0.4
},
{
	"name" : "Bulbassauro",
	"description": "Chicote de trepadeira",
	"type": "grass",
	attack: 49,
	height: 0.4
},
{
	"name" : "Charmander",
	"description" : "Esse é o cao chupando manga de fofinho",
	"type" : "fire",
	attack: 52,
	height: 0.6
},
{
	"name": "Squirtle",
	"description": "Ejeta água que passarinho nao bebe",
	"type": "water",
	attack: 48,
	height: 0.5
},
{
        "name" : "chikorita",
        "description" : "Pedaço de folha",
        "type" : "grass",
        attack : 100,
        defense : 50,
        height : 0.9
},
{
        "name" : "Growlithe ",
        "description" : "lobo sentimental",
        "type" : "fire",
        attack : 40,
        defense : 20,
        height : 0.7
},
{
        "name" : "Magnemite",
        "description" : "Imã voador em formato de olho",
        "type" : "electric",
        attack : 20,
        defense : 30,
        height : 0.3
},
{
        "name" : "Onix",
        "description" : "Michoca marombeira pedrificada",
        "type" : "rock",
        attack : 20,
        defense : 70,
        height : 8.8
},
{
        "name" : "Horsea",
        "description" : "cavalo marinho bebe",
        "type" : "water",
        attack : 20,
        defense : 30,
        height : 0.4
},
{
        "name" : "Trevenant ",
        "description" : "Arvore do mal",
        "type" : "grass",
        attack : 60,
        defense : 30,
        height : 1.5
}
]

#Lista dos pokemons em minha collection:
	> db.pokemons.find().pretty()
	{
			"_id" : ObjectId("5645de099e4a265a89c86ecc"),
			"name" : "Pikachu",
			"description" : "Rato elétrico bem fofinho",
			"type" : "electric",
			"attack" : 55,
			"defense" : 20,
			"height" : 0.4
	}
	{
			"_id" : ObjectId("5645de099e4a265a89c86ecd"),
			"name" : "chikorita",
			"description" : "Pedaço de folha",
			"type" : "grass",
			"attack" : 100,
			"defense" : 50,
			"height" : 0.9
	}
	{
			"_id" : ObjectId("5645de099e4a265a89c86ece"),
			"name" : "Growlithe ",
			"description" : "lobo sentimental",
			"type" : "fire",
			"attack" : 40,
			"defense" : 20,
			"height" : 0.7
	}
	{
			"_id" : ObjectId("5645de099e4a265a89c86ecf"),
			"name" : "Magnemite",
			"description" : "Imã voador em formato de olho",
			"type" : "electric",
			"attack" : 20,
			"defense" : 30,
			"height" : 0.3
	}
	{
			"_id" : ObjectId("5645de099e4a265a89c86ed0"),
			"name" : "Onix",
			"description" : "Michoca marombeira pedrificada",
			"type" : "rock",
			"attack" : 20,
			"defense" : 70,
			"height" : 8.8
	}
	{
			"_id" : ObjectId("5645de099e4a265a89c86ed1"),
			"name" : "Horsea",
			"description" : "cavalo marinho bebe",
			"type" : "water",
			"attack" : 20,
			"defense" : 30,
			"height" : 0.4
	}
	{
			"_id" : ObjectId("5645de099e4a265a89c86ed2"),
			"name" : "Trevenant ",
			"description" : "Arvore do mal",
			"type" : "grass",
			"attack" : 60,
			"defense" : 30,
			"height" : 1.5
	}


# 1. Liste todos Pokemons com a altura menor que 0.5 ;

	> var query = {height: {$lt: 0.5} }
	>
	> db.pokemons.find(query).pretty()
	{
			"_id" : ObjectId("5645de099e4a265a89c86ecc"),
			"name" : "Pikachu",
			"description" : "Rato elétrico bem fofinho",
			"type" : "electric",
			"attack" : 55,
			"defense" : 20,
			"height" : 0.4
	}
	{
			"_id" : ObjectId("5645de099e4a265a89c86ecf"),
			"name" : "Magnemite",
			"description" : "Imã voador em formato de olho",
			"type" : "electric",
			"attack" : 20,
			"defense" : 30,
			"height" : 0.3
	}
	{
			"_id" : ObjectId("5645de099e4a265a89c86ed1"),
			"name" : "Horsea",
			"description" : "cavalo marinho bebe",
			"type" : "water",
			"attack" : 20,
			"defense" : 30,
			"height" : 0.4
	}
	>


# 2. Liste todos Pokemons com a altura maior ou igual que 0.5 ;
	
	> var query = {height: {$gte: 0.5} }
	>
	> db.pokemons.find(query).pretty()
	{
			"_id" : ObjectId("5645de099e4a265a89c86ecd"),
			"name" : "chikorita",
			"description" : "Pedaço de folha",
			"type" : "grass",
			"attack" : 100,
			"defense" : 50,
			"height" : 0.9
	}
	{
			"_id" : ObjectId("5645de099e4a265a89c86ece"),
			"name" : "Growlithe ",
			"description" : "lobo sentimental",
			"type" : "fire",
			"attack" : 40,
			"defense" : 20,
			"height" : 0.7
	}
	{
			"_id" : ObjectId("5645de099e4a265a89c86ed0"),
			"name" : "Onix",
			"description" : "Michoca marombeira pedrificada",
			"type" : "rock",
			"attack" : 20,
			"defense" : 70,
			"height" : 8.8
	}
	{
			"_id" : ObjectId("5645de099e4a265a89c86ed2"),
			"name" : "Trevenant ",
			"description" : "Arvore do mal",
			"type" : "grass",
			"attack" : 60,
			"defense" : 30,
			"height" : 1.5
	}
	>


#3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

	> var query = {$and: [{height: {$lte: 0.5} }, {type:'grass'}] }
	>
	> db.pokemons.find(query).pretty()
	>

	### Mudei para 0.9 aqui para retornar algum resultado :)

	> var query = {$and: [{height: {$lte: 0.9} }, {type:'grass'}] }
	>
	> db.pokemons.find(query).pretty()
	{
			"_id" : ObjectId("5645de099e4a265a89c86ecd"),
			"name" : "chikorita",
			"description" : "Pedaço de folha",
			"type" : "grass",
			"attack" : 100,
			"defense" : 50,
			"height" : 0.9
	}
	>

#4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

	> var query = {$or: [{attack: {$lte: 0.5} }, {name:'Pikachu'}] }
	>
	> db.pokemons.find(query).pretty()
	{
			"_id" : ObjectId("5645de099e4a265a89c86ecc"),
			"name" : "Pikachu",
			"description" : "Rato elétrico bem fofinho",
			"type" : "electric",
			"attack" : 55,
			"defense" : 20,
			"height" : 0.4
	}

#5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

	> var query1 = {attack: {$gte: 48}}
	>
	> var query2 = {height: {$lte: 0.5 }}
	>
	> db.pokemons.find({$and: [query1, query2]}).pretty()
	{
			"_id" : ObjectId("5645de099e4a265a89c86ecc"),
			"name" : "Pikachu",
			"description" : "Rato elétrico bem fofinho",
			"type" : "electric",
			"attack" : 55,
			"defense" : 20,
			"height" : 0.4
	}
	>

