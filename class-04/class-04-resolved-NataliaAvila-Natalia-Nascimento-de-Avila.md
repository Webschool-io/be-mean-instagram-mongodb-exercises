# MongoDB - Aula 04 - Exercício
autor: Natália Nascimento de Ávila


#1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var poke = { $or: [ {name: /Pikachu/i}, {name: /Squirtle/i}, {name: /Bulbassauro/i}, {name: /Charmander/i} ]}

var mod = {$pushAll:{moves:['choque mega eletrico', 'investida do trovao']}}

var options = {multi:true}

db.pokemons.update(poke,mod,options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })

db.pokemons.find(poke)
{ "_id" : ObjectId("5723b2035b4bfa76504b144c"), "name" : "Squirtle", "description" : "tartaruguinha bonitinha", "type" :
 "agua", "attack" : 50, "defense" : 60, "height" : 0.5, "moves" : [ "choque mega eletrico", "investida do trovao" ] }

{ "_id" : ObjectId("5723b2035b4bfa76504b144d"), "name" : "Bulbassauro", "description" : "olhar sarcastico carrega coisa
nas costas", "type" : "grass", "attack" : 60, "defense" : 50, "height" : 0.7, "moves" : [ "choque mega eletrico", "inves
tida do trovao" ] }

{ "_id" : ObjectId("5723b7de5b4bfa76504b1454"), "name" : "Charmander", "description" : "solta fogo pelo rabo", "type" :
"fire", "attack" : 60, "defense" : 40, "height" : 0.6, "moves" : [ "choque mega eletrico", "investida do trovao" ] }

{ "_id" : ObjectId("57279b626c3282c03b4bf6e4"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type"
: "eletric", "attack" : 55, "defense" : 40, "height" : 0.4, "moves" : [ "choque mega eletrico", "investida do trovao" ]

```

#2. Adicionar 1 movimento em todos os pokemons: desvio.

```
var mod = {$push:{moves:'desvio'}}

var options = {multi:true}

db.pokemons.update(poke,mod,options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })

{ "_id" : ObjectId("5723b2035b4bfa76504b144c"), "name" : "Squirtle", "description" : "tartaruguinha bonitinha", "type" :  "agua", "attack" : 50, "defense" : 60, "height" : 0.5, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

{ "_id" : ObjectId("5723b2035b4bfa76504b144d"), "name" : "Bulbassauro", "description" : "olhar sarcastico carrega coisa nas costas", "type" : "grass", "attack" : 60, "defense" : 50, "height" : 0.7, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

{ "_id" : ObjectId("5723b7de5b4bfa76504b1454"), "name" : "Charmander", "description" : "solta fogo pelo rabo", "type" : "fire", "attack" : 60, "defense" : 40, "height" : 0.6, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

{ "_id" : ObjectId("57279ae26c3282c03b4bf6e3"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type": "eletric", "attack" : 55, "defense" : 40, "height" : 0.4, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }


```

#3. Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
var poke = {name:/AindaNaoExisteMon/i}

var mod = {$set:{active:true}, $setOnInsert:{name :null, attack: null, defense: null, height: null, description: 'Sem maiores informações'}}

var options = {upsert:true}

db.pokemons.update(poke,mod,options)
WriteResult({
        "nMatched" : 0,
        
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("5727a47aeefb878bc87dbd93")
})

```

#4. Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```
var poke = {moves:{$in: ['investida do trovao', 'choque mega eletrico']}}

db.pokemons.find(poke)
{ "_id" : ObjectId("5723b2035b4bfa76504b144c"), "name" : "Squirtle", "description" : "tartaruguinha bonitinha", "type" : "agua", "attack" : 50, "defense" : 60, "height" : 0.5, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

{ "_id" : ObjectId("5723b2035b4bfa76504b144d"), "name" : "Bulbassauro", "description" : "olhar sarcastico carrega coisa nas costas", "type" : "grass", "attack" : 60, "defense" : 50, "height" : 0.7, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

{ "_id" : ObjectId("5723b7de5b4bfa76504b1454"), "name" : "Charmander", "description" : "solta fogo pelo rabo", "type" :"fire", "attack" : 60, "defense" : 40, "height" : 0.6, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

{ "_id" : ObjectId("57279ae26c3282c03b4bf6e3"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type": "eletric", "attack" : 55, "defense" : 40, "height" : 0.4, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }


```

#5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
var poke = {moves:{$in: ['choque mega eletrico']}}

db.pokemons.find(poke)
{ "_id" : ObjectId("5723b2035b4bfa76504b144c"), "name" : "Squirtle", "description" : "tartaruguinha bonitinha", "type" : "agua", "attack" : 50, "defense" : 60, "height" : 0.5, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

{ "_id" : ObjectId("5723b2035b4bfa76504b144d"), "name" : "Bulbassauro", "description" : "olhar sarcastico carrega coisa nas costas", "type" : "grass", "attack" : 60, "defense" : 50, "height" : 0.7, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

{ "_id" : ObjectId("5723b7de5b4bfa76504b1454"), "name" : "Charmander", "description" : "solta fogo pelo rabo", "type" :"fire", "attack" : 60, "defense" : 40, "height" : 0.6, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

{ "_id" : ObjectId("57279ae26c3282c03b4bf6e3"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type": "eletric", "attack" : 55, "defense" : 40, "height" : 0.4, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

```

#6. Pesquisar todos os pokemons que não são do tipo elétrico.

```
var poke = {type:{$ne: ['eletric']}}

db.pokemons.find(poke)
{ "_id" : ObjectId("570cfc63887690aa1846c4d6"), "name" : "Wartortle", "description" : "Turtle Pokemon", "type" : "água", "attack" : 63, "defense" : 80, "height" : 0.9 }

{ "_id" : ObjectId("570cfc64887690aa1846c4d7"), "name" : "Beedrill", "description" : "Esse é venenoso", "type" : "buge poison", "attack" : 150, "defense" : 40, "height" : 1.4 }

{ "_id" : ObjectId("570cfc64887690aa1846c4d8"), "name" : "Venusaur", "description" : "esse é calminho", "type" : "grasse poison", "attack" : 82, "defense" : 83, "height" : 2 }

{ "_id" : ObjectId("570cfc64887690aa1846c4d9"), "name" : "Jigglypuff", "description" : "canta para deixar os inimigos lentos", "type" : "normal e fairy", "attack" : 45, "defense" : 20, "height" : 0.5 }

{ "_id" : ObjectId("570cfc64887690aa1846c4da"), "name" : "Butterfree", "description" : "transporta mel e flores em longa distancia", "type" : "bug e flying", "attack" : 45, "defense" : 50, "height" : 1 }

{ "_id" : ObjectId("570cfc88887690aa1846c4dd"), "name" : "Venusaur", "description" : "esse é calminho", "type" : "grasse poison", "attack" : 82, "defense" : 83, "height" : 2 }

{ "_id" : ObjectId("570cfc8f887690aa1846c4de"), "name" : "Jigglypuff", "description" : "canta para deixar os inimigos lentos", "type" : "normal e fairy", "attack" : 45, "defense" : 20, "height" : 0.5 }

{ "_id" : ObjectId("570cfc94887690aa1846c4df"), "name" : "Butterfree", "description" : "transporta mel e flores em longa distancia", "type" : "bug e flying", "attack" : 45, "defense" : 50, "height" : 1 }

{ "_id" : ObjectId("570d013e887690aa1846c4e1"), "name" : "Chespin", "description" : "mega proteção na cabeça e costas","type" : "grass", "attack" : 3, "defense" : 3, "height" : 0.4 }

{ "_id" : ObjectId("570d013e887690aa1846c4e2"), "name" : "Fennekin", "description" : "curte fogo e odeia agua", "type" : "fire", "attack" : 2, "defense" : 2, "height" : 0.4 }

{ "_id" : ObjectId("570d013e887690aa1846c4e3"), "name" : "Froakie", "description" : "é um sapinho que curte agua", "type" : "fire", "attack" : 30, "defense" : 20, "height" : 0.3 }

{ "_id" : ObjectId("570d013e887690aa1846c4e4"), "name" : "Binacle", "description" : "pedra aquatica de duas cabeças", "type" : "rock", "attack" : 50, "defense" : 50, "height" : 0.5 }

{ "_id" : ObjectId("5723b2035b4bfa76504b144c"), "name" : "Squirtle", "description" : "tartaruguinha bonitinha", "type" : "agua", "attack" : 50, "defense" : 60, "height" : 0.5, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

{ "_id" : ObjectId("5723b2035b4bfa76504b144d"), "name" : "Bulbassauro", "description" : "olhar sarcastico carrega coisa nas costas", "type" : "grass", "attack" : 60, "defense" : 50, "height" : 0.7, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

```

#7. Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

```
var poke = {$and: [{moves:{$in:['investida do trovao']},defense:{$not:{$lte: 49}}}]}

db.pokemons.find(poke)
{ "_id" : ObjectId("5723b2035b4bfa76504b144c"), "name" : "Squirtle", "description" : "tartaruguinha bonitinha", "type" : "agua", "attack" : 50, "defense" : 60, "height" : 0.5, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }
{ "_id" : ObjectId("5723b2035b4bfa76504b144d"), "name" : "Bulbassauro", "description" : "olhar sarcastico carrega coisanas costas", "type" : "grass", "attack" : 60, "defense" : 50, "height" : 0.7, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }


```

#8. Remova todos os pokemons do tipo água e com attack menor que 50.

```

var poke = {$and: [{type:{$in:['agua']},attack:{$lt: 100}}]}

db.pokemons.remove(poke)
WriteResult({ "nRemoved" : 1 })

db.pokemons.find(poke)
{ "_id" : ObjectId("570cfc64887690aa1846c4d7"), "name" : "Beedrill", "description" : "Esse é venenoso", "type" : "buge poison", "attack" : 150, "defense" : 40, "height" : 1.4 }

{ "_id" : ObjectId("570cfc64887690aa1846c4d8"), "name" : "Venusaur", "description" : "esse é calminho", "type" : "grasse poison", "attack" : 82, "defense" : 83, "height" : 2 }

{ "_id" : ObjectId("570cfc64887690aa1846c4d9"), "name" : "Jigglypuff", "description" : "canta para deixar os inimigos lentos", "type" : "normal e fairy", "attack" : 45, "defense" : 20, "height" : 0.5 }

{ "_id" : ObjectId("570cfc64887690aa1846c4da"), "name" : "Butterfree", "description" : "transporta mel e flores em longa distancia", "type" : "bug e flying", "attack" : 45, "defense" : 50, "height" : 1 }

{ "_id" : ObjectId("570cfc8f887690aa1846c4de"), "name" : "Jigglypuff", "description" : "canta para deixar os inimigos lentos", "type" : "normal e fairy", "attack" : 45, "defense" : 20, "height" : 0.5 }

{ "_id" : ObjectId("570d013e887690aa1846c4e1"), "name" : "Chespin", "description" : "mega proteção na cabeça e costas","type" : "grass", "attack" : 3, "defense" : 3, "height" : 0.4 }

{ "_id" : ObjectId("570d013e887690aa1846c4e2"), "name" : "Fennekin", "description" : "curte fogo e odeia agua", "type" : "fire", "attack" : 2, "defense" : 2, "height" : 0.4 }

{ "_id" : ObjectId("570d013e887690aa1846c4e3"), "name" : "Froakie", "description" : "é um sapinho que curte agua", "type" : "fire", "attack" : 30, "defense" : 20, "height" : 0.3 }

{ "_id" : ObjectId("570d013e887690aa1846c4e4"), "name" : "Binacle", "description" : "pedra aquatica de duas cabeças", "type" : "rock", "attack" : 50, "defense" : 50, "height" : 0.5 }

{ "_id" : ObjectId("5723b2035b4bfa76504b144d"), "name" : "Bulbassauro", "description" : "olhar sarcastico carrega coisa nas costas", "type" : "grass", "attack" : 60, "defense" : 50, "height" : 0.7, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

{ "_id" : ObjectId("5723b7de5b4bfa76504b1454"), "name" : "Charmander", "description" : "solta fogo pelo rabo", "type" :"fire", "attack" : 60, "defense" : 40, "height" : 0.6, "moves" : [ "choque mega eletrico", "investida do trovao", "desvio" ] }

```