# MongoDb - Aula 04 - Exercício
autor: Pablo R. Dinella

## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = {name:{$in:['Pikachu', 'Squirtle', 'Bulbassauro']}}
var mod = {$pushAll: {moves:['ataque sorrateiro','ataque agressivo']}}
var options = {multi:true}
db.pokemons.update(query,mod,options)
```

## 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```
var query = {}
var mod = {$push:{moves:'desvio'}}
var options = {multi:true}
db.pokemons.update(query,mod,options)
```

## 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```
var query = {name: /AindaNaoExisteMon/i}
var mod = {$setOnInsert:
    {
      name: 'AindaNaoExisteMon',
      type: null,
      attack: null,
      defense: null,
      height: null,
      description: 'sem maiores informações'
    }
}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
```

## 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```
var query = {moves: {$in: [/investida/i, /ataque sorrateiro/i]}}
db.pokemons.find(query)
```
## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
var query = {moves: {$all: [/ataque sorrateiro/i, /ataque agressivo/i]}}
db.pokemons.find(query)
```

## 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```
var query = {type: {$not: /elétrico/i}}
db.pokemons.find(query)
```

## 7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```
var query = {$and: [ {moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}} ]}
db.pokemons.find(query)
```

## 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
var query = {$and: [ {type: /água/i}, {attack: {$lt: 50}} ]}
db.pokemons.remove(query)
```

## 9. Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores `$ne` e `$not`.

Sei que o $not inclui documentos que não contenham o campo especificado e também aceita regex. Além disso o $not é operador lógico.
