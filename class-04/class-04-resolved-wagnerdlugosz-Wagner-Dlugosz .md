###MongoDB - Aula 04 - Exercício
Autor: Wagner Dlugosz Donato

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
> var attacks = ["Losango aberto","Voadora quantica"]
> var mod = {$pushAll: {moves: attacks}}
> var query = {$or: [{name: "Pikachu"},{name:"Squirtle"},{name:"Bulbassauro"},{name: "Charmander"}]}
> var options = {multi: true}
> var options = {multi: true}

> WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
> var mod = {$push: {moves: "Desvio"}}
> var query = {}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 7, "nUpserted" : 0, "nModified" : 7 })

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
> var query = {name: /AindaNaoExisteMon/i}
> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem maio
res informações", moves: []}}
> var options = {upsert: true}
> db.pokemons.update(query,mod,options)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("56562c505062a96ab7833835")
})

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
> var query = {moves: {$in: ["investida","voadora quantica"]}}

> db.pokemons.find(query)

{ "_id" : ObjectId("5646032932be57bf8e28eca9"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto"
, "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "Desvio" ] }

{ "_id" : ObjectId("5645fda5499ca8b85516ee04"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type"
: "electric", "attack" : 55, "height" : 0.4, "moves" : [ "investida", "choque do trovão", "Losango aberto", "Voadora qua
ntica", "Desvio" ], "active" : false }

{ "_id" : ObjectId("5651cf51e2f71e22052b4a24"), "active" : false, "moves" : [ "investida", "Desvio" ] }

{ "_id" : ObjectId("5651d10ae2f71e22052b4a25"), "active" : false, "moves" : [ "investida", "Desvio" ] }

{ "_id" : ObjectId("5645ff51499ca8b85516ee05"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type"
: "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "Losango aberto",
"Voadora quantica", "Losango aberto", "Voadora quantica", "Losango aberto", "Voadora quantica", "Desvio" ] }

{ "_id" : ObjectId("5645ff51499ca8b85516ee06"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de f
ofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "Los
ango aberto", "Voadora quantica", "Desvio" ] }

{ "_id" : ObjectId("5645ff55499ca8b85516ee07"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe
", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "Losango ab
erto", "Voadora quantica", "Desvio" ] }


```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
> var query = {moves: {$in: ["Losango aberto","Voadora quantica"]}}

> db.pokemons.find(query)

{ "_id" : ObjectId("5645fda5499ca8b85516ee04"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type"
: "electric", "attack" : 55, "height" : 0.4, "moves" : [ "investida", "choque do trovão", "Losango aberto", "Voadora qua
ntica", "Desvio" ], "active" : false }

{ "_id" : ObjectId("5645ff51499ca8b85516ee05"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type"
: "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "Losango aberto",
"Voadora quantica", "Losango aberto", "Voadora quantica", "Losango aberto", "Voadora quantica", "Desvio" ] }

{ "_id" : ObjectId("5645ff51499ca8b85516ee06"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de f
ofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "Los
ango aberto", "Voadora quantica", "Desvio" ] }

{ "_id" : ObjectId("5645ff55499ca8b85516ee07"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe
", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "Losango ab
erto", "Voadora quantica", "Desvio" ] }


```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
> var query = {type: {$ne: "eletric"}}

> db.pokemons.find(query)

{ "_id" : ObjectId("5646032932be57bf8e28eca9"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto"
, "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "Desvio" ] }

{ "_id" : ObjectId("5645fda5499ca8b85516ee04"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type"
: "electric", "attack" : 55, "height" : 0.4, "moves" : [ "investida", "choque do trovão", "Losango aberto", "Voadora qua
ntica", "Desvio" ], "active" : false }

{ "_id" : ObjectId("5651cf51e2f71e22052b4a24"), "active" : false, "moves" : [ "investida", "Desvio" ] }

{ "_id" : ObjectId("5651d10ae2f71e22052b4a25"), "active" : false, "moves" : [ "investida", "Desvio" ] }

{ "_id" : ObjectId("5645ff51499ca8b85516ee05"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type"
: "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "Losango aberto",
"Voadora quantica", "Losango aberto", "Voadora quantica", "Losango aberto", "Voadora quantica", "Desvio" ] }

{ "_id" : ObjectId("5645ff51499ca8b85516ee06"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de f
ofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "Los
ango aberto", "Voadora quantica", "Desvio" ] }

{ "_id" : ObjectId("5645ff55499ca8b85516ee07"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe
", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "Losango ab
erto", "Voadora quantica", "Desvio" ] }

{ "_id" : ObjectId("56562c505062a96ab7833835"), "name" : "AindaNaoExisteMon", "attack" : null, "defense" : null, "height
" : null, "description" : "Sem maiores informações", "moves" : [ ] }


```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
> var query = {$and: [{moves: {$in: ["investida"]}}, {defense: {$not: {$lte: 49}}}]}

> db.pokemons.find(query)

{ "_id" : ObjectId("5645fda5499ca8b85516ee04"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type"
: "electric", "attack" : 55, "height" : 0.4, "moves" : [ "investida", "choque do trovão", "Losango aberto", "Voadora qua
ntica", "Desvio" ], "active" : false }

{ "_id" : ObjectId("5651cf51e2f71e22052b4a24"), "active" : false, "moves" : [ "investida", "Desvio" ] }

{ "_id" : ObjectId("5651d10ae2f71e22052b4a25"), "active" : false, "moves" : [ "investida", "Desvio" ] }

{ "_id" : ObjectId("5645ff51499ca8b85516ee05"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type"
: "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "Losango aberto",
"Voadora quantica", "Losango aberto", "Voadora quantica", "Losango aberto", "Voadora quantica", "Desvio" ] }

{ "_id" : ObjectId("5645ff51499ca8b85516ee06"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de f
ofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "Los
ango aberto", "Voadora quantica", "Desvio" ] }

{ "_id" : ObjectId("5645ff55499ca8b85516ee07"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe
", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "Losango ab
erto", "Voadora quantica", "Desvio" ] }


```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
> var query = {$and: [{"type" : "água"}, {attack: {$lt: 50}}]}

> db.pokemons.remove(query)

WriteResult({ "nRemoved" : 1 })


```


