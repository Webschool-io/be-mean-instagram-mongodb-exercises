# MongoDB - Aula 03 - Exercicio
Autor: Robson Maia


## Liste todos Pokemons com a altura menor que 0.5;
```
> var query = {height:{$lt: 0.5}}
> db.pokemons.find(query)
{ 
	"_id" : ObjectId("59002653328f0adff7ac34a5"), 
	"name" : "Pikachu", 
	"description" : "Foi alterado", 
	"attack" : 55, 
	"defense" : 40, 
	"height" : 0.4 
}

{
 	"_id" : ObjectId("59002653328f0adff7ac34a7"),
	"name" : "Nidoran", 
	"description" : "Although small, its venomous barbs render this POKMON dangerous. The female has smaller horns.", 
	"attack" : 47, 
	"defense" : 52, 
	"height" : 0.4 
}
> 

```
## Liste todos Pokemons com a altura maior ou igual que 0.5
```
> var query = {height:{$gte: 0.5}}
> db.pokemons.find(query)
{ 
	"_id" : ObjectId("59002653328f0adff7ac34a6"), 
	"name" : "Sandshrew", "description" : 
	"To protect itself from attackers, it curls up into a ball. It lives in arid regions with minimal rainfall.", 
	"attack" : 75, 
	"defense" : 85, 
	"height" : 0.6 
}

{ 
	"_id" : ObjectId("59002653328f0adff7ac34a8"), 
	"name" : "Clefairy", 
	"description" : "Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.", 
	"attack" : 45, 
	"defense" : 48, 
	"height" : 0.6
}

{ 
	"_id" : ObjectId("59002653328f0adff7ac34a9"), 
	"name" : "Vulpix", 
	"description" : "If it is attacked by an enemy that is stronger than itself, it feigns injury to fool the enemy and escapes.", 
	"attack" : 41, 
	"defense" : 40, 
	"height" : 0.6
}
> 

```
## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** attack maior ou igual a 55
```
BlackArch(mongod-3.2.1) be-mean-pokemons> query = {$and: [ { height: {$lte: 0.5} }, { attack: {$gte: 55 } } ] }

BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56cc5195935d3f5fe428cc50"),
      "name": "Pikachu",
      "type": "electric",
      "attack": 55,
      "defense": 30,
      "height": 0.4
}

Fetched 1 record(s) in 2ms
```
## Liste todos Pokemons com o name `Pikachu` OU com altura menor ou igual que 0.5
```
BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {$or:[{"name":"pikachu"},{"height":{$lte:0.5}}]}
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56cc5195935d3f5fe428cc50"),
      "name": "voltorb",
      "attack": 12,
      "defense": 11,
      "height": 0.3
}
{
      "_id": ObjectId("56cc5195935d3f5fe428cc51"),
      "name": "evee",
      "attack": 30,
      "defense": 20,
      "height": 0.4
}
{
      "_id": ObjectId("56cc5195935d3f5fe428cc52"),
      "name": "weezing",
      "attack": 33,
      "defense": 12,
      "height": 0.4
}
{
      "_id": ObjectId("56cc55ecc8b1a12ce58bb459"),
      "name": "pikachu",
      "attack": 22,
      "defense": 11,
      "height": 0.3
}
Fetched 4 record(s) in 2ms
```
## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```

BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {$and:[{"attack":{$gte:48}},{"height":{$lte:0.5}}]}
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56cc5763c8b1a12ce58bb45a"),
      "name": "ferrothorn",
      "attack": 50,
      "defense": 40,
      "height": 0.4
}
Fetched 1 record(s) in 1ms
```
