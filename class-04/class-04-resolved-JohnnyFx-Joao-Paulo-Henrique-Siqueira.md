# MongoDB - Aula 04 - Exercício
autor: Joao Paulo Henrique Siqueira

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
var query = {$or:[{name:/pikachu/i}, {name:/squirtle/i}, {name:/bulbassauro/i}, {name:/charmander/i}]}

var mod = {$pushAll:{moves:["ataque de fúria","ataque rápido"]}}


var options = {multi:true}

db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 3ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})


```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
var query = {}
var attacks = ["desvio"]
var mod = {$set:{moves:attack}}
var options = {multi:true}

> db.pokemons.update(query,mod,options)
Updated 9 existing record(s) in 2ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})

})



```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = {"name": /AindaNaoExisteMon/i}

var mod = {setOnInsert:{"name":"AindaNaoExisteMon"
	,attack:null
	,defense:null
	,height:null
	,"description":"Sem maiores descrições"
	}}
var options = {upsert:true}

db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564f33e867a7e09ab46aed0f")
})


```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```

 var query = {moves:{$all:['investida','furia']} }
 db.pokemons.find(query)	

{
  "_id": ObjectId("5642af03ef0bc6adde3ae402"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "desvio",
    "investida",
    "furia"
  ]
}
{
  "_id": ObjectId("5642af35ef0bc6adde3ae403"),
  "name": "Squirtle",
  "description": "Ejeta agua que passarinho não bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5,
  "active": true,
  "moves": [
    "desvio",
    "investida",
    "furia"
  ]
}
{
  "_id": ObjectId("5642b4066aeb57418bf00ea8"),
  "nome": "Caterpie",
  "description": "Larva que avua",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "desvio",
    "investida",
    "furia"
  ]
}
{
  "_id": ObjectId("564f1cc667a7e09ab46aed0b"),
  "active": true,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "desvio",
    "investida",
    "furia"
  ]
}
{
  "_id": ObjectId("564f204d67a7e09ab46aed0c"),
  "evolui": false,
  "name": "Raichu",
  "attack": 61,
  "defense": 62,
  "height": 1.5,
  "description": "Rato eletrico amarelo",
  "moves": [
    "desvio",
    "investida",
    "furia"
  ]
}
{
  "_id": ObjectId("5642ac818e669fee4a0ba12b"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": true,
  "evolui": false,
  "moves": [
    "desvio",
    "investida",
    "furia"
  ]
}
{
  "_id": ObjectId("564f32bf67a7e09ab46aed0d"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "furia"
  ]
}
Fetched 7 record(s) in 4ms

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
var query = { moves: { $in: [/ataque rápido
/i] }}
db.pokemons.find(query)

{
  "_id": ObjectId("5642ac818e669fee4a0ba12b"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": true,
  "evolui": false,
  "moves": [
    "investida",
    "ataque de fúria",
    "ataque rápido"
  ]
}
{
  "_id": ObjectId("564fc53d10fc1478a0915a95"),
  "name": "Bulbassauro",
  "active": true,
  "type": "grama",
  "attack": 60,
  "defense": 20,
  "height": 2.1,
  "description": "Chicoteador",
  "moves": [
    "investida",
    "ataque de fúria",
    "ataque rápido"
  ]
}
{
  "_id": ObjectId("5650679d10fc1478a0915a96"),
  "name": "Squirtle",
  "active": true,
  "type": "agua",
  "attack": 58,
  "defense": 50,
  "height": 2.6,
  "description": "Tartaragua de agua",
  "moves": [
    "investida",
    "ataque de fúria",
    "ataque rápido"
  ]
}
{
  "_id": ObjectId("565067d910fc1478a0915a97"),
  "name": "Charmander",
  "active": true,
  "type": "fogo",
  "attack": 62,
  "defense": 50,
  "height": 2.8,
  "description": "Dragao de fogo",
  "moves": [
    "investida",
    "ataque de fúria",
    "ataque rápido"
  ]
}
Fetched 4 record(s) in 1ms

```

## Pesquisar **todos** que não são do tipo 'elétrico'.##
```
var query = {type:{$ne:"eletric"}}
db.pokemons.find(query)


{
  "_id": ObjectId("5642af03ef0bc6adde3ae402"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "desvio",
    "investida",
    "furia"
  ]
}
{
  "_id": ObjectId("5642af35ef0bc6adde3ae403"),
  "name": "Squirtle",
  "description": "Ejeta agua que passarinho não bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5,
  "active": true,
  "moves": [
    "desvio",
    "investida",
    "furia"
  ]
}
{
  "_id": ObjectId("5642b4066aeb57418bf00ea8"),
  "nome": "Caterpie",
  "description": "Larva que avua",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "desvio",
    "investida",
    "furia"
  ]
}

{
  "_id": ObjectId("564f3b8267a7e09ab46aed10"),
  "setOnInsert": {
    "name": "AindaNaoExisteMon",
    "attack": null,
    "defense": null,
    "height": null,
    "description": "Sem maiores descrições"
  },
  "type": null
}

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
 var query = {$and:[{moves:{$in:[/investida/i]}},{defense:{$gte:49}}]}
	
 db.pokemons.find(query)

{
  "_id": ObjectId("564f204d67a7e09ab46aed0c"),
  "evolui": false,
  "name": "Raichu",
  "attack": 61,
  "defense": 62,
  "height": 1.5,
  "description": "Rato eletrico amarelo",
  "moves": [
    "investida"
  ],
  "type": "eletric",
  "active": true
}
{
  "_id": ObjectId("5650679d10fc1478a0915a96"),
  "name": "Squirtle",
  "active": true,
  "type": "agua",
  "attack": 58,
  "defense": 50,
  "height": 2.6,
  "description": "Tartaragua de agua",
  "moves": [
    "investida",
    "ataque de fúria",
    "ataque rápido"
  ]
}
{
  "_id": ObjectId("565067d910fc1478a0915a97"),
  "name": "Charmander",
  "active": true,
  "type": "fogo",
  "attack": 62,
  "defense": 50,
  "height": 2.8,
  "description": "Dragao de fogo",
  "moves": [
    "investida",
    "ataque de fúria",
    "ataque rápido"
  ]
}
Fetched 3 record(s) in 3ms




```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var query = {$and:[{type:"agua"},{attack:{$lt:50}}]}

db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})


```
