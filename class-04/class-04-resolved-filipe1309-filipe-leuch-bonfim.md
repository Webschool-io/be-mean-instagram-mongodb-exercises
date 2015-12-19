# MongoDB - Aula 04 - Exercício
autor: Filipe Leuch Bonfim

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```javascript
var attacks = [ 'Shazan', 'Abracadabra' ]
var mod = { $pushAll: { moves: attacks } }
var query = { name: /pikachu/i }
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 25ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

var query = { $or: [ {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]}
var mod = { $pushAll: { moves: attacks } }
var opts = { multi: true }
db.pokemons.update(query, mod, opts)
Updated 3 existing record(s) in 0ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```javascript
var query = {}
var mod = { $push: { moves: 'desvio' } }
var opts = { multi: true }
db.pokemons.update(query, mod, opts)
Updated 11 existing record(s) in 1ms
WriteResult({
  "nMatched": 11,
  "nUpserted": 0,
  "nModified": 11
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```javascript
var query = {name: /aindanaoexistemon/i}
var mod = { $setOnInsert: {
        name: "AindaNaoExisteMon",
        attack: null,
        defense: null,
        height: null,
        description: "Sem maiores informações"
    }
}
var opts = { upsert: true }
db.pokemons.update(query, mod, opts)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564d1633b97b6ac99058523c")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```javascript
var attacks = ['investida', /Choque do trovão/i ]
var query = { moves: { $all : attacks }}
db.pokemons.find(query)
{
  "_id": ObjectId("564a5252d4a210f9ed59b940"),
  "name": "Pikachu",
  "description": "Rato amarelo elétrico",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "Choque do trovão",
    "investida",
    "Shazan",
    "Abracadabra",
    "desvio"
  ],
  "type": "electric"
}
Fetched 1 record(s) in 0ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```javascript
var attacks = [/shazan/i, /abracadabra/i, /desvio/i ]
var query = { moves: { $all : attacks }}
db.pokemons.find(query)
{
  "_id": ObjectId("564a5252d4a210f9ed59b940"),
  "name": "Pikachu",
  "description": "Rato amarelo elétrico",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "Choque do trovão",
    "investida",
    "Shazan",
    "Abracadabra",
    "desvio"
  ],
  "type": "electric"
}
{
  "_id": ObjectId("564d0dbd9fe5d1a58cbb0c7b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "Shazan",
    "Abracadabra",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d0dda9fe5d1a58cbb0c7c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Shazan",
    "Abracadabra",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d0e079fe5d1a58cbb0c7d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "Shazan",
    "Abracadabra",
    "desvio"
  ]
}
Fetched 4 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```javascript
var query = { type: { $ne : 'elétrico' }}
db.pokemons.find(query)
{
  "_id": ObjectId("56427740ead061cff56c4121"),
  "name": "Mewtwo",
  "description": "Fodabagarai e manja dos paranaue",
  "type": "psiquico",
  "attack": 110,
  "height": 2,
  "defense": 90,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5642792eead061cff56c4122"),
  "name": "Jigglypuff",
  "description": "Jiggaly ... puff ... puff ... jiggaly!",
  "type": "normal, fada",
  "attack": 45,
  "height": 0.5,
  "defense": 20,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564279d7ead061cff56c4123"),
  "name": "Psyduck",
  "description": "Atrapalhado e fofinho",
  "type": "água",
  "attack": 52,
  "height": 0.8,
  "defense": 48,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56427a64ead061cff56c4124"),
  "name": "Mr. Mime",
  "description": "Um palhaço muitcho loko",
  "type": "psiquico, fada",
  "attack": 45,
  "height": 1.3,
  "defense": 65,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56427b38ead061cff56c4125"),
  "name": "Meowth",
  "description": "Membro da equipe rocket e, e curte uma grana",
  "type": "normal",
  "attack": 45,
  "height": 0.4,
  "defense": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564a4c24d4a210f9ed59b93f"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "defense": 8000,
  "attack": 8000,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564a5252d4a210f9ed59b940"),
  "name": "Pikachu",
  "description": "Rato amarelo elétrico",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "Choque do trovão",
    "investida",
    "Shazan",
    "Abracadabra",
    "desvio"
  ],
  "type": "electric"
}
{
  "_id": ObjectId("564d0d879fe5d1a58cbb0c7a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564d0dbd9fe5d1a58cbb0c7b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "Shazan",
    "Abracadabra",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d0dda9fe5d1a58cbb0c7c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Shazan",
    "Abracadabra",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d0e079fe5d1a58cbb0c7d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "Shazan",
    "Abracadabra",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d1633b97b6ac99058523c"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 12 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```javascript
var query = { $and: [ { moves : { $in: [/investida/i] } }, { defense: { $not: { $lte: 49 } } } ] }
query
{
  "$and": [
    {
      "moves": {
        "$in": [
          /investida/i
        ]
      }
    },
    {
      "defense": {
        "$not": {
          "$lte": 49
        }
      }
    }
  ]
}
db.pokemons.find(query)
{
  "_id": ObjectId("564a5252d4a210f9ed59b940"),
  "name": "Pikachu",
  "description": "Rato amarelo elétrico",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "Choque do trovão",
    "investida",
    "Shazan",
    "Abracadabra",
    "desvio"
  ],
  "type": "electric"
}
Fetched 1 record(s) in 0ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```javascript
var query = { $and: [ { type: /água/i }, { attack:  { $lt: 50 } } ] }
query
{
  "$and": [
    {
      "type": /água/i
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}
db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not.
```
$ne: {campo: {$ne: valor} }
No operador $ne ( != ), o campo só aceita valores como parâmetro, e ele busca os documentos que possuem valores diferentes do especificado

$not: { campo: { $not: { <operador-expressão> } } }
No operador $not ( ! ), temos que passar como parâmetro um operador-expressão, que é uma regex ou um documento, e ele realiza um não lógico, buscando os documentos que não 'casam' com a expressão/documento passada.
```
