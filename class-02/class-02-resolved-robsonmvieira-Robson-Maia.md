###MongoDB - Aula 02 - Exercício
Autor: Robson Maia

##Criando database
```
> use be-mean-pokemons;
switched to db be-mean-pokemons

```

##Listando databases
```
> show dbs
admin        0.000GB
be-mean-vip  0.003GB
cadastrodb   0.000GB
clientes     0.000GB
local        0.000GB
twitterdb    0.000GB
> 

```

##Listando collections
```
> show collections;
> 


```


##Cadastro de pokemons
```
dell-marlom(mongod-3.0.9) be-mean-pokemons> var pokemons = [{'name':'Pikachu','description':'It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose.',attack: 55, defense: 40, height: 0.4},{'name':'Sandshrew','description':'To protect itself from attackers, it curls up into a ball. It lives in arid regions with minimal rainfall.',attack: 75, defense: 85, height: 0.6},{'name':'Nidoran','description':'Although small, its venomous barbs render this POKMON dangerous. The female has smaller horns.',attack: 47, defense: 52, height: 0.4},{'name':'Clefairy','description':'Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.',attack: 45, defense: 48, height: 0.6},{'name':'Vulpix','description':'If it is attacked by an enemy that is stronger than itself, it feigns injury to fool the enemy and escapes.',attack: 41, defense: 40, height: 0.6}]

> db
be-mean-pokemons
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

```

##Lista dos pokemons
```
dell-marlom(mongod-3.0.9) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56c0bad68f26b51a97f400eb"),
  "name": "Pikachu",
  "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose.",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("56c0bad68f26b51a97f400ec"),
  "name": "Sandshrew",
  "description": "To protect itself from attackers, it curls up into a ball. It lives in arid regions with minimal rainfall.",
  "attack": 75,
  "defense": 85,
  "height": 0.6
}
{
  "_id": ObjectId("56c0bad68f26b51a97f400ed"),
  "name": "Nidoran",
  "description": "Although small, its venomous barbs render this POKMON dangerous. The female has smaller horns.",
  "attack": 47,
  "defense": 52,
  "height": 0.4
}
{
  "_id": ObjectId("56c0bad68f26b51a97f400ee"),
  "name": "Clefairy",
  "description": "Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.",
  "attack": 45,
  "defense": 48,
  "height": 0.6
}
{
  "_id": ObjectId("56c0bad68f26b51a97f400ef"),
  "name": "Vulpix",
  "description": "If it is attacked by an enemy that is stronger than itself, it feigns injury to fool the enemy and escapes.",
  "attack": 41,
  "defense": 40,
  "height": 0.6
}
Fetched 5 record(s) in 2ms
```

##Pokemon
```
> var query = {"name" : "Pikachu"}
> db.pokemons.find(query)
{ "_id" : ObjectId("59002653328f0adff7ac34a5"), "name" : "Pikachu", "description" : "It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose.", "attack" : 55, "defense" : 40, "height" : 0.4 }
> 

```

##Atualização do Pokemon
```
> var query = {"name" : "Pikachu"}
> var poke = db.pokemons.findOne(query)
> poke
{
	"_id" : ObjectId("59002653328f0adff7ac34a5"),
	"name" : "Pikachu",
	"description" : "It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose.",
	"attack" : 55,
	"defense" : 40,
	"height" : 0.4
}
> poke.description = 'Foi alterado'
Foi alterado
> db.pokemons.save(pode)
2017-04-26T02:04:17.619-0300 E QUERY    [main] ReferenceError: pode is not defined :
@(shell):1:1
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

```
