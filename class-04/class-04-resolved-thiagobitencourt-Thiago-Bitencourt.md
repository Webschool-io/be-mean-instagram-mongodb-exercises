# MongoDB - Aula 04 - Exercício
autor: Thiago R. M. Bitencourt

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
> var query = {name: {$in: [/pikachu/i, /squirtle/i, /bulbasauro/i, /charmander/i]}}
> var mod = {moves: {$pushAll: ['cambalhota', 'ferroada']}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
> db.pokemons.update(query, mod, options)
  WriteResult({ "nMatched" : 4, "nUpserted" : 0 })
> db.pokemons.find(query).pretty()
  {
  	"_id" : ObjectId("577db0ea991e41068ed4fb6d"),
  	"attack" : 40,
  	"description" : "Fogo vivo",
  	"height" : 1.7,
  	"moves" : [
  		"cambalhota",
  		"ferroada"
  	],
  	"name" : "Charmander",
  	"type" : "fogo"
  }
  {
  	"_id" : ObjectId("577db13a991e41068ed4fb6e"),
  	"attack" : 10,
  	"description" : "dinosauro verde",
  	"height" : 0.7,
  	"moves" : [
  		"cambalhota",
  		"ferroada"
  	],
  	"name" : "Bulbasauro",
  	"type" : "grama"
  }
  {
  	"_id" : ObjectId("577c76ec07db620be3e755e8"),
  	"active" : false,
  	"attack" : "21",
  	"description" : "Rato elétrico",
  	"height" : 0.8,
  	"moves" : [
  		"investida",
  		"Choque do Tovao",
  		"cambalhota",
  		"ferroada"
  	],
  	"name" : "Pikachu",
  	"type" : "elétrico"
  }
  {
  	"_id" : ObjectId("577da373d3105bd467948ffd"),
  	"active" : false,
  	"attack" : 17,
  	"description" : "tartarugazinha",
  	"height" : 0.4,
  	"moves" : [
  		"investida",
  		"hidro bomba",
  		"cambalhota",
  		"ferroada"
  	],
  	"name" : "squirtle",
  	"type" : "agua"
  }
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
> var query = {}
> var mod = {$push: {moves: ['desvio']}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
  WriteResult({ "nMatched" : 17, "nUpserted" : 0 })
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
> var query = {name: /AindaNaoExisteMon/i}
> var mod = {$setOnInsert: {description: "Sem maiores informações", name: "AindaNaoExisteMon", attack: null, defense: null, moves: null, type: null, height: null}}
> var options = {upsert: true}
> db.pokemons.update(query, mod, options)
  WriteResult({
  	"nMatched" : 0,
  	"nUpserted" : 1,
  	"_id" : ObjectId("577db6c6d3105bd467948fff")
  })
> db.pokemons.find(query).pretty()
  {
  	"_id" : ObjectId("577db6c6d3105bd467948fff"),
  	"attack" : null,
  	"defense" : null,
  	"description" : "Sem maiores informações",
  	"height" : null,
  	"moves" : null,
  	"name" : "AindaNaoExisteMon",
  	"type" : null
  }
```

## Pesquisar todos os pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
> var query = {moves: {$all: [/investida/i, /ferroada/i]}}
> db.pokemons.find(query).pretty()
  {
  	"_id" : ObjectId("577c76ec07db620be3e755e8"),
  	"active" : false,
  	"attack" : "21",
  	"description" : "Rato elétrico",
  	"height" : 0.8,
  	"moves" : [
  		"investida",
  		"Choque do Tovao",
  		"cambalhota",
  		"ferroada"
  	],
  	"name" : "Pikachu",
  	"type" : "elétrico"
  }
  {
  	"_id" : ObjectId("577da373d3105bd467948ffd"),
  	"active" : false,
  	"attack" : 17,
  	"description" : "tartarugazinha",
  	"height" : 0.4,
  	"moves" : [
  		"investida",
  		"hidro bomba",
  		"cambalhota",
  		"ferroada",
  		"desvio"
  	],
  	"name" : "squirtle",
  	"type" : "agua"
  }
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
> var query = {moves: {$all: [/cambalhota/i, /ferroada/i]}}
> db.pokemons.find(query).pretty()
  {
  	"_id" : ObjectId("577db0ea991e41068ed4fb6d"),
  	"attack" : 40,
  	"description" : "Fogo vivo",
  	"height" : 1.7,
  	"moves" : [
  		"cambalhota",
  		"ferroada"
  	],
  	"name" : "Charmander",
  	"type" : "fogo"
  }
  {
  	"_id" : ObjectId("577db13a991e41068ed4fb6e"),
  	"attack" : 10,
  	"description" : "dinosauro verde",
  	"height" : 0.7,
  	"moves" : [
  		"cambalhota",
  		"ferroada"
  	],
  	"name" : "Bulbasauro",
  	"type" : "grama"
  }
  {
  	"_id" : ObjectId("577c76ec07db620be3e755e8"),
  	"active" : false,
  	"attack" : "21",
  	"description" : "Rato elétrico",
  	"height" : 0.8,
  	"moves" : [
  		"investida",
  		"Choque do Tovao",
  		"cambalhota",
  		"ferroada"
  	],
  	"name" : "Pikachu",
  	"type" : "elétrico"
  }
  {
  	"_id" : ObjectId("577da373d3105bd467948ffd"),
  	"active" : false,
  	"attack" : 17,
  	"description" : "tartarugazinha",
  	"height" : 0.4,
  	"moves" : [
  		"investida",
  		"hidro bomba",
  		"cambalhota",
  		"ferroada",
  		"desvio"
  	],
  	"name" : "squirtle",
  	"type" : "agua"
  }
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
> var query = {type: {$ne: "elétrico"}}
> db.pokemons.find(query).pretty()
{
  "_id" : ObjectId("577db0ea991e41068ed4fb6d"),
  "attack" : 40,
  "description" : "Fogo vivo",
  "height" : 1.7,
  "moves" : [
    "cambalhota",
    "ferroada"
  ],
  "name" : "Charmander",
  "type" : "fogo"
}
{
  "_id" : ObjectId("577db13a991e41068ed4fb6e"),
  "attack" : 10,
  "description" : "dinosauro verde",
  "height" : 0.7,
  "moves" : [
    "cambalhota",
    "ferroada"
  ],
  "name" : "Bulbasauro",
  "type" : "grama"
}
{
  "_id" : ObjectId("577da373d3105bd467948ffd"),
  "active" : false,
  "attack" : 17,
  "description" : "tartarugazinha",
  "height" : 0.4,
  "moves" : [
    "investida",
    "hidro bomba",
    "cambalhota",
    "ferroada",
    "desvio"
  ],
  "name" : "squirtle",
  "type" : "agua"
}
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
> var query = {$and: [{moves: {$in: [/investida/i]}}, {defense: {$gte: 49}}]}
> db.pokemons.find(query).pretty()
  {
  	"_id" : ObjectId("577c73842cfe017bc74f3e7e"),
  	"active" : false,
  	"attack" : 7999,
  	"defense" : 8000,
  	"description" : "testeeeeeeeee",
  	"moves" : [
  		"investida"
  	],
  	"name" : "Testemon"
  }
  {
  	"_id" : ObjectId("577b1901fe6950263ad63a6a"),
  	"active" : false,
  	"attack" : 62,
  	"defense" : 67,
  	"description" : "When NIDORINA are with their friends or family, they keep their barbs tucked away to prevent hurting each other.",
  	"height" : 0.2,
  	"moves" : [
  		"investida"
  	],
  	"name" : "Nidorina",
  	"type" : "veneno"
  }
  {
  	"_id" : ObjectId("577b1901fe6950263ad63a64"),
  	"active" : false,
  	"attack" : 45,
  	"defense" : 50,
  	"description" : "In battle, it flaps its wings at high speed to release highly toxic dust into the air.",
  	"height" : 0.3,
  	"heigth" : 0.3,
  	"moves" : [
  		"investida"
  	],
  	"name" : "Butterfree",
  	"type" : "inseto"
  }
  {
  	"_id" : ObjectId("577b1901fe6950263ad63a65"),
  	"active" : false,
  	"attack" : 85,
  	"defense" : 69,
  	"description" : "The frightening patterns on its belly have been studied. Six variations have been confirmed.",
  	"height" : 0.9,
  	"moves" : [
  		"investida"
  	],
  	"name" : "Arbok",
  	"type" : "veneno"
  }
```  

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
> var query = {type: /agua/i, attack: {$lt: 50}}
> db.pokemons.remove(query)
  WriteResult({ "nRemoved" : 1 })
```
