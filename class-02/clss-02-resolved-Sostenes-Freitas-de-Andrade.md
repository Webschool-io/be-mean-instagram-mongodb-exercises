#MongoDB - Aula 02 - Ecercicio
Autor: Sóstenes freitas de andrade usuario:(sostenesfreitas)

##Criando database 
```
BlackArch(mongod-3.2.1) test> use be-mean-pokemons
switched to db be-mean-pokemons
BlackArch(mongod-3.2.1) be-mean-pokemons>
```
##Listando databases 
```
BlackArch(mongod-3.2.1) be-mean-pokemons> show dbs
be-mean-instagram → 0.000GB
be-mean-pokemons  → 0.000GB
be_mean           → 0.002GB
local             → 0.000GB
test              → 0.000GB
```
##Listando collections da database be-mean-pokemons 
```
BlackArch(mongod-3.2.1) be-mean-pokemons> show collections


```
##Cadastro dos pokemons 
```
BlackArch(mongod-3.2.1) be-mean-pokemons> var pokes = [

{"name":"darkrai","attack":200.0,"defense":120.0,"height":10.0},
{"name":"charizard","attack":150.0,"defense":50.0,"height":89.0},
{"name":"umbreon","attack":77.0,"defense":55.0,"height":44.0},
{"name":"vaporeon","attack":87.0,"defense":29.0,"height":54.0},
{"name":"mew","attack":200.0,"defense":209.0,"height":4.0},
{"name":"mewtwo","attack":300.0,"defense":290.0,"height":40.0},
{"name":"arceus","attack":400.0,"defense":390.0,"height":400.0}
]

BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokes)
```
#Lista de todos os pokemons da collections pokemons 
```
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find()
{
      "_id": ObjectId("56c64b4304e657a13e0cd708"),
      "name": "darkrai",
      "attack": 200,
      "defense": 120,
      "height": 10,
                
}
{
      "_id": ObjectId("56c64b6904e657a13e0cd709"),
      "name": "charizard",
      "attack": 150,
      "defense": 50,
      "height": 89
}
{
      "_id": ObjectId("56c64baa04e657a13e0cd70c"),
      "name": "umbreon",
      "attack": 77,
      "defense": 55,
      "height": 44
}
{
      "_id": ObjectId("56c64bde04e657a13e0cd70d"),
      "name": "vaporeon",
      "attack": 87,
      "defense": 29,
      "height": 54
}
{
      "_id": ObjectId("56c64bf304e657a13e0cd70e"),
      "name": "mew",
      "attack": 200,
      "defense": 209,
      "height": 4
}
{
      "_id": ObjectId("56c64c0404e657a13e0cd70f"),
      "name": "mewtwo",
      "attack": 300,
      "defense": 290,
      "height": 40
}
{
      "_id": ObjectId("56c64c2904e657a13e0cd710"),
      "name": "arceus",
      "attack": 400,
      "defense": 390,
      "height": 400
}
{
Fetched 8 record(s) in 2ms

```
#Query para buscar um pokemon 
```
BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {"name":"darkrai"}
BlackArch(mongod-3.2.1) be-mean-pokemons> var poke = db.pokemons.findOne(query)
BlackArch(mongod-3.2.1) be-mean-pokemons> poke
{
      "_id": ObjectId("56c64b4304e657a13e0cd708"),
      "name": "darkrai",
      "attack": 200,
      "defense": 120,
      "height": 10
}
```
#Atualização do Pokemon selecionado 
```

BlackArch(mongod-3.2.1) be-mean-pokemons> poke.description = "Melhor pokemon ever"
Melhor pokemon ever
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
})
```
