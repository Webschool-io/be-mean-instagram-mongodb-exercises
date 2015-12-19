# MongoDB - Aula 04 - Exercício
** autor: Maurício José da Silva Júnior**

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
mjunior(mongod-3.0.7) be-mean-instagram> 
mjunior(mongod-3.0.7) be-mean-instagram> query = {$or: [{name:/pikachu/i},{name:/squirtle/i},{name:/bulbassauro/i},{name:/charmander/i}]}
{
  "$or": [
    {
      "name": /pikachu/i
    },
    {
      "name": /squirtle/i
    },
    {
      "name": /bulbassauro/i
    },
    {
      "name": /charmander/i
    }
  ]
}
mjunior(mongod-3.0.7) be-mean-instagram> mod = {$pushAll:{moves:['Ataque01','Ataque02']}}
{
  "$pushAll": {
    "moves": [
      "Ataque01",
      "Ataque02"
    ]
  }
}
mjunior(mongod-3.0.7) be-mean-instagram> options = {multi:true}
{
  "multi": true
}
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 37ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
mjunior(mongod-3.0.7) be-mean-instagram>
```

Pokemons atualizados

```
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56426f5aa4e4c4604c3cd104"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "Ataque01",
    "Ataque02"
  ]
}
{
  "_id": ObjectId("56426f6ba4e4c4604c3cd105"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "Ataque01",
    "Ataque02"
  ]
}
{
  "_id": ObjectId("564d6250b5605ebec8fc3151"),
  "name": "Squirtle",
  "active": true,
  "attack": 48,
  "defense": 65,
  "description": "Essa é a descrição do squirtle mas eu nao entendo nada de pokemon",
  "moves": [
    "investida",
    "Ataque01",
    "Ataque02"
  ]
}
{
  "_id": ObjectId("56426ebca4e4c4604c3cd103"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "Choque do trovão",
    "Ataque01",
    "Ataque02"
  ]
}
Fetched 4 record(s) in 6ms

```


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
mjunior(mongod-3.0.7) be-mean-instagram> mod = { $push:{moves:'desvio'}}
{
  "$push": {
    "moves": "desvio"
  }
}
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.update({},mod,options)
Updated 9 existing record(s) in 2ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})
mjunior(mongod-3.0.7) be-mean-instagram>
```
Listando todos os pokemons atualizados

```
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.find({})
{
  "_id": ObjectId("56426f5aa4e4c4604c3cd104"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "Ataque01",
    "Ataque02",
    "desvio"
  ]
}
{
  "_id": ObjectId("56427048a4e4c4604c3cd107"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d312bf1e03798b5454ff7"),
  "name": "Maurisson",
  "description": "faz nada",
  "type": "estudante",
  "attack": 9000,
  "height": 179,
  "defensee": 100,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d3152f1e03798b5454ff8"),
  "name": "Pokezinho",
  "description": "nem sei o que faz nem existe",
  "type": "inexistente",
  "attack": 500,
  "height": 179,
  "defensee": 100,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d4f9d676c466685bfe5da"),
  "name": "TestmonInexistente",
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d51f1676c466685bfe5db"),
  "name": "NaoExisteMon",
  "active": true,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56426ebca4e4c4604c3cd103"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "Choque do trovão",
    "Ataque01",
    "Ataque02",
    "desvio"
  ]
}
{
  "_id": ObjectId("56426f6ba4e4c4604c3cd105"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "Ataque01",
    "Ataque02",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d6250b5605ebec8fc3151"),
  "name": "Squirtle",
  "active": true,
  "attack": 48,
  "defense": 65,
  "description": "Essa é a descrição do squirtle mas eu nao entendo nada de pokemon",
  "moves": [
    "investida",
    "Ataque01",
    "Ataque02",
    "desvio"
  ]
}
Fetched 9 record(s) in 4ms
mjunior(mongod-3.0.7) be-mean-instagram> 
```


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
mjunior(mongod-3.0.7) be-mean-instagram> var options = {upsert:true}
mjunior(mongod-3.0.7) be-mean-instagram> var mod = {$set:{name: 'AindaNaoExisteMon'},$setOnInsert: {attack:null,defense:null,height:null,description:'Sem maiores informações'}}

mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.update({name:'AindaNaoExisteMon'},mod,options)

Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564d676d676c466685bfe5dc")
})

mjunior(mongod-3.0.7) be-mean-instagram> 

```
Buscando pokemon criado pela ID retornada **ObjectId("564d676d676c466685bfe5dc")**

```

mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.find({_id:ObjectId("564d676d676c466685bfe5dc")})
{
  "_id": ObjectId("564d676d676c466685bfe5dc"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 2ms
mjunior(mongod-3.0.7) be-mean-instagram> 
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##


```
mjunior(mongod-3.0.7) be-mean-instagram> var query = {moves: {$all: [/investida/i,/dormir/i]}}
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564d312bf1e03798b5454ff7"),
  "name": "Maurisson",
  "description": "faz nada",
  "type": "estudante",
  "attack": 9000,
  "height": 179,
  "defensee": 100,
  "moves": [
    "investida",
    "desvio",
    "dormir"
  ]
}
{
  "_id": ObjectId("56426f5aa4e4c4604c3cd104"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "Ataque01",
    "Ataque02",
    "desvio",
    "dormir"
  ]
}
Fetched 2 record(s) in 2ms
mjunior(mongod-3.0.7) be-mean-instagram> 

``` 

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
mjunior(mongod-3.0.7) be-mean-instagram> var query = {moves: {$all: [/ataque01/i,/ataque02/i,/dormir/i]}}
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56426f5aa4e4c4604c3cd104"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "Ataque01",
    "Ataque02",
    "desvio",
    "dormir"
  ]
}
Fetched 1 record(s) in 1ms
mjunior(mongod-3.0.7) be-mean-instagram> 
```


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
mjunior(mongod-3.0.7) be-mean-instagram> var query = {type:{$ne:'elétrico'}}
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56427048a4e4c4604c3cd107"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d312bf1e03798b5454ff7"),
  "name": "Maurisson",
  "description": "faz nada",
  "type": "estudante",
  "attack": 9000,
  "height": 179,
  "defensee": 100,
  "moves": [
    "investida",
    "desvio",
    "dormir"
  ]
}
{
  "_id": ObjectId("564d3152f1e03798b5454ff8"),
  "name": "Pokezinho",
  "description": "nem sei o que faz nem existe",
  "type": "inexistente",
  "attack": 500,
  "height": 179,
  "defensee": 100,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d4f9d676c466685bfe5da"),
  "name": "TestmonInexistente",
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d51f1676c466685bfe5db"),
  "name": "NaoExisteMon",
  "active": true,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56426ebca4e4c4604c3cd103"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "Choque do trovão",
    "Ataque01",
    "Ataque02",
    "Ataque01",
    "Ataque02",
    "desvio"
  ]
}
{
  "_id": ObjectId("56426f6ba4e4c4604c3cd105"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "Ataque01",
    "Ataque02",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d6250b5605ebec8fc3151"),
  "name": "Squirtle",
  "active": true,
  "attack": 48,
  "defense": 65,
  "description": "Essa é a descrição do squirtle mas eu nao entendo nada de pokemon",
  "moves": [
    "investida",
    "Ataque01",
    "Ataque02",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d676d676c466685bfe5dc"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
{
  "_id": ObjectId("56426f5aa4e4c4604c3cd104"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "Ataque01",
    "Ataque02",
    "desvio",
    "dormir"
  ]
}
Fetched 10 record(s) in 2ms
mjunior(mongod-3.0.7) be-mean-instagram> 

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
mjunior(mongod-3.0.7) be-mean-instagram> var query = {$and: [  {moves:{$in:[/investida/i]}}  ,   {defense:{$lte:49}}] }
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56427048a4e4c4604c3cd107"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms
mjunior(mongod-3.0.7) be-mean-instagram> 

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
mjunior(mongod-3.0.7) be-mean-instagram> var query = {$and: [{type:'agua'},  {attack:{$lt:50}}]}
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.remove(query)
Removed 0 record(s) in 2ms
WriteResult({
  "nRemoved": 0
})
mjunior(mongod-3.0.7) be-mean-instagram> 

```
