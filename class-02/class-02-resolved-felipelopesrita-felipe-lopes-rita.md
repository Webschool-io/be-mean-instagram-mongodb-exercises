# MongoDB - Aula 02 - Exercício
autor: Felipe José Lopes Rita

## Listagem das databases (passo 2)
```
StarKiller(mongod-3.2.0) be-mean-pokemons> show dbs
be-mean           → 0.008GB
be-mean-instagram → 0.000GB
local             → 0.000GB
```

## Listagem das coleções (passo 3)
```
StarKiller(mongod-3.2.0) be-mean-pokemons> db.createCollection("pokemons")
{
  "ok": 1
}
StarKiller(mongod-3.2.0) be-mean-pokemons> show collections
pokemons → 0.000MB / 0.004MB
```
## Cadastro dos pokemons (passo 4)
```
StarKiller(mongod-3.2.0) be-mean-pokemons> var pokemons = [
	{"name":"Cyndaquil","description":"Tem fogo nas costas e é fofo pra caralho","attack":52,"defense":43,"height":0.5},
	{"name":"Minun","description":"Coelho elétrico que parece mas não tem nada a ver com o pikachu", "attack":40,"defense":50,"height":0.4},
	{"name":"Charizard","description":"Pokemon mais pica das galáxias", "attack":84,"defense":78,"height":1.7},
	{"name":"Pidgey","description":"Pomba comum de Sampa, só que não caga em você (acho)", "attack":45,"defense":40,"height":0.3},
	{"name":"Zorua","description":"Raposa preta (deve ser do capeta) foda e fofa","attack":65,"defense":40,"height":0.7}
]

StarKiller(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 4ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})


```

## Lista dos pokemons (passo 5)
```
StarKiller(mongod-3.2.0) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56b4237765cd05bf6bff3322"),
  "name": "Cyndaquil",
  "description": "Tem fogo nas costas e é fofo pra caralho",
  "attack": 52,
  "defense": 43,
  "height": 0.5
}
{
  "_id": ObjectId("56b4237765cd05bf6bff3323"),
  "name": "Minun",
  "description": "Coelho elétrico que parece mas não tem nada a ver com o pikachu",
  "attack": 40,
  "defense": 50,
  "height": 0.4
}
{
  "_id": ObjectId("56b4237765cd05bf6bff3324"),
  "name": "Charizard",
  "description": "Pokemon mais pica das galáxias",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}
{
  "_id": ObjectId("56b4237765cd05bf6bff3325"),
  "name": "Pidgey",
  "description": "Pomba comum de Sampa, só que não caga em você (acho)",
  "attack": 45,
  "defense": 40,
  "height": 0.3
}
{
  "_id": ObjectId("56b4237765cd05bf6bff3326"),
  "name": "Zorua",
  "description": "Raposa preta (deve ser do capeta) foda e fofa",
  "attack": 65,
  "defense": 40,
  "height": 0.7
}
Fetched 5 record(s) in 7ms
```

## Buscar um pokemon (passo 6)
```
StarKiller(mongod-3.2.0) be-mean-pokemons> var query = {'name':'Cyndaquil'}
StarKiller(mongod-3.2.0) be-mean-pokemons> var poke = db.pokemons.findOne(query)
StarKiller(mongod-3.2.0) be-mean-pokemons> poke
{
  "_id": ObjectId("56b4237765cd05bf6bff3322"),
  "name": "Cyndaquil",
  "description": "Tem fogo nas costas e é fofo pra caralho",
  "attack": 52,
  "defense": 43,
  "height": 0.5
}
```

## Atualização do pokemon (passo 6)
```
StarKiller(mongod-3.2.0) be-mean-pokemons> poke.description = "Sempre escolhia ele quando jogava pokemon Gold & Silver"
Sempre escolhia ele quando jogava pokemon Gold & Silver
StarKiller(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```