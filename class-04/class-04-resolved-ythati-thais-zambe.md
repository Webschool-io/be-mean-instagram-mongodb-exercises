# MongoDB - Aula 04 - Exercício
Autor: Thais Zambe

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.##
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {name:'Pikachu'}
wolkenritter(mongod-3.0.6) be-mean-pokemons> var mod = {$pushAll: {moves:['choque do trovão', 'investida']}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {name:'Squirtle'}
wolkenritter(mongod-3.0.6) be-mean-pokemons> var mod = {$pushAll: {moves:['ataque de bolhas', 'aumentar defesa']}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {name:'Bulbassauro'}
wolkenritter(mongod-3.0.6) be-mean-pokemons> var mod = {$pushAll: {moves:['ataque de cipó', 'folhas cortantes']}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {name:'Charmander'}
wolkenritter(mongod-3.0.6) be-mean-pokemons> var mod = {$pushAll: {moves:['solta fogo', 'solta ainda mais fogo']}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {}
wolkenritter(mongod-3.0.6) be-mean-pokemons> var mod = {$push: {moves:'desvio'}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> var options = {multi:true}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 9 existing record(s) in 1ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {name:'AindaNaoExisteMon'}
wolkenritter(mongod-3.0.6) be-mean-pokemons> var mod = {$setOnInsert: {name:'AindaNaoExisteMon', description:'Sem maiores informações', type:null, attack:null, height:null, defense:null, moves:null}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> var options = {upsert:true}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56509e032ce86db89c291c8f")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {moves: {$in:['investida', 'ataque de cipó']}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564894bf8c1c831aa98033f8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 49,
  "moves": [
    "ataque de cipó",
    "folhas cortantes",
    "desvio"
  ]
}
{
  "_id": ObjectId("564894bf8c1c831aa98033f7"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "defense": 40,
  "moves": [
    "choque do trovão",
    "investida",
    "desvio"
  ]
}
Fetched 2 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {moves: {$all:['investida', 'desvio']}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564894bf8c1c831aa98033f7"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "defense": 40,
  "moves": [
    "choque do trovão",
    "investida",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {type: {$ne:'electric'}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564894bf8c1c831aa98033f8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 49,
  "moves": [
    "ataque de cipó",
    "folhas cortantes",
    "desvio"
  ]
}
{
  "_id": ObjectId("564894bf8c1c831aa98033f9"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 43,
  "moves": [
    "solta fogo",
    "solta ainda mais fogo",
    "desvio"
  ]
}
{
  "_id": ObjectId("564894bf8c1c831aa98033fa"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65,
  "moves": [
    "ataque de bolhas",
    "aumentar defesa",
    "desvio"
  ]
}
{
  "_id": ObjectId("564898108c1c831aa98033fb"),
  "name": "Zorua",
  "description": "Raposa metida",
  "type": "dark",
  "attack": 65,
  "height": 0.7,
  "defense": 40,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564898108c1c831aa98033fc"),
  "name": "Charmeleon",
  "description": "Charmander revolts",
  "type": "fire",
  "attack": 64,
  "height": 1.09,
  "defense": 58,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564898108c1c831aa98033fd"),
  "name": "Gourgeist",
  "description": "Abóbora Nicky Minaj",
  "type": "ghost",
  "attack": 90,
  "height": 1.7,
  "defense": 122,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564898108c1c831aa98033fe"),
  "name": "Aron",
  "description": "Coisa estranha furadinha e fofinha",
  "type": "steel",
  "attack": 70,
  "height": 0.4,
  "defense": 100,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564898108c1c831aa98033ff"),
  "name": "Mawile",
  "description": "Aquele Ukyo do Samurai Shodown",
  "type": "steel",
  "attack": 85,
  "height": 0.6,
  "defense": 85,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56509e032ce86db89c291c8f"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": null
}
Fetched 9 record(s) in 3ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {$and: [{moves:'investida'}, {defense: {$not: {$lte:49}}}]}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.##
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {$and: [{type:'água'}, {attack: {$lt:50}}]}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```

## Demonstre qual a diferença entre os operadores `$ne` e `$not`.##
O operador `$ne` consulta valores que não são iguais (not equal) ao argumento passado, desde que esse argumento não seja REGEX:
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {type: {$ne:/steel/i}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
Error: error: {
  "$err": "Can't canonicalize query: BadValue Can't have regex as arg to $ne.",
  "code": 17287
}
```

```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {type: {$ne:'steel'}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564894bf8c1c831aa98033f8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 49,
  "moves": [
    "ataque de cipó",
    "folhas cortantes",
    "desvio"
  ]
}
{
  "_id": ObjectId("564894bf8c1c831aa98033f9"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 43,
  "moves": [
    "solta fogo",
    "solta ainda mais fogo",
    "desvio"
  ]
}
{
  "_id": ObjectId("564898108c1c831aa98033fb"),
  "name": "Zorua",
  "description": "Raposa metida",
  "type": "dark",
  "attack": 65,
  "height": 0.7,
  "defense": 40,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564898108c1c831aa98033fc"),
  "name": "Charmeleon",
  "description": "Charmander revolts",
  "type": "fire",
  "attack": 64,
  "height": 1.09,
  "defense": 58,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564898108c1c831aa98033fd"),
  "name": "Gourgeist",
  "description": "Abóbora Nicky Minaj",
  "type": "ghost",
  "attack": 90,
  "height": 1.7,
  "defense": 122,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564894bf8c1c831aa98033f7"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "defense": 40,
  "moves": [
    "choque do trovão",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56509e032ce86db89c291c8f"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": null
}
Fetched 7 record(s) in 3ms
```

O operador `$not` por outro lado realiza a operação lógica de negação (not) e precisa de uma expressão regular como argumento:
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {type: {$not:'steel'}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
Error: error: {
  "$err": "Can't canonicalize query: BadValue $not needs a regex or a document",
  "code": 17287
}
```
Aparentemente também aceita documentos. E aí vai ela funcionando:

```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {type: {$not: {$ne:'steel'}}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564898108c1c831aa98033fe"),
  "name": "Aron",
  "description": "Coisa estranha furadinha e fofinha",
  "type": "steel",
  "attack": 70,
  "height": 0.4,
  "defense": 100,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564898108c1c831aa98033ff"),
  "name": "Mawile",
  "description": "Aquele Ukyo do Samurai Shodown",
  "type": "steel",
  "attack": 85,
  "height": 0.6,
  "defense": 85,
  "moves": [
    "desvio"
  ]
}
Fetched 2 record(s) in 0ms
```
