# MongoDB - Aula 04 - Exercício
autor: Rafael Ferreira Vianna

## 1 - Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander;

  ```
    var query = {$or: [{name: /Pikachu/i} , {name: /Squirtle/i} , {name: /Bulbassauro/i} , {name: /Charmander/i}]}
    var mod = {$inc: {attack: 2}}
    var options = {multi: 1}

    db.pokemons.update(query, mod, options)

  ```

## 2 - Adicionar 1 movimento em todos os pokemons: desvio;

  ```
  var query = {}
  var move = ['Desvio']
  var mod = {$pushAll: {moves: move}}
  var options = {multi: 1}

  db.pokemons.update(query, mod, options)

  ```

## 3 - Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações";

  ```
  var query = {name: /NaoExisteMon/i}
  var mod = {
    $set: {active: 1},
    $setOnInsert : {
      name:'NaoExisteMon',
      attack: null,
      defense: null,
      height: null,
      description: "Sem maiores informações"
    }
  }
  var options = { upsert: true }

  db.pokemons.update(query, mod, options)

  ```

## 4 - Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito;

   ```
   var query = {moves: {$in : ['investida', 'voar']}}
   db.pokemons.find(query)

   ```

## 5 - Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito;

  ```
  var query = {moves: {$in: ['voar']}}
  db.pokemons.find(query)

  ```

## 6 - Pesquisar todos os pokemons que não são do tipo elétrico;

  ```
  var query = {type: {$nin: ['electric']}}
  db.pokemons.find(query)

  ```

## 7 - Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49;

  ```
  var query = { $and: [{ moves: { $in: [/investida/i] }}, { defense: { $not: { $lte: 49 } } }]}
  db.pokemons.find(query)

  ```

## 8 - Remova todos os pokemons do tipo água e com attack menor que 50;

  ```
  var query = { $and: [{ type: {/agua/i }, { attack: { $lt: { 50 } } }]}
  db.pokemons.remove(query)

  ```
