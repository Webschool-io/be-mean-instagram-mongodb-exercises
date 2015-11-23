# MongoDB - Aula 03 - Exercício
autor: Dariano Soares

##1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons, Bulbassauro e Charmander.

    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var query = { nome: {$in : ["Bulbassauro", "Charmander"]} }
    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var mod = { $inc: { attack: 2}}
    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var options = { multi: true}
    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> db.pokemons.update(query, mod, options)
    Updated 2 existing record(s) in 3ms
    WriteResult({
      "nMatched": 2,
      "nUpserted": 0,
      "nModified": 2
    })


##2. Adicionar 1 movimento em todos os pokemons: 'desvio'.

    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var query = {}
    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var mod = { $push: { moves: "desvio" }}
    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var options = { multi: true}
    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> db.pokemons.update(query, mod, options)
    Updated 10 existing record(s) in 12ms
    WriteResult({
      "nMatched": 10,
      "nUpserted": 0,
      "nModified": 10
    })

##3. Adicionar o pokemon 'AindaNaoExisteMon' caso ele nao exista com todos os dados com o valor 'null' e a descricao: 'Sem maiores informacoes'.

    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var query = { nome: /AindaNaoExisteMon/i}
    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var mod = {
        $setOnInsert :
            {
              "active": false,
              "nome": "AindaNaoExisteMon",
              "attack": null,
              "defense": null,
              "height": null,
              "description": "Sem maiores informações",
            }
    }
    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var options = { upsert: true}
    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> db.pokemons.update(query, mod, options)
    Updated 1 new record(s) in 4ms
    WriteResult({
      "nMatched": 0,
      "nUpserted": 1,
      "nModified": 0,
      "_id": ObjectId("564be3a88fdcb426e18aba11")
    })


##4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que voce adicionou, escolha seu pokemon favorito.

    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var query = { moves: { $all:  ["investida", "lança-chamas"]}}
    dariano-IC4I(mongod-3.0.7) be-mean-mongodb> db.pokemons.find(query)
    {
      "_id": ObjectId("56429748ce29771f1d16afbc"),
      "nome": "Charmander",
      "description": "Esse é o cão chupando manga do fofinho",
      "type": "fogo",
      "attack": 52,
      "height": 0.5,
      "active": false,
      "moves": [
        "investida",
        "lança-chamas",
        "desvio"
      ]
    }
    Fetched 1 record(s) in 3ms


##5. Pesquisar todos os pokemons que possuam os ataques que voce adicionou, escolha seu pokemon favorito.

	dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var query = { moves: { $all: ["investida", "folha navalha", "desvio"]}}
	dariano-IC4I(mongod-3.0.7) be-mean-mongodb> db.pokemons.find(query)
	{
		"_id": ObjectId("56429705ce29771f1d16afbb"),
		"nome": "Bulbassauro",
		"description": "Chicote de trepadeira",
		"type": "grama",
		"attack": 51,
		"height": 0.4,
		"active": false,
		"moves": [
		"investida",
		"folha navalha",
		"desvio"
		]
	}
	Fetched 1 record(s) in 5ms

##6. Pesquisar todos os pokemons que nao sao do tipo 'eletrico'.

	dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var query = { type: {$ne: "eletrico"}}
	dariano-IC4I(mongod-3.0.7) be-mean-mongodb> db.pokemons.find(query)
	Fetched 11 record(s) in 6ms


##7. Pesquisar todos os pokemons que tenha o ataque 'investida' E tenham a defesa nao menor ou igual a  49.

	dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var queryInvestida = { $all: ["investida"]}
	dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var queryDefesa = { $not: { $gte: 49}}
	dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var query = { moves: queryInvestida, attack: queryDefesa }
	dariano-IC4I(mongod-3.0.7) be-mean-mongodb> db.pokemons.find(query)

	Fetched 5 record(s) in 7ms

##8. Remova todos os pokemons do tipo agua e com attack menor que 50.

	dariano-IC4I(mongod-3.0.7) be-mean-mongodb> var query2 = { $and: [ { type: "água"},{ attack: { $lt: 50}} ] }
	dariano-IC4I(mongod-3.0.7) be-mean-mongodb> db.pokemons.find(query2)
	Fetched 0 record(s) in 0ms


