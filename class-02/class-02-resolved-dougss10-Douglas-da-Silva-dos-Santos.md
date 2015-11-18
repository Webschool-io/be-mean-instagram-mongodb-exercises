# MongoDB - Aula 02 - Exercício
autor: Douglas da Silva dos Santos

## Listagem das databases (passo 2)

...

> show dbs
CursoDB   0.078GB
admin     (empty)
be-mean   0.078GB
colecao1  0.078GB
local     0.078GB
> 

...

## Listagem das coleções (passo 3)

...

> show collections
> 

...

## Cadastro dos pokemons (passo 4)

...

var pokemons = [{"name": "Pikachu", "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.", "attack":"30", "defense":"20", "height":"0.4"}, {"name": "Sandslash",  "description": "Sandslash's body is covered by tough spikes, which are hardened sections of its hide.", "attack":"50", "defense":"50", "height":"1.0"}, {"name": "Nidoran",  "description": "Nidoran? has barbs that secrete a powerful poison.", "attack":"30", "defense":"20", "height":"0.4"}, {"name": "Raichu",  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.", "attack":"50", "defense":"30", "height":"0.8"}, {"name": "Sandshrew",  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert.", "attack":"40", "defense":"40", "height":"0.6"}]


> db.pokemons.insert(pokemons)
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
> 

...

## Lista dos pokemons (passo 5)

...

> db.pokemons.find()
{ "_id" : ObjectId("56489a87bb2ba66f85e26f7e"), "name" : "Pikachu", "description" : "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.", "attack" : "30", "defense" : "20", "height" : "0.4" }
{ "_id" : ObjectId("56489a87bb2ba66f85e26f7f"), "name" : "Sandslash", "description" : "Sandslash's body is covered by tough spikes, which are hardened sections of its hide.", "attack" : "50", "defense" : "50", "height" : "1.0" }
{ "_id" : ObjectId("56489a87bb2ba66f85e26f80"), "name" : "Nidoran", "description" : "Nidoran? has barbs that secrete a powerful poison.", "attack" : "30", "defense" : "20", "height" : "0.4" }
{ "_id" : ObjectId("56489a87bb2ba66f85e26f81"), "name" : "Raichu", "description" : "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.", "attack" : "50", "defense" : "30", "height" : "0.8" }
{ "_id" : ObjectId("56489a87bb2ba66f85e26f82"), "name" : "Sandshrew", "description" : "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert.", "attack" : "40", "defense" : "40", "height" : "0.6" }
> 

...

## Pikachu (passo 6)

...

> var query = {name : "Pikachu"}
> var poke = db.pokemons.findOne(query)
> poke
{
	"_id" : ObjectId("564a82719379345ca8ed7abb"),
	"name" : "Pikachu",
	"description" : "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.",
	"attack" : "30",
	"defense" : "20",
	"height" : "0.4"
}
> 

...

## Atualização do Pikachu (passo 6)

...

> poke.description = "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.(Modified)"

> db.pokemons.save(poke)

> var poke = db.pokemons.findOne(query)
> poke
{
	"_id" : ObjectId("564a82719379345ca8ed7abb"),
	"name" : "Pikachu",
	"description" : "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.(Modified)",
	"attack" : "30",
	"defense" : "20",
	"height" : "0.4"
}

...

