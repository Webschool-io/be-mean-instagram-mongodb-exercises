###MongoDB - Aula 02 - Exercício
Autor: Hudson Brendon

##Criando database
```
ubuntu(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons
```

##Listando databases
```
ubuntu(mongod-3.0.7) be-mean-pokemons> show dbs
local              0.078GB
be-mean            0.203GB
pokemons           0.078GB
be-mean-instagram  0.078GB
```

##Listando collections
```
> show collections
pokemons
system.indexes
```

##Cadastro dos pokemons
```
> var pokemon = [{'name':'Beedrill','description':'Mel deus do céu!','type':'bug', attack: 70, defense: 30, height: 1.0},{'name':'Raichu','description':'Tipo o pikachu, só que sem a pika','type':'bug', attack: 90, defense: 30, height: 0.8},{'name':'Vulpix','description':'Lindos cachos','type':'fire', attack: 40, defense: 30, height: 0.6},{'name':'Machamp','description':'Veem monstro!','type':'fighting', attack: 100, defense: 40, height: 1.6},{'name':'Rapidash','description':'Ta pegando fogo bixo!','type':'fire', attack: 80, defense: 30, height: 1.7},{'name':'Weedle','description':'Minhoca arregaça cú','type':'bug', attack: 30, defense: 10, height: 0.3}]
> db.pokemons.save(pokemon)

BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 6,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]
})
```

##Lista de todos os pokemons
```
{ "_id" : ObjectId("564921350910df3d8696d709"), "name" : "Beedrill", "description" : "Mel deus do céu!", "type" : "bug", "attack" : 70, "defense" : 30, "height" : 1 }
{ "_id" : ObjectId("564921350910df3d8696d70a"), "name" : "Raichu", "description" : "Tipo o pikachu, só que sem a pika", "type" : "bug", "attack" : 90, "defense" : 30, "height" : 0.8 }
{ "_id" : ObjectId("564921350910df3d8696d70b"), "name" : "Vulpix", "description" : "Lindos cachos", "type" : "fire", "attack" : 40, "defense" : 30, "height" : 0.6 }
{ "_id" : ObjectId("564921350910df3d8696d70c"), "name" : "Machamp", "description" : "Veem monstro!", "type" : "fighting", "attack" : 100, "defense" : 40, "height" : 1.6 }
{ "_id" : ObjectId("564921350910df3d8696d70d"), "name" : "Rapidash", "description" : "Ta pegando fogo bixo!", "type" : "fire", "attack" : 80, "defense" : 30, "height" : 1.7 }
{ "_id" : ObjectId("564921350910df3d8696d70e"), "name" : "Weedle", "description" : "Minhoca arregaça cú", "type" : "bug", "attack" : 30, "defense" : 10, "height" : 0.3 }
```

##Query para buscar o pokemon
```
var query = {name:'Rapidash'}
> var poke = db.pokemons.find(query)
> poke
{ "_id" : ObjectId("564921350910df3d8696d70d"), "name" : "Rapidash", "description" : "Ta pegando fogo bixo!", "type" : "fire", "attack" : 80, "defense" : 30, "height" : 1.7 }
```

##Atualizando a descrição do Pokemon
```
> var query = {name:'Rapidash'}
> var poke = db.pokemons.findOne(query)
> poke.description = 'Quem é esse pokemon?'
Éssa fera aí mêu!
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```
