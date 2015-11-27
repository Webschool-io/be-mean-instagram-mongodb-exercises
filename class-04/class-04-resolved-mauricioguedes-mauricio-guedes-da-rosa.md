# MongoDB - Aula 04/05 - Exercício
autor: Maurício Guedes

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Bulbasaur, Charmeleon, Charizard e Metapod.
```
var query = {$or: [{name: /bulbasaur/i}, {name: /charmeleon/i}, {name: /charizard/i}, {name: /metapod/i}]}
var mod = {$pushAll: {moves: ['ataque de fogo', 'ataque de agua']}}
var opt = {multi: true}
db.pokemons.update(query, mod, opt)
db.pokemons.find(query)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
db.pokemons.find(query)
{ "_id" : ObjectId("5643c6c703acdc55ec079516"), "name" : "Bulbasaur", "description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", "attack" : 49, "defense" : 49, "height" : 7, "moves" : [ "ataque de fogo", "ataque de agua" ] }
{ "_id" : ObjectId("5643c6d103acdc55ec079517"), "name" : "Metapod", "description" : "The shell covering this Pokmon's body is as hard as an iron slab. Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.", "attack" : 20, "defense" : 55, "height" : 7, "moves" : [ "ataque de fogo", "ataque de agua" ] }
{ "_id" : ObjectId("5643c6e503acdc55ec079519"), "name" : "Charmeleon", "description" : "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.", "attack" : 64, "defense" : 58, "height" : 11, "moves" : [ "ataque de fogo", "ataque de agua" ] }
{ "_id" : ObjectId("5643c6ec03acdc55ec07951a"), "name" : "Charizard", "description" : "Charizard é o bixão", "attack" : 84, "defense" : 78, "height" : 17, "moves" : [ "ataque de fogo", "ataque de agua" ] }
```

## Adicionar 1 movimento em todos os pokemons: desvio.
```
var mod = {$push: {moves: 'desvio'}}
var opt = {multi: true}
db.pokemons.update({}, mod, opt)
WriteResult({ "nMatched" : 7, "nUpserted" : 0, "nModified" : 7 })
db.pokemons.find()
{ "_id" : ObjectId("5643c6c703acdc55ec079516"), "name" : "Bulbasaur", "description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", "attack" : 49, "defense" : 49, "height" : 7, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5643c6d103acdc55ec079517"), "name" : "Metapod", "description" : "The shell covering this Pokmon's body is as hard as an iron slab. Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.", "attack" : 20, "defense" : 55, "height" : 7, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5643c6d803acdc55ec079518"), "name" : "Ivysaur", "description" : "There is a bud on this Pokmon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.", "attack" : 62, "defense" : 63, "height" : 10, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643c6e503acdc55ec079519"), "name" : "Charmeleon", "description" : "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.", "attack" : 64, "defense" : 58, "height" : 11, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5643c6ec03acdc55ec07951a"), "name" : "Charizard", "description" : "Charizard é o bixão", "attack" : 84, "defense" : 78, "height" : 17, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5646231ba485bd420f9e58fc"), "name" : "Mauricio", "description" : " o bixo", "attack" : 84, "defense" : 78, "height" : 0.2, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("56462cf30f4ef44513a3ebf6"), "name" : "Mauricio tipo Grama", "description" : "o bixo da grama", "attack" : 84, "defense" : 78, "height" : 0.2, "type" : "grama", "moves" : [ "desvio" ] }
```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
```
> query
{ "name" : /AindaNaoExisteMon/i }
> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', "description" : null, "  var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', "description" : null, "type" : null, "attack" : null, "height" : null, "defense" : null}, }
> mod
{
        "$setOnInsert" : {
                "name" : "AindaNaoExisteMon",
                "description" : null,
                "type" : null,
                "attack" : null,
                "height" : null,
                "defense" : null
        }
}
var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', "description" : 'Sem maiores informações', "type" : null, "attack" : null, "height" : null, "defense" : null}, }
var opt = {upsert: true}
db.pokemons.update(query, mod, opt)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("56533b37f951d89b1c2daeab")
})
db.pokemons.find(query)
{ "_id" : ObjectId("56533b37f951d89b1c2daeab"), "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "type" : null, "attack" : null, "height" : null, "defense" : null }
```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
```
var query = {moves: {$in: [/ataque de agua/i, /investida/i]}}
db.pokemons.find(query)
{ "_id" : ObjectId("5643c6c703acdc55ec079516"), "name" : "Bulbasaur", "description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", "attack" : 49, "defense" : 49, "height" : 7, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5643c6d103acdc55ec079517"), "name" : "Metapod", "description" : "The shell covering this Pokmon's body is as hard as an iron slab. Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.", "attack" : 20, "defense" : 55, "height" : 7, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5643c6e503acdc55ec079519"), "name" : "Charmeleon", "description" : "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.", "attack" : 64, "defense" : 58, "height" : 11, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5643c6ec03acdc55ec07951a"), "name" : "Charizard", "description" : "Charizard é o bixão", "attack" : 84, "defense" : 78, "height" : 17, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
var query = {moves: {$in: [/ataque de fogo/i, /ataque de agua/i, /desvio/i]}}
db.pokemons.find(query)
{ "_id" : ObjectId("5643c6c703acdc55ec079516"), "name" : "Bulbasaur", "description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", "attack" : 49, "defense" : 49, "height" : 7, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5643c6d103acdc55ec079517"), "name" : "Metapod", "description" : "The shell covering this Pokmon's body is as hard as an iron slab. Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.", "attack" : 20, "defense" : 55, "height" : 7, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5643c6d803acdc55ec079518"), "name" : "Ivysaur", "description" : "There is a bud on this Pokmon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.", "attack" : 62, "defense" : 63, "height" : 10, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643c6e503acdc55ec079519"), "name" : "Charmeleon", "description" : "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.", "attack" : 64, "defense" : 58, "height" : 11, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5643c6ec03acdc55ec07951a"), "name" : "Charizard", "description" : "Charizard é o bixão", "attack" : 84, "defense" : 78, "height" : 17, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5646231ba485bd420f9e58fc"), "name" : "Mauricio", "description" : " o bixo", "attack" : 84, "defense" : 78, "height" : 0.2, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("56462cf30f4ef44513a3ebf6"), "name" : "Mauricio tipo Grama", "description" : "o bixo da grama", "attack" : 84, "defense" : 78, "height" : 0.2, "type" : "grama", "moves" : [ "desvio" ] }
```

## Pesquisar todos os pokemons que não são do tipo elétrico.
```
var query = {type: {$ne: 'eltrico'}}
db.pokemons.find(query)
{ "_id" : ObjectId("5643c6c703acdc55ec079516"), "name" : "Bulbasaur", "description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", "attack" : 49, "defense" : 49, "height" : 7, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5643c6d103acdc55ec079517"), "name" : "Metapod", "description" : "The shell covering this Pokmon's body is as hard as an iron slab. Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.", "attack" : 20, "defense" : 55, "height" : 7, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5643c6d803acdc55ec079518"), "name" : "Ivysaur", "description" : "There is a bud on this Pokmon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.", "attack" : 62, "defense" : 63, "height" : 10, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643c6e503acdc55ec079519"), "name" : "Charmeleon", "description" : "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.", "attack" : 64, "defense" : 58, "height" : 11, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5643c6ec03acdc55ec07951a"), "name" : "Charizard", "description" : "Charizard é o bixão", "attack" : 84, "defense" : 78, "height" : 17, "moves" : [ "ataque de fogo", "ataque de agua", "desvio" ] }
{ "_id" : ObjectId("5646231ba485bd420f9e58fc"), "name" : "Mauricio", "description" : " o bixo", "attack" : 84, "defense" : 78, "height" : 0.2, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("56462cf30f4ef44513a3ebf6"), "name" : "Mauricio tipo Grama", "description" : "o bixo da grama", "attack" : 84, "defense" : 78, "height" : 0.2, "type" : "grama", "moves" : [ "desvio" ] }
{ "_id" : ObjectId("56533b37f951d89b1c2daeab"), "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "type" : null, "attack" : null, "height" : null, "defense" : null }
```

## Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa menor ou igual a 49.
```
var query = {$and: [{moves: {$in: ['investida']}}, {defense: {lte: 49}}]}
db.pokemons.find(query)
// Nenhum registro encontrado
```

## Remova todos os pokemons do tipo água e com attack menor que 50.
```
var query = {$and: [{type: /gua/i}, {attack: {lt: 50}}]}
db.pokemons.remove(query)
WriteResult({ "nRemoved" : 0 })
```
