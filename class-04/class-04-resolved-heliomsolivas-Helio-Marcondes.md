# MongoDb - Aula 04 - Exercício
Autor: Hélio Marcondes

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
    var query = { $or: [{name: /pikachu/i},{name:/squirtle/i},{name: /bulbassauro/i},{name: /charmandar/i}] }
    var mod = {$set:{attack: ['flash','quick attack']}}
    var opt = {multi:true}
    db.pokemons.update(query,mod,opt)
    WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
```

## 2. Adicionar 1 movimento em todos os pokemons: `desvio`

```
    var query = {}
    var mod = {$set:{moves:['desvio']}}
    var options = {multi:true}
    db.pokemons.update(query,mod,options)
    WriteResult({ "nMatched" : 9, "nUpserted" : 0, "nModified" : 9 })
```

## 3. Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```
    var query = {name: 'AindaNaoExisteMon'}
    var mod = {$set:{active:true},$setOnInsert:{name:"AindaNaoExisteMon",attack:null,defense:null,height:null,description:"Sem maiores informações"}}
    var options = {upsert:true}
    db.pokemons.update(query,mod,options)
    WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("56a9538a3c1d0983f9fec101")
    })
```

## 4. Pesquisar todos os pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```
    var query = {attack: {$in:[/investida/i,/flash/i]}}
    db.pokemons.find(query)
    { "_id" : ObjectId("56a7f43c52aa820658a17400"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : [ "flash", "quick attack" ], "height" : 0.4, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a7f45a52aa820658a17401"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : [ "flash", "quick attack" ], "height" : 0.4, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a7f47052aa820658a17402"), "name" : "Charmandar", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : [ "flash", "quick attack" ], "height" : 0.6, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a7f47e52aa820658a17403"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : [ "flash", "quick attack" ], "height" : 0.5, "moves" : [ "desvio" ] }
```

## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
    var query = {attack: {$in:[/flash/i,/quick attack/i]}}
    db.pokemons.find(query)
    { "_id" : ObjectId("56a7f43c52aa820658a17400"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : [ "flash", "quick attack" ], "height" : 0.4, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a7f45a52aa820658a17401"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : [ "flash", "quick attack" ], "height" : 0.4, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a7f47052aa820658a17402"), "name" : "Charmandar", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : [ "flash", "quick attack" ], "height" : 0.6, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a7f47e52aa820658a17403"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : [ "flash", "quick attack" ], "height" : 0.5, "moves" : [ "desvio" ] }
```

## 6. Pesquisar todos que não são do tipo `elétrico`.

```
    var query ={ type: {$ne: 'eletric'}}
    db.pokemons.find(query)
    { "_id" : ObjectId("56a7f3a952aa820658a173fe"), "name" : "Eevee", "description" : "Raposinha bonitinha", "type" : "normal", "attack" : null, "defense" : 20, "height" : 6.5, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a7f40052aa820658a173ff"), "name" : "Umbreon", "description" : "Raposinha bonitinha versão do mau", "type" : "dark", "attack" : null, "defense" : 30, "height" : 27, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a7f45a52aa820658a17401"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : [ "flash", "quick attack" ], "height" : 0.4, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a7f47052aa820658a17402"), "name" : "Charmandar", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : [ "flash", "quick attack" ], "height" : 0.6, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a7f47e52aa820658a17403"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : [ "flash", "quick attack" ], "height" : 0.5, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a7f50f52aa820658a17404"), "name" : "Flareon", "description" : "Raposinha bonitinha versão de fogo", "type" : "fire", "attack" : null, "defense" : 40, "height" : 0.9, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a7f52652aa820658a17406"), "name" : "Vaporeon", "description" : "Raposinha bonitinha versão de água", "type" : "água", "attack" : null, "defense" : 32, "height" : 1, "moves" : [ "desvio" ] }
    { "_id" : ObjectId("56a9538a3c1d0983f9fec101"), "name" : "AindaNaoExisteMon", "active" : true, "attack" : null, "defense" : null, "height" : null, "description" : "Sem maiores informações" }
```

## 7. Pesquisar todos pokemons que tenham o ataque `investida`  E tenham a defesa não menor ou igual a 49

```
    var query = {$and: [{moves: {$in: ['investida']}}, {defense: {lte: 49}}]}
    db.pokemons.find(query)
```

## 8. Remova todos os pokemons do tipo água e com attack menor que 50.

```
    var query = {$and: [ {type: /agua/i}, {attack: {lt:50}}]}
    db.pokemons.remove(query)
    WriteResult({ "nRemoved" : 0 })
```