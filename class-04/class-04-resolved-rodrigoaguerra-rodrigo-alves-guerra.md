# MongoDB - Aula 04 - Exercício
autor: Rodrigo Alves Guerra

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
	
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var query = {$or : [{name: /pikachu/i}, {name: /squirtle/i}, {name:/bulbassauro/i},  {name: /charmander/i}]}
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var attacks = ['Socar', 'Chutar']
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var mod = {$pushAll: {moves: attacks}}
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var options = {multi: true}
	ogid-S430(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
	ogid-S430(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa84"),
	  "active": false,
	  "attack": 100,
	  "description": "Rato elétrico bem fofinho",
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "choque do travão",
	    "Socar",
	    "Chutar",
	    "Socar",
	    "Chutar"
	  ],
	  "name": "Pikachu",
	  "type": "eletric"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa87"),
	  "active": false,
	  "attack": 48,
	  "description": "Ejeta água que passarinho não bebe",
	  "height": 0.5,
	  "moves": [
	    "investida",
	    "hidro bomba",
	    "Socar",
	    "Chutar"
	  ],
	  "name": "Squirtle",
	  "type": "água"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa86"),
	  "active": false,
	  "attack": 52,
	  "description": "Esse é o cão chupando manga de fofinho",
	  "height": 0.6,
	  "moves": [
	    "investida",
	    "lança-chamas",
	    "Socar",
	    "Chutar"
	  ],
	  "name": "Charmander",
	  "type": "fogo"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa85"),
	  "active": false,
	  "attack": 49,
	  "description": "Chicote de trepadeira",
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "folha navalha",
	    "Socar",
	    "Chutar"
	  ],
	  "name": "Bulbassauro",
	  "type": "grama"
	}
	Fetched 4 record(s) in 4ms


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var query = {}
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var options = {multi: true}
	ogid-S430(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
	Updated 11 existing record(s) in 2ms
	ogid-S430(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("564a671c411c20b1c61afa83"),
	  "active": false,
	  "attack": 8000,
	  "defense": 8000,
	  "description": "Pokemon de teste",
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": "Testemon"
	}
	{
	  "_id": ObjectId("5642c9018068785ae3aecb57"),
	  "active": false,
	  "attack": 35,
	  "defense": "30",
	  "description": "Muito Misterioso",
	  "height": 0.6,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": "Kadabra",
	  "type": "psychic"
	}
	{
	  "_id": ObjectId("5642ca838068785ae3aecb5a"),
	  "active": false,
	  "attack": 20,
	  "defense": "15",
	  "description": "Muito loko chapadao",
	  "height": 0.5,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": "Abra",
	  "type": "psychic"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa84"),
	  "active": false,
	  "attack": 100,
	  "description": "Rato elétrico bem fofinho",
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "choque do travão",
	    "Socar",
	    "Chutar",
	    "Socar",
	    "Chutar",
	    "desvio"
	  ],
	  "name": "Pikachu",
	  "type": "eletric"
	}
	{
	  "_id": ObjectId("5642c9cb8068785ae3aecb58"),
	  "active": false,
	  "attack": 90,
	  "defense": "55",
	  "description": "Pokemon maloqueiro",
	  "height": 0.9,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": "Raichu",
	  "type": "electric"
	}
	{
	  "_id": ObjectId("5642ca298068785ae3aecb59"),
	  "active": false,
	  "attack": 83,
	  "defense": "100",
	  "description": "Um dos mais top da galaxia",
	  "height": 0.9,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": "Blastoise",
	  "type": "water"
	}
	{
	  "_id": ObjectId("564c6f05ca535e6cf6493dc6"),
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": /PokemonInexistente/i
	}
	{
	  "_id": ObjectId("5642cb668068785ae3aecb5b"),
	  "active": false,
	  "attack": 30,
	  "defense": "56",
	  "description": "Deixa a galera loka",
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": "Rattata",
	  "type": "normal"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa87"),
	  "active": false,
	  "attack": 48,
	  "description": "Ejeta água que passarinho não bebe",
	  "height": 0.5,
	  "moves": [
	    "investida",
	    "hidro bomba",
	    "Socar",
	    "Chutar",
	    "desvio"
	  ],
	  "name": "Squirtle",
	  "type": "água"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa86"),
	  "active": false,
	  "attack": 52,
	  "description": "Esse é o cão chupando manga de fofinho",
	  "height": 0.6,
	  "moves": [
	    "investida",
	    "lança-chamas",
	    "Socar",
	    "Chutar",
	    "desvio"
	  ],
	  "name": "Charmander",
	  "type": "fogo"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa85"),
	  "active": false,
	  "attack": 49,
	  "description": "Chicote de trepadeira",
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "folha navalha",
	    "Socar",
	    "Chutar",
	    "desvio"
	  ],
	  "name": "Bulbassauro",
	  "type": "grama"
	}


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

	ogid-S430(mongod-2.4.9) be-mean-pokemons> var query = {name: 'AindaNaoExisteMon', attack: null, defense: null, type: null, height: null, moves: null, description: "Sem maiores informações" }
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var mod = {$set: {active: true}}
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var options = {upsert: true}
	ogid-S430(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
	Updated 1 new record(s) in 1ms
	ogid-S430(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("564e1abb44b28ea04eeeede2"),
	  "active": true,
	  "attack": null,
	  "defense": null,
	  "description": "Sem maiores informações",
	  "height": null,
	  "moves": null,
	  "name": "AindaNaoExisteMon",
	  "type": null
	}
	Fetched 1 record(s) in 1ms

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
        
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var attacks = ['Socar', 'investida']
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var query = {moves: {$all: attacks}}
	ogid-S430(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
		{
		  "_id": ObjectId("564a6e1b411c20b1c61afa84"),
		  "active": false,
		  "attack": 100,
		  "description": "Rato elétrico bem fofinho",
		  "height": 0.4,
		  "moves": [
		    "investida",
		    "choque do travão",
		    "Socar",
		    "Chutar",
		    "Socar",
		    "Chutar",
		    "desvio"
		  ],
		  "name": "Pikachu",
		  "type": "eletric"
		}
		{
		  "_id": ObjectId("564a6e1b411c20b1c61afa87"),
		  "active": false,
		  "attack": 48,
		  "description": "Ejeta água que passarinho não bebe",
		  "height": 0.5,
		  "moves": [
		    "investida",
		    "hidro bomba",
		    "Socar",
		    "Chutar",
		    "desvio"
		  ],
		  "name": "Squirtle",
		  "type": "água"
		}
		{
		  "_id": ObjectId("564a6e1b411c20b1c61afa86"),
		  "active": false,
		  "attack": 52,
		  "description": "Esse é o cão chupando manga de fofinho",
		  "height": 0.6,
		  "moves": [
		    "investida",
		    "lança-chamas",
		    "Socar",
		    "Chutar",
		    "desvio"
		  ],
		  "name": "Charmander",
		  "type": "fogo"
		}
		{
		  "_id": ObjectId("564a6e1b411c20b1c61afa85"),
		  "active": false,
		  "attack": 49,
		  "description": "Chicote de trepadeira",
		  "height": 0.4,
		  "moves": [
		    "investida",
		    "folha navalha",
		    "Socar",
		    "Chutar",
		    "desvio"
		  ],
		  "name": "Bulbassauro",
		  "type": "grama"
		}
		{
		  "_id": ObjectId("564a671c411c20b1c61afa83"),
		  "active": false,
		  "attack": 8000,
		  "defense": 8000,
		  "description": "Pokemon de teste",
		  "moves": [
		    "investida",
		    "desvio",
		    "Socar",
		    "investida"
		  ],
		  "name": "Testemon"
		}
		Fetched 5 record(s) in 4ms


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var attacks = ['Socar', 'Chutar']
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var query = {moves: {$in: attacks}}
	ogid-S430(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa84"),
	  "active": false,
	  "attack": 100,
	  "description": "Rato elétrico bem fofinho",
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "choque do travão",
	    "Socar",
	    "Chutar",
	    "Socar",
	    "Chutar",
	    "desvio"
	  ],
	  "name": "Pikachu",
	  "type": "eletric"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa87"),
	  "active": false,
	  "attack": 48,
	  "description": "Ejeta água que passarinho não bebe",
	  "height": 0.5,
	  "moves": [
	    "investida",
	    "hidro bomba",
	    "Socar",
	    "Chutar",
	    "desvio"
	  ],
	  "name": "Squirtle",
	  "type": "água"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa86"),
	  "active": false,
	  "attack": 52,
	  "description": "Esse é o cão chupando manga de fofinho",
	  "height": 0.6,
	  "moves": [
	    "investida",
	    "lança-chamas",
	    "Socar",
	    "Chutar",
	    "desvio"
	  ],
	  "name": "Charmander",
	  "type": "fogo"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa85"),
	  "active": false,
	  "attack": 49,
	  "description": "Chicote de trepadeira",
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "folha navalha",
	    "Socar",
	    "Chutar",
	    "desvio"
	  ],
	  "name": "Bulbassauro",
	  "type": "grama"
	}
	{
	  "_id": ObjectId("564a671c411c20b1c61afa83"),
	  "active": false,
	  "attack": 8000,
	  "defense": 8000,
	  "description": "Pokemon de teste",
	  "moves": [
	    "investida",
	    "desvio",
	    "Socar",
	    "investida"
	  ],
	  "name": "Testemon"
	}


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
ogid-S430(mongod-2.4.9) be-mean-pokemons> var query = {type: {$ne: 'eletric'}}
ogid-S430(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642c9018068785ae3aecb57"),
  "active": false,
  "attack": 35,
  "defense": "30",
  "description": "Muito Misterioso",
  "height": 0.6,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Kadabra",
  "type": "psychic"
}
{
  "_id": ObjectId("5642ca838068785ae3aecb5a"),
  "active": false,
  "attack": 20,
  "defense": "15",
  "description": "Muito loko chapadao",
  "height": 0.5,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Abra",
  "type": "psychic"
}
{
  "_id": ObjectId("5642c9cb8068785ae3aecb58"),
  "active": false,
  "attack": 90,
  "defense": "55",
  "description": "Pokemon maloqueiro",
  "height": 0.9,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Raichu",
  "type": "electric"
}
{
  "_id": ObjectId("5642ca298068785ae3aecb59"),
  "active": false,
  "attack": 83,
  "defense": "100",
  "description": "Um dos mais top da galaxia",
  "height": 0.9,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Blastoise",
  "type": "water"
}
{
  "_id": ObjectId("564c6f05ca535e6cf6493dc6"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": /PokemonInexistente/i
}
{
  "_id": ObjectId("5642cb668068785ae3aecb5b"),
  "active": false,
  "attack": 30,
  "defense": "56",
  "description": "Deixa a galera loka",
  "height": 0.4,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Rattata",
  "type": "normal"
}
{
  "_id": ObjectId("564a6e1b411c20b1c61afa87"),
  "active": false,
  "attack": 48,
  "description": "Ejeta água que passarinho não bebe",
  "height": 0.5,
  "moves": [
    "investida",
    "hidro bomba",
    "Socar",
    "Chutar",
    "desvio"
  ],
  "name": "Squirtle",
  "type": "água"
}
{
  "_id": ObjectId("564a6e1b411c20b1c61afa86"),
  "active": false,
  "attack": 52,
  "description": "Esse é o cão chupando manga de fofinho",
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "Socar",
    "Chutar",
    "desvio"
  ],
  "name": "Charmander",
  "type": "fogo"
}
{
  "_id": ObjectId("564a6e1b411c20b1c61afa85"),
  "active": false,
  "attack": 49,
  "description": "Chicote de trepadeira",
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "Socar",
    "Chutar",
    "desvio"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("564e1abb44b28ea04eeeede2"),
  "active": true,
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "height": null,
  "moves": null,
  "name": "AindaNaoExisteMon",
  "type": null
}
{
  "_id": ObjectId("564a671c411c20b1c61afa83"),
  "active": false,
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio",
    "Socar",
    "investida"
  ],
  "name": "Testemon"
}
Fetched 11 record(s) in 10ms

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var query = {$and: [{moves: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}}]}
	ogid-S430(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("5642c9018068785ae3aecb57"),
	  "active": false,
	  "attack": 35,
	  "defense": "30",
	  "description": "Muito Misterioso",
	  "height": 0.6,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": "Kadabra",
	  "type": "psychic"
	}
	{
	  "_id": ObjectId("5642ca838068785ae3aecb5a"),
	  "active": false,
	  "attack": 20,
	  "defense": "15",
	  "description": "Muito loko chapadao",
	  "height": 0.5,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": "Abra",
	  "type": "psychic"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa84"),
	  "active": false,
	  "attack": 100,
	  "description": "Rato elétrico bem fofinho",
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "choque do travão",
	    "Socar",
	    "Chutar",
	    "Socar",
	    "Chutar",
	    "desvio"
	  ],
	  "name": "Pikachu",
	  "type": "eletric"
	}
	{
	  "_id": ObjectId("5642c9cb8068785ae3aecb58"),
	  "active": false,
	  "attack": 90,
	  "defense": "55",
	  "description": "Pokemon maloqueiro",
	  "height": 0.9,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": "Raichu",
	  "type": "electric"
	}
	{
	  "_id": ObjectId("5642ca298068785ae3aecb59"),
	  "active": false,
	  "attack": 83,
	  "defense": "100",
	  "description": "Um dos mais top da galaxia",
	  "height": 0.9,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": "Blastoise",
	  "type": "water"
	}
	{
	  "_id": ObjectId("564c6f05ca535e6cf6493dc6"),
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": /PokemonInexistente/i
	}
	{
	  "_id": ObjectId("5642cb668068785ae3aecb5b"),
	  "active": false,
	  "attack": 30,
	  "defense": "56",
	  "description": "Deixa a galera loka",
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "name": "Rattata",
	  "type": "normal"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa87"),
	  "active": false,
	  "attack": 48,
	  "description": "Ejeta água que passarinho não bebe",
	  "height": 0.5,
	  "moves": [
	    "investida",
	    "hidro bomba",
	    "Socar",
	    "Chutar",
	    "desvio"
	  ],
	  "name": "Squirtle",
	  "type": "água"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa86"),
	  "active": false,
	  "attack": 52,
	  "description": "Esse é o cão chupando manga de fofinho",
	  "height": 0.6,
	  "moves": [
	    "investida",
	    "lança-chamas",
	    "Socar",
	    "Chutar",
	    "desvio"
	  ],
	  "name": "Charmander",
	  "type": "fogo"
	}
	{
	  "_id": ObjectId("564a6e1b411c20b1c61afa85"),
	  "active": false,
	  "attack": 49,
	  "description": "Chicote de trepadeira",
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "folha navalha",
	    "Socar",
	    "Chutar",
	    "desvio"
	  ],
	  "name": "Bulbassauro",
	  "type": "grama"
	}
	{
	  "_id": ObjectId("564a671c411c20b1c61afa83"),
	  "active": false,
	  "attack": 8000,
	  "defense": 8000,
	  "description": "Pokemon de teste",
	  "moves": [
	    "investida",
	    "desvio",
	    "Socar",
	    "investida"
	  ],
	  "name": "Testemon"
	}
	Fetched 11 record(s) in 8ms

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
	ogid-S430(mongod-2.4.9) be-mean-pokemons> var query = {$and: [{type: /aguá/i}, {attack: {$lt: 50}}]}
	ogid-S430(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not. ##
	$ne -> significa o diferente em programação, precisa que os objetos tenham os campos, porém esse operador não aceita regex; 
	$not -> significa uma negação lógica, esse operador aceita regex.

