# MongoDB - Aula 04 - Exercício
autor: Denner Evaldt Machado

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
// Alterei por raichu um dos pokemons, que tenho cadastrado, para adicionar os ataques

> var query = { $or: [{name: /raichu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}
> var mod = { $pushAll: { moves: ['pular','voar']}};
> var options = {multi: true}
> db.pokemons.update(query, mod, options)

WriteResult({ 
	"nMatched" : 1, 
	"nUpserted" : 0, 
	"nModified" : 1 
})

> db.pokemons.find()
{ "_id" : ObjectId("56427c825978a2317b17a1df"), "name" : "Metapod", "description" : "Baguio loco de pedra e ferro", "type" : "Bug", "attack" : 10, "height" : 0.7 }
{ "_id" : ObjectId("56427d5e5978a2317b17a1e0"), "name" : "Butterfree", "description" : "Borboleta colorida bonitinha", "type" : "Butterfly", "attack" : 20, "height" : 1.1 }
{ "_id" : ObjectId("564281df5978a2317b17a1e1"), "name" : "Charizard", "description" : "Fogo na bomba", "type" : "Fire", "attack" : 40, "height" : 1.7 }
{ "_id" : ObjectId("5642827c5978a2317b17a1e2"), "name" : "Rattata", "description" : "Ratinho louco", "type" : "Normal", "attack" : 30, "height" : 0.3 }
{ "_id" : ObjectId("564283105978a2317b17a1e3"), "name" : "Raichu", "description" : "Pokemon elétrico parecido com pikachu", "type" : "electric", "attack" : 50, "height" : 0.8, "moves" : [ "pular", "voar" ] }

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
> var query = {}
> var mod = {$push: {moves:'desvio'}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)

WriteResult({ 
	"nMatched" : 5, 
	"nUpserted" : 0, 
	"nModified" : 5 
})

> db.pokemons.find()
{ "_id" : ObjectId("56427c825978a2317b17a1df"), "name" : "Metapod", "description" : "Baguio loco de pedra e ferro", "type" : "Bug", "attack" : 10, "height" : 0.7, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("56427d5e5978a2317b17a1e0"), "name" : "Butterfree", "description" : "Borboleta colorida bonitinha", "type" : "Butterfly", "attack" : 20, "height" : 1.1, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564281df5978a2317b17a1e1"), "name" : "Charizard", "description" : "Fogo na bomba", "type" : "Fire", "attack" : 40, "height" : 1.7, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5642827c5978a2317b17a1e2"), "name" : "Rattata", "description" : "Ratinho louco", "type" : "Normal", "attack" : 30, "height" : 0.3, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564283105978a2317b17a1e3"), "name" : "Raichu", "description" : "Pokemon elétrico parecido com pikachu", "type" : "electric", "attack" : 50, "height" : 0.8, "moves" : [ "pular", "voar", "desvio" ] }

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
> var query = {name: /AindaNaoExisteMon/i}
> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', description: 'Sem maiores informações', type: null, attack: null, height: null, moves: []}}
> var options = {upsert: true}
> db.pokemons.update(query, mod, options)

WriteResult({
	"nMatched" : 0,
	"nUpserted" : 1,
	"nModified" : 0,
	"_id" : ObjectId("564cb567e6697393b00232ee")
})

> db.pokemons.find()
{ "_id" : ObjectId("56427c825978a2317b17a1df"), "name" : "Metapod", "description" : "Baguio loco de pedra e ferro", "type" : "Bug", "attack" : 10, "height" : 0.7, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("56427d5e5978a2317b17a1e0"), "name" : "Butterfree", "description" : "Borboleta colorida bonitinha", "type" : "Butterfly", "attack" : 20, "height" : 1.1, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564281df5978a2317b17a1e1"), "name" : "Charizard", "description" : "Fogo na bomba", "type" : "Fire", "attack" : 40, "height" : 1.7, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5642827c5978a2317b17a1e2"), "name" : "Rattata", "description" : "Ratinho louco", "type" : "Normal", "attack" : 30, "height" : 0.3, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564283105978a2317b17a1e3"), "name" : "Raichu", "description" : "Pokemon elétrico parecido com pikachu", "type" : "electric", "attack" : 50, "height" : 0.8, "moves" : [ "pular", "voar", "desvio" ] }
{ "_id" : ObjectId("564cb567e6697393b00232ee"), "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "type" : null, "attack" : null, "height" : null, "moves" : [ ] }

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
> var query = {moves: {$in: ['investida', 'pular']}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564283105978a2317b17a1e3"), "name" : "Raichu", "description" : "Pokemon elétrico parecido com pikachu", "type" : "electric", "attack" : 50, "height" : 0.8, "moves" : [ "pular", "voar", "desvio" ] }

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
> var query = {moves: {$in: [/desvio/i]}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56427c825978a2317b17a1df"), "name" : "Metapod", "description" : "Baguio loco de pedra e ferro", "type" : "Bug", "attack" : 10, "height" : 0.7, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("56427d5e5978a2317b17a1e0"), "name" : "Butterfree", "description" : "Borboleta colorida bonitinha", "type" : "Butterfly", "attack" : 20, "height" : 1.1, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564281df5978a2317b17a1e1"), "name" : "Charizard", "description" : "Fogo na bomba", "type" : "Fire", "attack" : 40, "height" : 1.7, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5642827c5978a2317b17a1e2"), "name" : "Rattata", "description" : "Ratinho louco", "type" : "Normal", "attack" : 30, "height" : 0.3, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564283105978a2317b17a1e3"), "name" : "Raichu", "description" : "Pokemon elétrico parecido com pikachu", "type" : "electric", "attack" : 50, "height" : 0.8, "moves" : [ "pular", "voar", "desvio" ] }

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
> var query = {type: { $ne: "electric"}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56427c825978a2317b17a1df"), "name" : "Metapod", "description" : "Baguio loco de pedra e ferro", "type" : "Bug", "attack" : 10, "height" : 0.7, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("56427d5e5978a2317b17a1e0"), "name" : "Butterfree", "description" : "Borboleta colorida bonitinha", "type" : "Butterfly", "attack" : 20, "height" : 1.1, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564281df5978a2317b17a1e1"), "name" : "Charizard", "description" : "Fogo na bomba", "type" : "Fire", "attack" : 40, "height" : 1.7, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5642827c5978a2317b17a1e2"), "name" : "Rattata", "description" : "Ratinho louco", "type" : "Normal", "attack" : 30, "height" : 0.3, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564cb567e6697393b00232ee"), "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "type" : null, "attack" : null, "height" : null, "moves" : [ ] }

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
// Alterei para ao invés de defesa (que não tenho cadastrado nos pokemons) usar o ataque (attack)
// Alterei para ao invés de investida (que não tenho cadastrado nos pokemons) usar o desvio

> var query = {$and: [{moves: {$in: [/desvio/i]}}, {attack: {$not: {$lte: 49} } }]}
> db.pokemons.find(query)
{ "_id" : ObjectId("564283105978a2317b17a1e3"), "name" : "Raichu", "description" : "Pokemon elétrico parecido com pikachu", "type" : "electric", "attack" : 50, "height" : 0.8, "moves" : [ "pular", "voar", "desvio" ] }

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
> var query = {$and: [{type: 'água'}, {attack: {$lt: 50}}]}
> db.pokemons.remove(query)
WriteResult({ 
	"nRemoved" : 0 
})

```
