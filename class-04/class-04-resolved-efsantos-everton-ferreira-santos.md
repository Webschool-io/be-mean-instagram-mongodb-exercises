# MongoDB - Aula 04 - Exercício
autor: Everton Ferreira Dos Santos 

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons : Pikachu, Squirtle, Bulbassauro e Charmander. 

```js
var query = {'name':'Pikachu'}
var mod = {$pushAll:{moves:['ataque full', 'ataque full master']}}
db.pokemons.update(query,mod)

var query = {'name':'Squirtle'}
var mod = {$pushAll:{moves:['redominho', 'onda gigante']}}
db.pokemons.update(query,mod)

var query = {'name':'Bulbassauro'}
var mod = {$pushAll:{moves:['chicote de cipó', 'semente sanguessuga ']}}
db.pokemons.update(query,mod)

var query = {'name':'Charmander'}
var mod = {$pushAll:{moves:['garra de metal', 'fúria']}}
db.pokemons.update(query,mod)

query = {$or:[{name:'Pikachu'}, {name:'Bulbassauro'}, {name:'Squirtle'}, {name:'Charmander'}]}
var fields = {name:1, moves:1}
db.pokemons.find(query,fields)

{
  "_id": ObjectId("586b04441ea9448f2ec30694"),
  "name": "Pikachu",
  "moves": [
    "investida",
    "choque do trovão",
    "ataque full",
    "ataque full master"
  ]
}
{
  "_id": ObjectId("586b05c71ea9448f2ec30695"),
  "name": "Bulbassauro",
  "moves": [
    "investida",
    "folha navalha",
    "chicote de cipó",
    "semente sanguessuga "
  ]
}
{
  "_id": ObjectId("586b064c1ea9448f2ec30696"),
  "name": "Charmander",
  "moves": [
    "investida",
    "lança-chamas",
    "garra de metal",
    "fúria"
  ]
}
{
  "_id": ObjectId("586b07211ea9448f2ec30697"),
  "name": "Squirtle",
  "moves": [
    "investida",
    "hidro bomba",
    "redemoinho",
    "onda gigante"
  ]
}
Fetched 4 record(s) in 32ms
```
## 2. Adicionar um movimento em todos os pokemons: `desvio`.

```js
var query = {}
var mod = {$push:{moves:'desvio'}}
var options = {multi: 1}
db.pokemons.update(query,mod,options)

Updated 6 existing record(s) in 3ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})

var query = {}
var fields = {name: 1, moves:1}
db.pokemons.find(query,fields)

{
  "_id": ObjectId("586b04441ea9448f2ec30694"),
  "name": "Pikachu",
  "moves": [
    "investida",
    "choque do trovão",
    "ataque full",
    "ataque full master",
    "desvio"
  ]
}
{
  "_id": ObjectId("586b05c71ea9448f2ec30695"),
  "name": "Bulbassauro",
  "moves": [
    "investida",
    "folha navalha",
    "chicote de cipó",
    "semente sanguessuga ",
    "desvio"
  ]
}
{
  "_id": ObjectId("586b064c1ea9448f2ec30696"),
  "name": "Charmander",
  "moves": [
    "investida",
    "lança-chamas",
    "garra de metal",
    "fúria",
    "desvio"
  ]
}
{
  "_id": ObjectId("586b07211ea9448f2ec30697"),
  "name": "Squirtle",
  "moves": [
    "investida",
    "hidro bomba",
    "redemoinho",
    "onda gigante",
    "desvio"
  ]
}
{
  "_id": ObjectId("586b09191ea9448f2ec30698"),
  "name": "Caterpie",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("587a650d3e7eb969c8edb730"),
  "name": "Testemon",
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 6 record(s) in 52ms
```
## 3. Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```js
var query = {name:'AindaNaoExisteMon'}
var mod ={$setOnInsert:{name:'AindaNaoExisteMon', type: null, attack: null,defense: null, height: null, description: 'Sem maiores informações'}}
var options = {upsert: 1}
db.pokemons.update(query,mod,options)

Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("587be72f4210bbc906e30fe4")
})

db.pokemons.find({"_id": ObjectId("587be72f4210bbc906e30fe4")})
{
  "_id": ObjectId("587be72f4210bbc906e30fe4"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 6ms
```
## 4. Pesquisar todos os pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```js
var query = {moves:{$in:['investida','fúria']}}
db.pokemons.find(query)

{
  "_id": ObjectId("586b04441ea9448f2ec30694"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "ataque full",
    "ataque full master",
    "desvio"
  ]
}
{
  "_id": ObjectId("586b05c71ea9448f2ec30695"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "chicote de cipó",
    "semente sanguessuga",
    "desvio"
  ]
}
{
  "_id": ObjectId("586b064c1ea9448f2ec30696"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "garra de metal",
    "fúria",
    "desvio"
  ]
}
{
  "_id": ObjectId("586b07211ea9448f2ec30697"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "hidro bomba",
    "redemoinho",
    "onda gigante",
    "desvio"
  ]
}
{
  "_id": ObjectId("586b09191ea9448f2ec30698"),
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
  "_id": ObjectId("587a650d3e7eb969c8edb730"),
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 6 record(s) in 78ms
```
## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```js
var query = {moves:{$all:['garra de metal','fúria']}}
{
  "_id": ObjectId("586b064c1ea9448f2ec30696"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "garra de metal",
    "fúria",
    "desvio"
  ]
}
Fetched 1 record(s) in 10ms
```
## 6. Pesquisar todos os pokemons que não são do tipo `elétrico`.

```js
var query = {type:{$ne:'eletric'}}
db.pokemons.find(query)

{
  "_id": ObjectId("586b05c71ea9448f2ec30695"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "chicote de cipó",
    "semente sanguessuga",
    "desvio"
  ]
}
{
  "_id": ObjectId("586b064c1ea9448f2ec30696"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "garra de metal",
    "fúria",
    "desvio"
  ]
}
{
  "_id": ObjectId("586b07211ea9448f2ec30697"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "hidro bomba",
    "redemoinho",
    "onda gigante",
    "desvio"
  ]
}
{
  "_id": ObjectId("586b09191ea9448f2ec30698"),
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
  "_id": ObjectId("587a650d3e7eb969c8edb730"),
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("587be72f4210bbc906e30fe4"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 6 record(s) in 83ms
```
## 7. Pesquisar todos os pokemons que tenham o ataque `investida` E tenham o attack não menor ou igual a 49.

```js
var query = {$and:[{moves:{$in:['investida']}},{attack: {$not:{$lte: 49}}}]}
db.pokemons.find(query)

{
  "_id": ObjectId("586b04441ea9448f2ec30694"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "ataque full",
    "ataque full master",
    "desvio"
  ]
}
{
  "_id": ObjectId("586b064c1ea9448f2ec30696"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "garra de metal",
    "fúria",
    "desvio"
  ]
}
{
  "_id": ObjectId("587a650d3e7eb969c8edb730"),
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 3 record(s) in 35ms
```
## 8. Remova todos os pokemons do tipo água e com attack menor que 50.

```js
var query = {$and:[{type:'água'},{attack:{$lt:50}}]}
db.pokemons.remove(query)

Removed 1 record(s) in 6ms
WriteResult({
  "nRemoved": 1
})
```
## 9. Qual a diferença entre os operadores `$ne` e `$not`.

```
A diferença entre os operadores `$ne` e `$not` é que o `$ne` não aceita REGEX diferentemente do operador `$not` que aceita REGEX e também pelo fato do operador `$ne` retornar apenas objetos que satisfaçam a condição da query, enquanto que o operador `$not`
retorna todos os objetos mesmo se eles não contiverem os campos informados na condição.
```   


 















