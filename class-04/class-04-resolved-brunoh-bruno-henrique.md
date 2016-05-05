# MongoDB - Aula 04 - Exercício
autor: Bruno Henrique C. da Silva

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

    ```
    var query = {$or:[{name:/Pikachu/i}, {name:/Squirtle/i}, {name:/Bulbassauro/i}, {name:/Charmander/i}]}
    brunoh(mongod-3.0.7) be-mean-pokemons> var ataques = ['investida', 'provocar']
    brunoh(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll:{moves:ataques}}
    brunoh(mongod-3.0.7) be-mean-pokemons> var options = {multi:true}
    brunoh be-mean-pokemons> db.pokemons.update(query, mod, options)
    Updated 3 existing record(s) in 4ms
    WriteResult({
      "nMatched": 3,
      "nUpserted": 0,
      "nModified": 3
    })
    ```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

    ```
    var query = {}
    brunoh(mongod-3.0.7) be-mean-pokemons> var mod = {$push:{moves:'desvio'}}
    brunoh(mongod-3.0.7) be-mean-pokemons> var options = {multi:true}
    brunoh(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
    Updated 8 existing record(s) in 4ms
    WriteResult({
      "nMatched": 8,
      "nUpserted": 0,
      "nModified": 8
    })
    ```


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

    ```
    var query = {name:/NaoExisteMon/i}
    brunoh(mongod-3.0.7) be-mean-pokemons> var mod = {$set:{name:/NaoExisteMon/i}, $setOnInsert:{name:"NaoExisteMon", attack:null, height:null, description:"Sem maiores informações"}}
    brunoh(mongod-3.0.7) be-mean-pokemons> var options = {upsert:true}
    brunoh(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod,   options)
    Updated 1 new record(s) in 34ms
    WriteResult({
      "nMatched": 0,
      "nUpserted": 1,
      "nModified": 0,
      "_id": ObjectId("567eaa2395c39cd49b500aaf")
    })

    ```


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

    ```
    var query = {moves: {$in:['investida', 'Clone das Sombras']}}
    brunoh(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    ``

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

    ```
    var query = {moves: {$all:['investida', 'provocar']}}
    brunoh(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    ``

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

    ```
    var query = {type:{$nin:['eletrico']}}
    brunoh(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    ```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

    ```
    var query = {$and:[{moves:{$in:['investida']}}, {defense:{$lte:49}}]}
    brunoh(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    ```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

    ```
    var query = {$and:[{type:"agua"}, {attack:{$lt:50}}]}
    brunoh(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
    Removed 0 record(s) in 5ms
    WriteResult({
      "nRemoved": 0
    })
    ```