# MongoDB - Aula 03 - Exercício
autor: JOHAN PEDRO INÊS

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
	```
		> newMoves = ['soco','chute']
		> pokemons = [/pikachu/i,/squirtle/i,/bulbassauro/i,/charmander/i]
		> query = {name:{$in:pokemons}}
		> mod = {$pushAll:{moves:newMoves}}
		> opt = {multi:1}
		> db.pokemons.update(query,mod,opt)
		WriteResult({ "nMatched" : 2, "nUpserted" : 0, "nModified" : 2 })
	```
## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
	```
		> newMove = 'desvio'
		> query = {}
		> mod = {$push:{moves:newMove}}
		> opt = {multi:1}
		> db.pokemons.update(query,mod,opt)
		WriteResult({ "nMatched" : 7, "nUpserted" : 0, "nModified" : 7 })
	```


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
	```
		> query = {name:/AindaNaoExisteMon/i}
		> mod = {$setOnInsert:{name:'AindaNaoExisteMon',description:'Sem maiores informações',attack:null,defense:null,height:null,moves:null}}
		> opt = {upsert:1}
		> db.pokemons.update(query,mod,opt)
		WriteResult({
	        "nMatched" : 0,
	        "nUpserted" : 1,
	        "nModified" : 0,
	        "_id" : ObjectId("5654c0c88648ae8771c6bae3")
		})
	```


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
	```
		> query = {moves:{$all:[/investida/i,/soco/i]}}
		> db.pokemons.find(query)
		{ "_id" : ObjectId("5642ee00916e298aebb522b9"), "name" : "pikachu", "description" : "rato eletrico bem fofinho HUE HUE HUE", "type" : "eletric", "attack" : 55, "height" : 0.4, "moves" : [ "soco", "chute", "desvio", "investida" ] }
		{ "_id" : ObjectId("5643fe41916e298aebb522bb"), "name" : "charmander", "description" : "dragão de fogo", "type" : "fogo", "attack" : 600, "defense" : 500, "height" : 0.5, "moves" : [ "soco", "chute", "desvio", "investida" ] }
		>
	```


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
	```
		> query = {moves:{$all:[/chute/i,/soco/i]}}
		> db.pokemons.find(query)
		{ "_id" : ObjectId("5642ee00916e298aebb522b9"), "name" : "pikachu", "description" : "rato eletrico bem fofinho HUE HUE HUE", "type" : "eletric", "attack" : 55, "height" : 0.4, "moves" : [ "soco", "chute", "desvio", "investida" ] }
		{ "_id" : ObjectId("5643fe41916e298aebb522bb"), "name" : "charmander", "description" : "dragão de fogo", "type" : "fogo", "attack" : 600, "defense" : 500, "height" : 0.5, "moves" : [ "soco", "chute", "desvio", "investida" ] }
		>
	```


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
	```
		> query = {type:/eletric/i}
		> db.pokemons.find(query)
		{ "_id" : ObjectId("5642ee00916e298aebb522b9"), "name" : "pikachu", "description" : "rato eletrico bem fofinho HUE HUE HUE", "type" : "eletric", "attack" : 55, "height" : 0.4, "moves" : [ "soco", "chute", "desvio", "investida" ] }
	
	```


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
	```
		> query = {$and:[{moves:{$in:[/investida/i]}},{defense:{$lte:49}}]}
		> db.pokemons.find(query)
		{ "_id" : ObjectId("5642eee3916e298aebb522ba"), "name" : "Caterpie", "description" : "Larvalutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "desvio", "investida" ] }
		{ "_id" : ObjectId("5643fe41916e298aebb522be"), "name" : "charliemon brown", "description" : "aspirador de pó", "type" : "skate", "attack" : 3, "defense" : 0, "height" : 1.9, "moves" : [ "desvio", "investida" ] }
		{ "_id" : ObjectId("5643fe41916e298aebb522bf"), "name" : "mc brinquedomon", "description" : "Roça o pokemon nela que ela gosta", "type" : "carai", "attack" : 1, "defense" : 0, "height" : 1.6, "moves" : [ "desvio", "investida" ] }
	```


## Remova **todos** os pokemons do tipo água e com attack menor que 50.
	```
		> query = {$and:[{type:'water'},{attack:{$lt:50}}]}
		> db.pokemons.find(query)
		>
	```