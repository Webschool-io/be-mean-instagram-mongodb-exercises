# MongoDB - Aula 04 - Exercício
autor: Cristiano Mesquita

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander

ubuntu(mongod-2.6.10) be-mean-instagram> var query = ({$or:[{name:'Pikachu'},{name:'Charmander'},{name:'Squirtle'},{name:'Bulbassauro'}]})

var mod = ({$pushAll:{moves:['bomba netuno','came came ha']}})

var options = ({multi:1})

ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 432ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("574a708651f10f8cd6c8d5b9"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "bomba netuno",
    "came came ha"
  ]
}
{
  "_id": ObjectId("574a714151f10f8cd6c8d5bb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "àgua",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "Hidro bomba",
    "bomba netuno",
    "came came ha"
  ]
}
{
  "_id": ObjectId("574a6ff751f10f8cd6c8d5b8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "choque do trovão",
    "investida",
    "bomba netuno",
    "came came ha"
  ]
}
{
  "_id": ObjectId("574a70f251f10f8cd6c8d5ba"),
  "name": "Charmander",
  "description": "Esse é o cão cupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "bomba netuno",
    "came came ha"
  ]
}
Fetched 4 record(s) in 2ms


## Adicionar 1 movimento em todos os pokemons 'Desvio'

ubuntu(mongod-2.6.10) be-mean-instagram> var query = ({});
ubuntu(mongod-2.6.10) be-mean-instagram> var mod = ({$pushAll:{moves:['Desvio']}});

ubuntu(mongod-2.6.10) be-mean-instagram> var options = ({multi:1})
ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.update(query,mod,options);
Updated 6 existing record(s) in 5ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})
ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query);
{
  "_id": ObjectId("574d937fee95c1d9e100241f"),
  "description": "pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a6ff751f10f8cd6c8d5b8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "choque do trovão",
    "investida",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574dfbe75891ad6d852a6334"),
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a70f251f10f8cd6c8d5ba"),
  "name": "Charmander",
  "description": "Esse é o cão cupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a708651f10f8cd6c8d5b9"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a714151f10f8cd6c8d5bb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "àgua",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "Hidro bomba",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
Fetched 6 record(s) in 113ms


## Adicionar o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição 'Sem maiores informações.

ubuntu(mongod-2.6.10) be-mean-instagram> var query = ({name:'AindaNaoExistemMon'});
ubuntu(mongod-2.6.10) be-mean-instagram> var mod = ({$set:{description:'Sem maiores informações'},$setOnInsert:{name:'AindaNaoExisteMon',attack:null,defense:null,height:null}})
ubuntu(mongod-2.6.10) be-mean-instagram> var options = ({upsert:1})
ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 124ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5750e6e85891ad6d852b2954")
})
ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.find({"_id": ObjectId("5750e6e85891ad6d852b2954")})
{
  "_id": ObjectId("5750e6e85891ad6d852b2954"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "attack": null,
  "defense": null,
  "height": null
}
Fetched 1 record(s) in 16ms


## Pesquisar todos os pokemons que possuam ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.

ubuntu(mongod-2.6.10) be-mean-instagram> var query = {moves:{$in:[/investida/i,/came came ha/i]}}
ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("574d937fee95c1d9e100241f"),
  "description": "pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a6ff751f10f8cd6c8d5b8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "choque do trovão",
    "investida",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574dfbe75891ad6d852a6334"),
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a70f251f10f8cd6c8d5ba"),
  "name": "Charmander",
  "description": "Esse é o cão cupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a708651f10f8cd6c8d5b9"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a714151f10f8cd6c8d5bb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "àgua",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "Hidro bomba",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
Fetched 6 record(s) in 2ms

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

ubuntu(mongod-2.6.10) be-mean-instagram> var query = {moves:{$all:[/came came ha/i,/bomba netuno/i]}}
ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("574a6ff751f10f8cd6c8d5b8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "choque do trovão",
    "investida",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a70f251f10f8cd6c8d5ba"),
  "name": "Charmander",
  "description": "Esse é o cão cupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a708651f10f8cd6c8d5b9"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a714151f10f8cd6c8d5bb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "àgua",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "Hidro bomba",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
Fetched 4 record(s) in 46ms

## Pesquisar todos os pokemons que não são do tipo elétrico.

ubuntu(mongod-2.6.10) be-mean-instagram> var query = {type:{$ne:'eletric'}}
ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("574d937fee95c1d9e100241f"),
  "description": "pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574dfbe75891ad6d852a6334"),
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a70f251f10f8cd6c8d5ba"),
  "name": "Charmander",
  "description": "Esse é o cão cupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a708651f10f8cd6c8d5b9"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a714151f10f8cd6c8d5bb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "Hidro bomba",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5750e6e85891ad6d852b2954"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "attack": null,
  "defense": null,
  "height": null
}
Fetched 6 record(s) in 3ms

## Pesquisar todos os pokemons que tenham o ataque 'investida' E tenham defesa não menor ou igual a 49.

ubuntu(mongod-2.6.10) be-mean-instagram> var query = {$and:[{moves:{$in:['investida']}},{attack:{$not:{$lte:49}}}]}

ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("574d937fee95c1d9e100241f"),
  "description": "pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a6ff751f10f8cd6c8d5b8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "choque do trovão",
    "investida",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574dfbe75891ad6d852a6334"),
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("574a70f251f10f8cd6c8d5ba"),
  "name": "Charmander",
  "description": "Esse é o cão cupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
Fetched 4 record(s) in 1ms

## Remova todos os pokemons do tipo água e com attack menor que 50.

ubuntu(mongod-2.6.10) be-mean-instagram> var query = {$and:[{type:/água/i},{attack:{$lt:50}}]}
ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("574a714151f10f8cd6c8d5bb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "Hidro bomba",
    "bomba netuno",
    "came came ha",
    "Desvio"
  ]
}
Fetched 1 record(s) in 1ms
ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 31ms
WriteResult({
  "nRemoved": 1
})

ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query)
Fetched 0 record(s) in 1ms


## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício, demostre qual a diferença entre operadores '$ne' e '$not'

A diferença é que o $not aceita Regex e o $ne não aceita, além de o $not ser o não lógico enquanto o $ne seria um diferente != e $not a negação !






