# MongoDB - Aula 02 - Exercício
autor: Leonardo Filipe

## Listagem das databases (passo 2)
```
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> show dbs
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
be-mean-pokemons  → 0.000GB
be-mean-teste     → 0.000GB
local             → 0.000GB
```


## Listagem das coleções (passo 3)
```
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> show collections
test → 0.000MB / 0.016MB
```


## Cadastro dos pokemons (passo 4)
```
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokes.insert({name:'Bulbasaur',description:'Alface lutadora',attack:10,defense:12,height:0.3})
Inserted 1 record(s) in 25ms
WriteResult({
"nInserted": 1
})
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokes.insert({name:'Ivysaur',description:'Repolho lutador',attack:20,defense:24,height:0.45})
Inserted 1 record(s) in 5ms
WriteResult({
"nInserted": 1
})
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokes.insert({name:'Venusaur',description:'Rúcula lutadora',attack:30,defense:36,height:0.6})
Inserted 1 record(s) in 1ms
WriteResult({
"nInserted": 1
})
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokes.insert({name:'Charmander',description:'Tem fogo no rabo',attack:12,defense:10,height:0.29})
Inserted 1 record(s) in 1ms
WriteResult({
"nInserted": 1
})
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokes.insert({name:'Charmeleon',description:'Tem fogo ainda no rabo',attack:24,defense:20,height:0.5})
Inserted 1 record(s) in 1ms
WriteResult({
"nInserted": 1
})
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokes.insert({name:'Charizard',description:'Tem fogo no rabo e asas',attack:36,defense:30,height:0.7})
Inserted 1 record(s) in 1ms
WriteResult({
"nInserted": 1
})
```


## Lista dos pokemons (passo 5)
```
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokes.find()
{
"_id": ObjectId("5681beed75bb4f2d96502793"),
"name": "Bulbasaur",
"description": "Alface lutadora",
"attack": 10,
"defense": 12,
"height": 0.3
}
{
"_id": ObjectId("5681bf1775bb4f2d96502794"),
"name": "Ivysaur",
"description": "Repolho lutador",
"attack": 20,
"defense": 24,
"height": 0.45
}
{
"_id": ObjectId("5681bf3a75bb4f2d96502795"),
"name": "Venusaur",
"description": "Rúcula lutadora",
"attack": 30,
"defense": 36,
"height": 0.6
}
{
"_id": ObjectId("5681bf7975bb4f2d96502796"),
"name": "Charmander",
"description": "Tem fogo no rabo",
"attack": 12,
"defense": 10,
"height": 0.29
}
{
"_id": ObjectId("5681bfaf75bb4f2d96502797"),
"name": "Charmeleon",
"description": "Tem fogo ainda no rabo",
"attack": 24,
"defense": 20,
"height": 0.5
}
{
"_id": ObjectId("5681bfe775bb4f2d96502798"),
"name": "Charizard",
"description": "Tem fogo no rabo e asas",
"attack": 36,
"defense": 30,
"height": 0.7
}
Fetched 6 record(s) in 11ms
```


## Pikachu (passo 6)
```
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> var poke = db.pokes.findOne({name:"Charmeleon"})
```


## Atualização do Pikachu (passo 6)
```
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> poke.description = "Tem mais fogo ainda no rabo"
Tem mais fogo ainda no rabo
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokes.save(poke)
Updated 1 existing record(s) in 9ms
WriteResult({
"nMatched": 1,
"nUpserted": 0,
"nModified": 1
})
```