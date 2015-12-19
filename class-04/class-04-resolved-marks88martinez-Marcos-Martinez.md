# MongoDB - Aula 04 - Exercício
autor: Marcos Antonio Martinez Florentin

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
> var query = {$or:[{name: /pikachu/i},{name: /squirtle/i}, {name: /bulbassauro/i},{name: /charmander/i}]}
> var attacke = ['resplando electrico', 'fogo que queima', 'chute nas bolas']
> var mod = {$pushAll:{moves: attacke}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
> 

```


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
> var query = {}
> var attacke = ['desvio']
> var mod = {$pushAll:{moves:attacke}}
> var options = {multi:true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 7, "nUpserted" : 0, "nModified" : 7 })
> 


```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
> var query = {name:/AindaNaoExisteMon/i}
> var mod ={$setOnInsert:{ name:'NaoExisteMon', type:null, attack:null, height:null, moves:[], description: "Sem maiores informacoes"}}
> var options = {upsert: true}
> db.pokemons.update(query, mod, options)
WriteResult({
	"nMatched" : 0,
	"nUpserted" : 1,
	"nModified" : 0,
	"_id" : ObjectId("564e53cf5b4dd80d5358e489")
})
> 

```


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##


```
> var query = {moves: {$all:[/investida/i, /choque do trovao/i]}}
> db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("5642961ec9222a3fc35f8e08"),
	"name" : "Pikachu",
	"description" : "Rato elétrico bem fofinho",
	"type" : "electric",
	"attack" : 55,
	"height" : 0.4,
	"defense" : 35,
	"moves" : [
		"Investida",
		"choque do trovao",
		"resplando electrico",
		"fogo que queima",
		"chute nas bolas",
		"desvio"
	],
	"active" : false
}
> 

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
> var query = {moves: {$all:[/resplando electrico/i, /fogo que queima/i, /chute nas bolas/i]}}
> db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("5642961ec9222a3fc35f8e08"),
	"name" : "Pikachu",
	"description" : "Rato elétrico bem fofinho",
	"type" : "electric",
	"attack" : 55,
	"height" : 0.4,
	"defense" : 35,
	"moves" : [
		"Investida",
		"choque do trovao",
		"resplando electrico",
		"fogo que queima",
		"chute nas bolas",
		"desvio"
	],
	"active" : false
}
{
	"_id" : ObjectId("5642998cc9222a3fc35f8e09"),
	"name" : "charmander",
	"description" : "tira fogo pela bunda",
	"type" : "fogo",
	"attack" : 54,
	"height" : 0.3,
	"active" : false,
	"moves" : [
		"Investida",
		"lanca-chamas",
		"resplando electrico",
		"fogo que queima",
		"chute nas bolas",
		"desvio"
	]
}
{
	"_id" : ObjectId("56429a47c9222a3fc35f8e0a"),
	"name" : "Bulbassauro",
	"description" : "Chicote de trepadeira",
	"type" : "grama",
	"attack" : 49,
	"height" : 0.4,
	"active" : false,
	"moves" : [
		"Investida",
		"folha navalha",
		"resplando electrico",
		"fogo que queima",
		"chute nas bolas",
		"desvio"
	]
}
{
	"_id" : ObjectId("56429abec9222a3fc35f8e0b"),
	"name" : "Squirtle",
	"description" : "Ejeta água que passarinho não bebe",
	"type" : "água",
	"attack" : 48,
	"height" : 0.5,
	"active" : false,
	"moves" : [
		"Investida",
		"hidro bomba",
		"resplando electrico",
		"fogo que queima",
		"chute nas bolas",
		"desvio"
	]
}
> 


```


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```

> var query = {type: {$ne: 'electric'}}
> db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("56429c22c9222a3fc35f8e0c"),
	"name" : "Bulbasaur",
	"description" : "ataque con las platas",
	"type" : "plantas",
	"attack" : 54,
	"height" : 0.9,
	"active" : false,
	"moves" : [
		"Investida",
		"desvio"
	]
}
{
	"_id" : ObjectId("564c70d8518b583fbdba3ad9"),
	"description" : "Pokemon de teste",
	"name" : "testemon",
	"attack" : 8000,
	"defense" : 8000,
	"active" : false,
	"moves" : [
		"Investida",
		"desvio"
	]
}
{
	"_id" : ObjectId("564e100f29ebfceefbd4a790"),
	"active" : false,
	"moves" : [
		"Investida",
		"desvio"
	]
}
{
	"_id" : ObjectId("5642998cc9222a3fc35f8e09"),
	"name" : "charmander",
	"description" : "tira fogo pela bunda",
	"type" : "fogo",
	"attack" : 54,
	"height" : 0.3,
	"active" : false,
	"moves" : [
		"Investida",
		"lanca-chamas",
		"resplando electrico",
		"fogo que queima",
		"chute nas bolas",
		"desvio"
	]
}
{
	"_id" : ObjectId("56429a47c9222a3fc35f8e0a"),
	"name" : "Bulbassauro",
	"description" : "Chicote de trepadeira",
	"type" : "grama",
	"attack" : 49,
	"height" : 0.4,
	"active" : false,
	"moves" : [
		"Investida",
		"folha navalha",
		"resplando electrico",
		"fogo que queima",
		"chute nas bolas",
		"desvio"
	]
}
{
	"_id" : ObjectId("56429abec9222a3fc35f8e0b"),
	"name" : "Squirtle",
	"description" : "Ejeta água que passarinho não bebe",
	"type" : "água",
	"attack" : 48,
	"height" : 0.5,
	"active" : false,
	"moves" : [
		"Investida",
		"hidro bomba",
		"resplando electrico",
		"fogo que queima",
		"chute nas bolas",
		"desvio"
	]
}
{
	"_id" : ObjectId("564e53cf5b4dd80d5358e489"),
	"name" : "NaoExisteMon",
	"type" : null,
	"attack" : null,
	"height" : null,
	"moves" : [ ],
	"description" : "Sem maiores informacoes"
}
> 


```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
> var query =  {$and: [{moves: {$in: [/investida/i]}}, {attack: {$not: {$lte: 49}} }]}
> db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("56429c22c9222a3fc35f8e0c"),
	"name" : "Bulbasaur",
	"description" : "ataque con las platas",
	"type" : "plantas",
	"attack" : 54,
	"height" : 0.9,
	"active" : false,
	"moves" : [
		"Investida",
		"desvio"
	]
}
{
	"_id" : ObjectId("564c70d8518b583fbdba3ad9"),
	"description" : "Pokemon de teste",
	"name" : "testemon",
	"attack" : 8000,
	"defense" : 8000,
	"active" : false,
	"moves" : [
		"Investida",
		"desvio"
	]
}
{
	"_id" : ObjectId("5642961ec9222a3fc35f8e08"),
	"name" : "Pikachu",
	"description" : "Rato elétrico bem fofinho",
	"type" : "electric",
	"attack" : 55,
	"height" : 0.4,
	"defense" : 35,
	"moves" : [
		"Investida",
		"choque do trovao",
		"resplando electrico",
		"fogo que queima",
		"chute nas bolas",
		"desvio"
	],
	"active" : false
}
{
	"_id" : ObjectId("564e100f29ebfceefbd4a790"),
	"active" : false,
	"moves" : [
		"Investida",
		"desvio"
	]
}
{
	"_id" : ObjectId("5642998cc9222a3fc35f8e09"),
	"name" : "charmander",
	"description" : "tira fogo pela bunda",
	"type" : "fogo",
	"attack" : 54,
	"height" : 0.3,
	"active" : false,
	"moves" : [
		"Investida",
		"lanca-chamas",
		"resplando electrico",
		"fogo que queima",
		"chute nas bolas",
		"desvio"
	]
}
> 

```


## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
> var query = {$and:[{attack:{$lt: 50}}, {type:'agua'}]}
> db.pokemons.find(query).pretty()
>  nao tenho nada con tal parametro


```
