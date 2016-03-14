#MongoDB - Aula 04 - Ecercicio
Autor: Sóstenes freitas de andrade usuario:(sostenesfreitas)

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu,Squirtle, Bulbassauro e Charmander

```

BlackArch(mongod-3.2.1) be-mean-pokemons> var atkElt = ["thunderbolt","light speed"]
BlackArch(mongod-3.2.1) be-mean-pokemons> var query =  {"name":"Pikachu"}
BlackArch(mongod-3.2.1) be-mean-pokemons> var mod =    {$pushAll: {moves: atkElt}}
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
})
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56ce011287b6da7c45905f6d"),
      "name": "Pikachu",
      "description": "Pestinha Amarela",
      "type": "Elétrico",
      "attack": 55,
      "defense": 40,
      "height": 0.41,
      "moves": [
                "thunderbolt",
                "light speed"
               ]
}
Fetched 1 record(s) in 1ms

BlackArch(mongod-3.2.1) be-mean-pokemons> var atkWat = ["hydro pump","surf"]
BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {"name":"Squirtle"}
BlackArch(mongod-3.2.1) be-mean-pokemons> var mod = {$pushAll: {moves: atkWat}}
BlackArch(mongod-3.2.1) be-mean-pokemons> 
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
})
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56ce011287b6da7c45905f6b"),
      "name": "Squirtle",
      "description": "Tartaruga Azul",
      "type": "Água",
      "attack": 48,
      "defense": 65,
      "height": 0.51,
      "moves": [
                "hydro pump",
                "surf"
               ]
}
Fetched 1 record(s) in 1ms

BlackArch(mongod-3.2.1) be-mean-pokemons> var atkGra = ["solar beam","sleep powder"]
BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {"name":"Bulbassauro"}
BlackArch(mongod-3.2.1) be-mean-pokemons> var mod = {$pushAll: {moves: atkGra}}
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
})
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56ce017a87b6da7c45905f74"),
      "name": "Bulbassauro",
      "description": "Chicote de trepadeira",
      "type": "grama",
      "attack": 49,
      "height": 0.4,
      "moves": [
                "solar beam",
                "sleep powder"
               ]
}
Fetched 1 record(s) in 1ms

BlackArch(mongod-3.2.1) be-mean-pokemons> var atkFir = ["fire blaster","inferno"]
BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {"name":"Charmander"}
BlackArch(mongod-3.2.1) be-mean-pokemons> var mod = {$pushAll: {moves: atkFir}}
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
})
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56ce054887b6da7c45905f75"),
      "name": "Charmander",
      "description": "Dragão de fogo",
      "type": "fogo",
      "attack": 52,
      "defense": 40,
      "height": 0.6,
      "moves": [
                "fire blaster",
                "inferno"
               ]
}
Fetched 1 record(s) in 1ms
```


## Adicionar 1 movimento em todos os pokemons: 'desvio'.

```

BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {}
BlackArch(mongod-3.2.1) be-mean-pokemons> var mod = {$set: {moves:["desvio"]}}
BlackArch(mongod-3.2.1) be-mean-pokemons> var options = {multi: true}
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 27 existing record(s) in 1ms
WriteResult({
      "nMatched": 27,
      "nUpserted": 0,
      "nModified": 27
})
```
## Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com a valor `null` e a descrição : "Sem maiores informações".

```

BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {"name":"/AindaNaoExisteMon/i}
BlackArch(mongod-3.2.1) be-mean-pokemons> mod = {$setOnInsert: {name: "NaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"}
BlackArch(mongod-3.2.1) be-mean-pokemons> var options = {upsert:true}
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 11ms
WriteResult({
        "nMatched": 0,
        "nUpserted": 1,
        "nModified": 0,
        "_id": ObjectId("568333b8465179df99fcfdd8")
})
```
##Pesquisar todos os pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.
```
BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {moves:{$all["investida","dream eater"]}}
BlackArch(mongod-3.2.1) be-mean-pokemons>  db.pokemons.find(query)
{
      "_id": ObjectId("56c64b4304e657a13e0cd708"),
      "name": "darkrai",
      "attack": 200,
      "defense": 120,
      "height": 10,
      "description": "Melhor pokemon ever",
      "moves": [
                "desvio",
                "investida",
                "dream eater"
               ]
}
```
##Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito
```
BlackArch(mongod-3.2.1) be-mean-pokemons> var query  = {moves:{$all:["Spikes","Gyro Ball"]}}
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56cc5763c8b1a12ce58bb45a"),
      "name": "Ferrothorn",
      "attack": 94,
      "defense": 131,
      "height": 10,
      "description": "beBleyd",
      "moves": [
                "Spikes",
                "Leech Seed",
                "Gyro Ball",
                "Thunder Wave",
                "desvio"
               ]
}


```
##Pesquisar **todos** os pokemons que não são do tipo `eletrico`.
```
BlackArch(mongod-3.2.1) be-mean-pokemons>  var query = {"type":{$not:"eletrico"}}
{
        "_id": ObjectId("5670bde3dbd364f21b5949b5"),
        "name": "Bulbassauro",
        "description": "Chicote de trepadeira",
        "type": "grama",
        "attack": 49,
        "height": 0.4,
        "moves": [
                   "folha navalha",
                   "chicote de vinha",
                   "desvio"
                 ]
}
{
        "_id": ObjectId("5670bde8dbd364f21b5949b6"),
        "name": "Charmander",
        "description": "Esse é o cão chupando manga de fofinho",
        "type": "fogo",
        "attack": 52,
        "height": 0.6,
        "moves": [
                    "arranhão",
                    "lança chamas",
                    "desvio"
                 ]
}
{
        "_id": ObjectId("5670bdebdbd364f21b5949b7"),
        "name": "Squirtle",
        "description": "Ejeta água que passarinho não bebe",
        "type": "água",
        "attack": 48,
        "height": 0.5,
        "moves": [
                   "jato d'água",
                   "chicote de cauda",
                   "desvio"
                 ]
}
{
        "_id": ObjectId("5670bec5dbd364f21b5949b8"),
        "name": "Caterpie",
        "description": "Larva lutadora",
        "type": "inseto",
        "attack": 30,
        "height": 0.3,
        "defense": 35,
        "moves": [
                   "desvio"
                 ]
}
{
        "_id": ObjectId("568333b8465179df99fcfdd8"),
        "name": "AindaNaoExisteMon",
        "description": null,
        "type": null,
        "attack": null,
        "defense": null,
        "height": null
}
Fetched 5 record(s) in 12ms
```
##Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.
```
BlackArch(mongod-3.2.1) be-mean-pokemons> {$and:[{"moves":{$in:["investida"]}},{"defense":{$not:{$lte:49}}}]}
```
##Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
BlackArch(mongod-3.2.1) be-mean-pokemons> {$and:[{"type":/agua/i},{"attack":{$lt:50}}]}
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 11ms
WriteResult({
        "nRemoved": 1
})
```



















