# MongoDb - Aula 04
**Autor**: Willian Lauber


## Exercício

### 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro-está escrito Bulbasaur no arquivo pokemons.json- e Charmander.



```js
 $ mongo be-mean-pokemons
MongoDB shell version: 2.6.10

connecting to: be-mean-pokemons
Mongo-Hacker 0.0.14
lubuntu(mongod-2.6.10) be-mean-pokemons> var query = { $or: [ { name: "Pikachu" }, { name : "Squir
tle" }, {name : "Bulbasaur"}, {name : "Charmander"} ] }
lubuntu(mongod-2.6.10) be-mean-pokemons> var mod = {$push : {moves:{$each : ["persistencia", "esfo
rço"]}}}
lubuntu(mongod-2.6.10) be-mean-pokemons> var opt = {multi : true}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 4 existing record(s) in 10ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
lubuntu(mongod-2.6.10) be-mean-pokemons>
```

### 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```js
lubuntu(mongod-2.6.10) be-mean-pokemons> var query = {}
lubuntu(mongod-2.6.10) be-mean-pokemons> var mod = {$push : {moves : 'desvio'}}
lubuntu(mongod-2.6.10) be-mean-pokemons> var options = {multi : true}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 610 existing record(s) in 12ms
WriteResult({
  "nMatched": 610,
  "nUpserted": 0,
  "nModified": 610
})
```

### 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```js
lubuntu(mongod-2.6.10) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
lubuntu(mongod-2.6.10) be-mean-pokemons> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', type: null, attack: null, defense: null, height: null, description: 'Sem maiores informações'}}
lubuntu(mongod-2.6.10) be-mean-pokemons> var options = {upsert: true}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, options)
```

### 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```js
lubuntu(mongod-2.6.10) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /persistencia/i]}}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)

```

### 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```js
lubuntu(mongod-2.6.10) be-mean-pokemons> var query = {moves: {$all: [/esforço/i, /persistencia/i]}}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
```

### 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```js
lubuntu(mongod-2.6.10) be-mean-pokemons> var query = {type: {$not: /elétrico/i}}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
```

### 7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a attack **não menor ou igual** a 49.

```js
lubuntu(mongod-2.6.10) be-mean-pokemons> var query = {$and:[ {moves: {$in: [/investida/i]}}, {attack: {$not: {$lte: 49}}}]}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
```

### 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.
```js
lubuntu(mongod-2.6.10) be-mean-pokemons> var query = {$and: [ {types : {$in : ["water"]}}, {attack: {$lt : 50}} ]}
db.pokemons.remove(query)
```

### 9. Demonstre qual a diferença entre os operadores '$ne' e '$not'

```js
$ne, not equal, operador de comparação DE UM CAMPO COM OUTRO, não aceita rejex. Necessariamente o banco deve possuir o campo sendo buscado.
$not, not lógico, aceita regex.
```
