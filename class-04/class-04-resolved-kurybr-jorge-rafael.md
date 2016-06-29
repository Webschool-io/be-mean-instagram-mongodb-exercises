# MongoDB - Aula 04 - Exercício
Autor: Jorge Rafael

#### **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

``` Javascript
var query = { $or :
        [
          {name : /pikachu/i}
        , {name : /squirtle/i}
        , {name : /bulbassauro/i}
        , {name : /charmander/i}
        ]
    }
var mod = { $pushAll : { moves : ['Agarrar','Agilidade'] } }
var options = { multi : true }
db.pokemons.update(query,mod,options)

WriteResult({ "nMatched" : 3, "nUpserted" : 0, "nModified" : 3 })

```


#### **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

``` Javascript
var query = {}
var mod = { $pushAll : { moves : ['Desvio'] } }
var options = { multi : true }
db.pokemons.update(query,mod,options)

WriteResult({ "nMatched" : 7, "nUpserted" : 0, "nModified" : 7 })

```

#### **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

``` Javascript

var query = {name: /NaoExisteMon/i }
var mod = {
  $set: {moves: []},
  $setOnInsert: {
    name: "NaoExisteMon",
    attack: null,
    defense: null,
    height: null,
    description: "Sem maiores informações"
  }
}
var options = {upsert: true}
db.pokemons.update(query, mod, options)

WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

```

#### Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

``` Javascript
var query = { moves : { $in : [/investida/i,/agilidade/i]}}
db.pokemons.find(query)

/* 1 */
{
    "_id" : ObjectId("564288cacc052955701cf5b0"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30.0000000000000000,
    "height" : 0.3000000000000000,
    "defense" : 35.0000000000000000,
    "active" : false,
    "moves" : [
        "investida",
        "Desvio"
    ]
}

/* 2 */
{
    "_id" : ObjectId("564c807c83803ec901191c6e"),
    "description" : "Pokemon de teste",
    "name" : "Testemon",
    "attack" : 8000.0000000000000000,
    "defense" : 8000.0000000000000000,
    "active" : false,
    "moves" : [
        "investida",
        "Desvio"
    ]
}

/* 3 */
{
    "_id" : ObjectId("566c39040b5f704108ee6f2a"),
    "active" : false,
    "moves" : [
        "investida",
        "Desvio",
        "Desvio"
    ]
}

/* 4 */
{
    "_id" : ObjectId("564284a8920a9673a775bb0d"),
    "name" : "Pikachu",
    "description" : "Rato elétrico bem fofinho",
    "type" : "electric",
    "attack" : 55.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [
        "investida",
        "choque do trovão",
        "Cauda de aço",
        "Thunderbolt",
        "Agarrar",
        "Agilidade",
        "Desvio"
    ],
    "active" : false
}

/* 5 */
{
    "_id" : ObjectId("564284d1920a9673a775bb0e"),
    "name" : "Bulbassauro",
    "description" : "Chicote de trepadeira",
    "type" : "grama",
    "attack" : 49.0000000000000000,
    "height" : 0.4000000000000000,
    "active" : false,
    "moves" : [
        "investida",
        "folha navalha",
        "Agarrar",
        "Agilidade",
        "Desvio"
    ]
}

/* 6 */
{
    "_id" : ObjectId("56428532920a9673a775bb0f"),
    "name" : "Charmander",
    "description" : "Esse é o cão chupando manga de fofinho",
    "type" : "fogo",
    "attack" : 52.0000000000000000,
    "height" : 0.6000000000000000,
    "active" : false,
    "moves" : [
        "investida",
        "lança-chamas",
        "Agarrar",
        "Agilidade",
        "Desvio"
    ]
}

```

#### Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

``` Javascript
var query = { moves : { $in : [/agarrar/i,/agilidade/i]}}
db.pokemons.find(query)


/* 1 */
{
    "_id" : ObjectId("564284a8920a9673a775bb0d"),
    "name" : "Pikachu",
    "description" : "Rato elétrico bem fofinho",
    "type" : "electric",
    "attack" : 55.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [
        "investida",
        "choque do trovão",
        "Cauda de aço",
        "Thunderbolt",
        "Agarrar",
        "Agilidade",
        "Desvio"
    ],
    "active" : false
}

/* 2 */
{
    "_id" : ObjectId("564284d1920a9673a775bb0e"),
    "name" : "Bulbassauro",
    "description" : "Chicote de trepadeira",
    "type" : "grama",
    "attack" : 49.0000000000000000,
    "height" : 0.4000000000000000,
    "active" : false,
    "moves" : [
        "investida",
        "folha navalha",
        "Agarrar",
        "Agilidade",
        "Desvio"
    ]
}

/* 3 */
{
    "_id" : ObjectId("56428532920a9673a775bb0f"),
    "name" : "Charmander",
    "description" : "Esse é o cão chupando manga de fofinho",
    "type" : "fogo",
    "attack" : 52.0000000000000000,
    "height" : 0.6000000000000000,
    "active" : false,
    "moves" : [
        "investida",
        "lança-chamas",
        "Agarrar",
        "Agilidade",
        "Desvio"
    ]
}
```

#### Pesquisar **todos** os pokemons que não são do tipo `eletric`.##

``` Javascript
var query = { type : { $not : [/eletric/i]}}
//var query = { type : { $nin : [/electric/i]}}
db.pokemons.find(query)

/* 1 */
{
    "_id" : ObjectId("564288cacc052955701cf5b0"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30.0000000000000000,
    "height" : 0.3000000000000000,
    "defense" : 35.0000000000000000,
    "active" : false,
    "moves" : [
        "investida",
        "Desvio"
    ]
}

/* 2 */
{
    "_id" : ObjectId("564c807c83803ec901191c6e"),
    "description" : "Pokemon de teste",
    "name" : "Testemon",
    "attack" : 8000.0000000000000000,
    "defense" : 8000.0000000000000000,
    "active" : false,
    "moves" : [
        "investida",
        "Desvio"
    ]
}

/* 3 */
{
    "_id" : ObjectId("566c39570b5f704108ee6f2b"),
    "active" : false,
    "name" : "NaoExisteMon",
    "attack" : null,
    "defense" : null,
    "height" : null,
    "description" : "Sem maiores informações",
    "moves" : []
}

/* 4 */
{
    "_id" : ObjectId("566c39040b5f704108ee6f2a"),
    "active" : false,
    "moves" : [
        "investida",
        "Desvio",
        "Desvio"
    ]
}

/* 5 */
{
    "_id" : ObjectId("564284d1920a9673a775bb0e"),
    "name" : "Bulbassauro",
    "description" : "Chicote de trepadeira",
    "type" : "grama",
    "attack" : 49.0000000000000000,
    "height" : 0.4000000000000000,
    "active" : false,
    "moves" : [
        "investida",
        "folha navalha",
        "Agarrar",
        "Agilidade",
        "Desvio"
    ]
}

/* 6 */
{
    "_id" : ObjectId("56428532920a9673a775bb0f"),
    "name" : "Charmander",
    "description" : "Esse é o cão chupando manga de fofinho",
    "type" : "fogo",
    "attack" : 52.0000000000000000,
    "height" : 0.6000000000000000,
    "active" : false,
    "moves" : [
        "investida",
        "lança-chamas",
        "Agarrar",
        "Agilidade",
        "Desvio"
    ]
}

```

#### Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

``` Javascript

var query = {$and : [{moves : /investida/i}, {defense : {$not : { $lte : 49 }}}]}
db.pokemons.find(query)


/* 1 */
{
    "_id" : ObjectId("564c807c83803ec901191c6e"),
    "description" : "Pokemon de teste",
    "name" : "Testemon",
    "attack" : 8000.0000000000000000,
    "defense" : 8000.0000000000000000,
    "active" : false,
    "moves" : [
        "investida",
        "Desvio"
    ]
}

/* 2 */
{
    "_id" : ObjectId("566c39040b5f704108ee6f2a"),
    "active" : false,
    "moves" : [
        "investida",
        "Desvio",
        "Desvio"
    ]
}

/* 3 */
{
    "_id" : ObjectId("564284a8920a9673a775bb0d"),
    "name" : "Pikachu",
    "description" : "Rato elétrico bem fofinho",
    "type" : "electric",
    "attack" : 55.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [
        "investida",
        "choque do trovão",
        "Cauda de aço",
        "Thunderbolt",
        "Agarrar",
        "Agilidade",
        "Desvio"
    ],
    "active" : false
}

/* 4 */
{
    "_id" : ObjectId("56428532920a9673a775bb0f"),
    "name" : "Charmander",
    "description" : "Esse é o cão chupando manga de fofinho",
    "type" : "fogo",
    "attack" : 52.0000000000000000,
    "height" : 0.6000000000000000,
    "active" : false,
    "moves" : [
        "investida",
        "lança-chamas",
        "Agarrar",
        "Agilidade",
        "Desvio"
    ]
}
```

#### Remova **todos** os pokemons do tipo grama e com attack menor que 50.

``` Javascript
// Alterei para grama pois já tinha excluido o squirtle
var query = {$and : [{type : /grama/i}, {attack : {$not : { $lte : 50 }}}]}
db.pokemons.remove(query)

WriteResult({ "nRemoved" : 0 })
```
