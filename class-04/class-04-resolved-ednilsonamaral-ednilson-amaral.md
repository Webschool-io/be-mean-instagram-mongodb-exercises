# MongoDB - Aula 04 - Exercício  
Autor: Ednilson Amaral


Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro, Charmander
----------------------------------------------------------------------------------------------------------

```  
be-mean-pokemons> var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}  
be-mean-pokemons> var mod = {$set: {moves: ['engole fogo', 'assopra veneno']}}  
be-mean-pokemons> var options = {multi: true}  
be-mean-pokemons> db.pokemons.update(query, mod, options)  
Updated 4 existing record(s) in 5ms  
WriteResult({  
  "nMatched": 4,  
  "nUpserted": 0,  
  "nModified": 4  
})  
```


Adicionar 1 movimento em todos os pokemons: 'desvio'
-----------------------------------------------------

```  
be-mean-pokemons> var query = {}  
be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}  
be-mean-pokemons> var options = {multi: true}  
be-mean-pokemons> db.pokemons.update(query, mod, options)  
Updated 9 existing record(s) in 4ms  
WriteResult({  
  "nMatched": 9,  
  "nUpserted": 0,  
  "nModified": 9  
})  
```


Adicionar o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição 'Sem maiores informações'
----------------------------------------------------------------------------------------------------------------

```  
be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}  
be-mean-pokemons> var mod = {$setOnInsert: {name: 'AindaNaoExisteMom', attack: null, height: null, defense: null, moves: [], description: 'Sem maiores informações'}}  
be-mean-pokemons> var options = {upsert: true}  
be-mean-pokemons> db.pokemons.update(query, mod, options)  
Updated 1 new record(s) in 53ms  
WriteResult({  
  "nMatched": 0,  
  "nUpserted": 1,  
  "nModified": 0,  
  "_id": ObjectId("564de099fc7e5880d64a877e")  
})  
be-mean-pokemons> var query = {"_id": ObjectId("564de099fc7e5880d64a877e")}  
be-mean-pokemons> db.pokemons.find(query)  
{  
  "_id": ObjectId("564de099fc7e5880d64a877e"),  
  "name": "AindaNaoExisteMom",  
  "attack": null,  
  "height": null,  
  "defense": null,  
  "moves": [ ],  
  "description": "Sem maiores informações"  
}  
Fetched 1 record(s) in 2ms  
```


Pesquisar todos o pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito
--------------------------------------------------------------------------------------------------------------


```  
be-mean-pokemons> var query = {moves: {$in: ['investida', /assopra veneno/i]}}  
be-mean-pokemons> db.pokemons.find(query)  
{  
  "_id": ObjectId("5644da2d329b6e6a8376bd42"),  
  "name": "Rampardos",  
  "description": "Pode levar qualquer cascudo na cabeça que não vai sentir porra nenhuma",  
  "type": "rocha",  
  "attack": 165,  
  "defense": 60,  
  "height": 1.6,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da44329b6e6a8376bd43"),  
  "name": "Slaking",  
  "description": "Pense em um cara preguiçoso, é esse pokebola aí",  
  "type": "normal",  
  "attack": 160,  
  "defense": 100,  
  "height": 2,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da4e329b6e6a8376bd44"),  
  "name": "Haxorus",  
  "description": "Esse é dócil viu, mas se baixar a pomba gira nele, fica muito agressivo",  
  "type": "dragão",  
  "attack": 147,  
  "defense": 90,  
  "height": 1.8,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da5a329b6e6a8376bd45"),  
  "name": "Rhyperior",  
  "description": "Esse resiste até a erupções",  
  "type": "rocha",  
  "attack": 140,  
  "defense": 130,  
  "height": 2.4,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da63329b6e6a8376bd46"),  
  "name": "Metagross",  
  "description": "Esse não tem Windows como SO",  
  "type": "psíquico",  
  "attack": 135,  
  "defense": 130,  
  "height": 1.6,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("564cfedbf9025dedb2553203"),  
  "name": "Pikachu",  
  "description": "Rato elétrico bem fofinho",  
  "type": "electric",  
  "attack": 100,  
  "height": 0.4,  
  "moves": [  
    "engole fogo",  
    "assopra veneno",  
    "desvio"  
  ],  
  "active": false  
}  
{  
  "_id": ObjectId("564cff04f9025dedb2553204"),  
  "name": "Bulbassauro",  
  "description": "Chicote de trepadeira",  
  "type": "grama",  
  "attack": 49,  
  "height": 0.4,  
  "active": false,  
  "moves": [  
    "engole fogo",  
    "assopra veneno",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("564cff04f9025dedb2553205"),  
  "name": "Charmander",  
  "description": "Esse é o cão chupando manga de fofinho",  
  "type": "fogo",  
  "attack": 52,  
  "height": 0.6,  
  "active": false,  
  "moves": [  
    "engole fogo",  
    "assopra veneno",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("564cff04f9025dedb2553206"),  
  "name": "Squirtle",  
  "description": "Ejeta água que passarinho não bebe",  
  "type": "água",  
  "attack": 48,  
  "height": 0.5,  
  "active": false,  
  "moves": [  
    "engole fogo",  
    "assopra veneno",  
    "desvio"  
  ]  
}  
Fetched 9 record(s) in 11ms  
```


Pesquisar 'todos' o pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito
-----------------------------------------------------------------------------------------------------

```  
be-mean-pokemons> var query = {moves: {$in: ['engole fogo', 'assopra veneno']}}
be-mean-pokemons> db.pokemons.find(query)  
{  
  "_id": ObjectId("564cfedbf9025dedb2553203"),  
  "name": "Pikachu",  
  "description": "Rato elétrico bem fofinho",  
  "type": "electric",  
  "attack": 100,  
  "height": 0.4,  
  "moves": [  
    "engole fogo",  
    "assopra veneno",  
    "desvio"  
  ],  
  "active": false  
}  
{  
  "_id": ObjectId("564cff04f9025dedb2553204"),  
  "name": "Bulbassauro",  
  "description": "Chicote de trepadeira",  
  "type": "grama",  
  "attack": 49,  
  "height": 0.4,  
  "active": false,  
  "moves": [  
    "engole fogo",  
    "assopra veneno",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("564cff04f9025dedb2553205"),  
  "name": "Charmander",  
  "description": "Esse é o cão chupando manga de fofinho",  
  "type": "fogo",  
  "attack": 52,  
  "height": 0.6,  
  "active": false,  
  "moves": [  
    "engole fogo",  
    "assopra veneno",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("564cff04f9025dedb2553206"),  
  "name": "Squirtle",  
  "description": "Ejeta água que passarinho não bebe",  
  "type": "água",  
  "attack": 48,  
  "height": 0.5,  
  "active": false,  
  "moves": [  
    "engole fogo",  
    "assopra veneno",  
    "desvio"  
  ]  
}  
Fetched 4 record(s) in 8ms  
```


Pesquisar todos os pokemons que não são do tipo `elétrico`
-----------------------------------------------------------

```  
be-mean-pokemons> var query = {type: {$ne: 'electric'}}  
be-mean-pokemons> db.pokemons.find(query)  
{  
  "_id": ObjectId("5644da2d329b6e6a8376bd42"),  
  "name": "Rampardos",  
  "description": "Pode levar qualquer cascudo na cabeça que não vai sentir porra nenhuma",  
  "type": "rocha",  
  "attack": 165,  
  "defense": 60,  
  "height": 1.6,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da44329b6e6a8376bd43"),  
  "name": "Slaking",  
  "description": "Pense em um cara preguiçoso, é esse pokebola aí",  
  "type": "normal",  
  "attack": 160,  
  "defense": 100,  
  "height": 2,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da4e329b6e6a8376bd44"),  
  "name": "Haxorus",  
  "description": "Esse é dócil viu, mas se baixar a pomba gira nele, fica muito agressivo",  
  "type": "dragão",  
  "attack": 147,  
  "defense": 90,  
  "height": 1.8,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da5a329b6e6a8376bd45"),  
  "name": "Rhyperior",  
  "description": "Esse resiste até a erupções",  
  "type": "rocha",  
  "attack": 140,  
  "defense": 130,  
  "height": 2.4,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da63329b6e6a8376bd46"),  
  "name": "Metagross",  
  "description": "Esse não tem Windows como SO",  
  "type": "psíquico",  
  "attack": 135,  
  "defense": 130,  
  "height": 1.6,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("564cff04f9025dedb2553204"),  
  "name": "Bulbassauro",  
  "description": "Chicote de trepadeira",  
  "type": "grama",  
  "attack": 49,  
  "height": 0.4,  
  "active": false,  
  "moves": [  
    "engole fogo",  
    "assopra veneno",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("564cff04f9025dedb2553205"),  
  "name": "Charmander",  
  "description": "Esse é o cão chupando manga de fofinho",  
  "type": "fogo",  
  "attack": 52,  
  "height": 0.6,  
  "active": false,  
  "moves": [  
    "engole fogo",  
    "assopra veneno",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("564cff04f9025dedb2553206"),  
  "name": "Squirtle",  
  "description": "Ejeta água que passarinho não bebe",  
  "type": "água",  
  "attack": 48,  
  "height": 0.5,  
  "active": false,  
  "moves": [  
    "engole fogo",  
    "assopra veneno",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("564de099fc7e5880d64a877e"),  
  "name": "AindaNaoExisteMom",  
  "attack": null,  
  "height": null,  
  "defense": null,  
  "moves": [ ],  
  "description": "Sem maiores informações"  
}  
Fetched 9 record(s) in 9ms  
```


Pesquisar 'todos' pokemons que tenham o ataque 'investida' E tenham a defesa 'não menor ou igual' a 49
--------------------------------------------------------------------------------------------------------

```  
be-mean-pokemons> var query = {$and: [{moves: {$in: ['investida']}}, {defense: {$lte: 49}}]}  
be-mean-pokemons> db.pokemons.find(query)  
Fetched 0 record(s) in 1ms  
```


Nesse exercício eu fiz um outro teste para ter certeza que fiz o comando certo com `$lte: 90` e retornou:  

```  
be-mean-pokemons> var query = {$and: [{moves: {$in: ['investida']}}, {defense: {$lte: 90}}]}  
be-mean-pokemons> db.pokemons.find(query)  
{  
  "_id": ObjectId("5644da2d329b6e6a8376bd42"),  
  "name": "Rampardos",  
  "description": "Pode levar qualquer cascudo na cabeça que não vai sentir porra nenhuma",  
  "type": "rocha",  
  "attack": 165,  
  "defense": 60,  
  "height": 1.6,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da4e329b6e6a8376bd44"),  
  "name": "Haxorus",  
  "description": "Esse é dócil viu, mas se baixar a pomba gira nele, fica muito agressivo",  
  "type": "dragão",  
  "attack": 147,  
  "defense": 90,  
  "height": 1.8,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
Fetched 2 record(s) in 5ms  
```


Pesquisar 'todos' pokemons que tenham o ataque 'investida' E tenham a defesa 'não menor ou igual' a 49
-------------------------------------------------------------------------------------------------------

```  
be-mean-pokemons> var query = {$and: [{moves: 'investida'}, {defense: {$not: {$lte: 49}}}]}  
be-mean-pokemons> db.pokemons.find(query)  
{  
  "_id": ObjectId("5644da2d329b6e6a8376bd42"),  
  "name": "Rampardos",  
  "description": "Pode levar qualquer cascudo na cabeça que não vai sentir porra nenhuma",  
  "type": "rocha",  
  "attack": 165,  
  "defense": 60,  
  "height": 1.6,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da44329b6e6a8376bd43"),  
  "name": "Slaking",  
  "description": "Pense em um cara preguiçoso, é esse pokebola aí",  
  "type": "normal",  
  "attack": 160,  
  "defense": 100,  
  "height": 2,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da4e329b6e6a8376bd44"),  
  "name": "Haxorus",  
  "description": "Esse é dócil viu, mas se baixar a pomba gira nele, fica muito agressivo",  
  "type": "dragão",  
  "attack": 147,  
  "defense": 90,  
  "height": 1.8,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da5a329b6e6a8376bd45"),  
  "name": "Rhyperior",  
  "description": "Esse resiste até a erupções",  
  "type": "rocha",  
  "attack": 140,  
  "defense": 130,  
  "height": 2.4,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
{  
  "_id": ObjectId("5644da63329b6e6a8376bd46"),  
  "name": "Metagross",  
  "description": "Esse não tem Windows como SO",  
  "type": "psíquico",  
  "attack": 135,  
  "defense": 130,  
  "height": 1.6,  
  "active": false,  
  "moves": [  
    "investida",  
    "desvio"  
  ]  
}  
Fetched 5 record(s) in 7ms  
```


Remova 'todos' os pokemons do tipo água E com attack menor que 50
------------------------------------------------------------------

```  
be-mean-pokemons> var query = {$and: [{type: 'água'}, {attack: {$lt: 50}}]}  

be-mean-pokemons> db.pokemons.find(query)  
{  
  "_id": ObjectId("564cff04f9025dedb2553206"),  
  "name": "Squirtle",  
  "description": "Ejeta água que passarinho não bebe",  
  "type": "água",  
  "attack": 48,  
  "height": 0.5,  
  "active": false,  
  "moves": [  
    "engole fogo",  
    "assopra veneno",  
    "desvio"  
  ]  
}  
Fetched 1 record(s) in 3ms  

be-mean-pokemons> db.pokemons.remove(query)  
Removed 1 record(s) in 4ms  
WriteResult({  
  "nRemoved": 1  
})  

be-mean-pokemons> db.pokemons.find(query)  
Fetched 0 record(s) in 2ms  
```


Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores `$ne` e `$not`
--------------------------------------------------------------------------------------------------------------

`$ne` seleciona os documentos onde o valor do campo **não é igual** ao valor especificado no comando. Isso também inclui documentos que não contêm esse campo.  

`$not` é simular ao operador lógico **NOT**, onde ele ele seleciona os documentos onde o valor do campo que **não** sejam iguais ao valor especificado no comando. Isso também inclui documentos que não contêm esse campo.