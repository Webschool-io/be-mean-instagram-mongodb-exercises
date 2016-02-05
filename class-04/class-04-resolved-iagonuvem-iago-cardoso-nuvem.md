# MongoDB - Aula 04 - Exercício
autor: *Iago Nuvem*

## 1 - **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro, Charmander

```js

// Define array com os nomes para modificar
> var query = {name: {$in: [/pikachu/i, /bulbassauro/i , /squirtle/i , /charmander/i ]}}

// Seta os atributos à serem adicionados
> var mod = {$set: {moves: ['movimento 1', 'movimento 2']}}

> var options = {multi: true}

> db.pokemons.update(query,mod,options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
// Exibe os Pokemons alterados
> db.pokemons.find(query)
{ "_id" : ObjectId("564da4e50b47a45b460e4232"), "name" : "Pikachu", "description" : "Rato Elétrico Psicodélico", "type" : "electric", "attack" : 100, "height" : 0.4, "moves" : [ "movimento 1", "movimento 2" ], "active" : false }
{ "_id" : ObjectId("564daf81e9a7daec5650c86a"), "name" : "bulbassauro", "description" : "Chicote de Trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "movimento 1", "movimento 2" ] }
{ "_id" : ObjectId("564dafafe9a7daec5650c86b"), "name" : "Charmander", "description" : "Esse é o cao chupando manga", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "movimento 1", "movimento 2" ] }
{ "_id" : ObjectId("564dafbce9a7daec5650c86c"), "name" : "Squirtle", "description" : "Ejeta fluidos vaginais", "type" : "agua", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "movimento 1", "movimento 2" ] }

```
## 2 - **Adicionar** 1 movimento em todos pokemons:'desvio'.

```js

// Deixa a query vazia pra buscar todos registros
> var query = {}

> var mod = {$push: {moves: 'desvio'}}

> var options = {upsert: true, multi: true}

> db.pokemons.update(query,mod,options)
WriteResult({ "nMatched" : 8, "nUpserted" : 0, "nModified" : 8 })
> db.pokemons.find()
{ "_id" : ObjectId("564da4e50b47a45b460e4232"), "name" : "Pikachu", "description" : "Rato Elétrico Psicodélico", "type" : "electric", "attack" : 100, "height" : 0.4, "moves" : [ "desvio", "desvio" ], "active" : false }
{ "_id" : ObjectId("564daf81e9a7daec5650c86a"), "name" : "bulbassauro", "description" : "Chicote de Trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }
{ "_id" : ObjectId("564dafafe9a7daec5650c86b"), "name" : "Charmander", "description" : "Esse é o cao chupando manga", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }
{ "_id" : ObjectId("564dafbce9a7daec5650c86c"), "name" : "Squirtle", "description" : "Ejeta fluidos vaginais", "type" : "agua", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }
{ "_id" : ObjectId("564db23d77a952f6723bae8f"), "name" : "Caterpie", "description" : "Larva Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("5656dd4fcdf5e5c1b0bc29db"), "description" : "pokemon de teste", "name" : "Testemon", "attack" : 8001, "defense" : 8000, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565827cd9b69b9a594ddecbd"), "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565829069b69b9a594ddecbe"), "active" : false, "name" : "NaoExisteMon", "attack" : null, "defense" : null, "description" : "Sem Info", "moves" : [ "investida", "desvio" ] }
```

## 3 - **Adicionar** o pokemon 'AindaNaoExisteMon' caso ele nao exista, com todos os dados com valor 'null' e a descrição: "Sem maiores informações".

```js

> var query = {name: /AindaNaoExisteMon/i}

// Seta modificador para Alterar o Nome para 'AindaNaoExisteMon' , e caso precise fazer um INSERT os outros dados serão vazios
> var mod = {$set: {name: 'AindaNaoExisteMon'}, $setOnInsert: {name: null, attack: null, defense: null, height: null, description: "Sem maiores informações"}}

> var options = {upsert: true}

> db.pokemons.update(query,mod,options)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("565837dc9b69b9a594ddecbf")
})
> db.pokemons.find(query)
{ "_id" : ObjectId("565837dc9b69b9a594ddecbf"), "name" : "AindaNaoExisteMon" , "attack" : null, "defense" : null, "height" : null , description: "Sem maiores informações"}

```
## 4 - Pesquisar todos os pokemons que possuem o ataque 'Investida' e mais um que voce adicionou, escolha seu pokemon favorito

```js

> var query = {moves: {$in: ['investida', 'movimento 1']}}

> db.pokemons.find(query)
{ "_id" : ObjectId("564daf81e9a7daec5650c86a"), "name" : "bulbassauro", "description" : "Chicote de Trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }
{ "_id" : ObjectId("564dafafe9a7daec5650c86b"), "name" : "Charmander", "description" : "Esse é o cao chupando manga", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }
{ "_id" : ObjectId("564dafbce9a7daec5650c86c"), "name" : "Squirtle", "description" : "Ejeta fluidos vaginais", "type" : "agua", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }
{ "_id" : ObjectId("564db23d77a952f6723bae8f"), "name" : "Caterpie", "description" : "Larva Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("5656dd4fcdf5e5c1b0bc29db"), "description" : "pokemon de teste", "name" : "Testemon", "attack" : 8001, "defense" : 8000, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565827cd9b69b9a594ddecbd"), "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565829069b69b9a594ddecbe"), "active" : false, "name" : "NaoExisteMon", "attack" : null, "defense" : null, "description" : "Sem Info", "moves" : [ "investida", "desvio" ] }

```

## 5 - Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito

```js

> var query = {moves: {$all: ['movimento 1', 'movimento 2']}}

> db.pokemons.find(query)
{ "_id" : ObjectId("564daf81e9a7daec5650c86a"), "name" : "bulbassauro", "description" : "Chicote de Trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }
{ "_id" : ObjectId("564dafafe9a7daec5650c86b"), "name" : "Charmander", "description" : "Esse é o cao chupando manga", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }
{ "_id" : ObjectId("564dafbce9a7daec5650c86c"), "name" : "Squirtle", "description" : "Ejeta fluidos vaginais", "type" : "agua", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }

```
## 6 - Pesquisar **todos** os pokemons que não são do tipo 'elétrico'

```js

> var query = {type: {$ne : 'electric'}}

> db.pokemons.find(query)
{ "_id" : ObjectId("564daf81e9a7daec5650c86a"), "name" : "bulbassauro", "description" : "Chicote de Trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }
{ "_id" : ObjectId("564dafafe9a7daec5650c86b"), "name" : "Charmander", "description" : "Esse é o cao chupando manga", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }
{ "_id" : ObjectId("564dafbce9a7daec5650c86c"), "name" : "Squirtle", "description" : "Ejeta fluidos vaginais", "type" : "agua", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }
{ "_id" : ObjectId("564db23d77a952f6723bae8f"), "name" : "Caterpie", "description" : "Larva Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("5656dd4fcdf5e5c1b0bc29db"), "description" : "pokemon de teste", "name" : "Testemon", "attack" : 8001, "defense" : 8000, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565827cd9b69b9a594ddecbd"), "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565829069b69b9a594ddecbe"), "active" : false, "name" : "NaoExisteMon", "attack" : null, "defense" : null, "description" : "Sem Info", "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565837dc9b69b9a594ddecbf"), "descricao" : "Sem Maiores Informacoes", "name" : null, "attack" : null, "defense" : null, "height" : null }

```
## 7 - Pesquisar **todos** pokemons que tenham ataque 'investida' **E** tenham a defesa **menor ou igual** a 49

```js

> var query = {moves : {$in: ['investida']}, defense : {$lte : 49}}

> db.pokemons.find(query)
{ "_id" : ObjectId("564db23d77a952f6723bae8f"), "name" : "Caterpie", "description" : "Larva Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "desvio" ] }

```

## 8 - Remova **todos** os pokemons do tipo água e com attack menor que 50

```js

> var query = {type: /agua/i}
// Exibindo os pokemons do tipo água , so pra conferir
> db.pokemons.find(query)
{ "_id" : ObjectId("564dafbce9a7daec5650c86c"), "name" : "Squirtle", "description" : "Ejeta fluidos vaginais", "type" : "agua", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "movimento 1", "movimento 2", "desvio" ] }

> var query = {type: /agua/i , defense: {$lt: 50}}
> db.pokemons.remove(query)

// Não foi Removido nenhum, pois não existe nenhum pokemon do tipo agua com o campo 'defense'
WriteResult({ "nRemoved" : 0 })
```