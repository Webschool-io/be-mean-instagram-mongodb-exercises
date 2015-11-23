# MongoDB - Aula 04 - Exercício
autor: Leonam Carlos da S Souza

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var query = {name: /Pikachu/i}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var mod = {$pushAll: {moves: ['raio de luz','raio de trovão']}}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var query = {name: /Squirtle/i}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var mod = {$pushAll: {moves: ['jato potente' , 'água nervosa']}}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod)
Updated 1 existing record(s) in 357ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var query = {name: /Bulbassauro/i}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var mod = {$pushAll: {moves: ['lamina afiada', 'ataque da grama']}}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```




```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var mod = {$pushAll: {moves:[ 'fogo furioso',' explosão de fogo ']}}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```

Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var query = {}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var mod = {$push: {moves: 'desvio'}}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var options ={multi: true}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod,options)
Updated 7 existing record(s) in 2ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})



```
## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var query = {name: /AindaNaoExisteMon/i}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var mod = {$setOnInsert:{ name: 'AindaNaoExisteMon', type: null, attack: null , defense: null , height: null , description: 'Sem maiores informações'}}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var options = {upsert: true}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56538dc6d95d34f7414447cd")
})


```
## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var query = {moves: {$in: [/investida/i , /lamina afiada/i]}}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)


```
## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var query = {moves: {$all: [/lamina afiada/i , /ataque da grama/i]}}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5652a886a3f6e8b765214f2b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "lamina afiada",
    "ataque da grama",
    "desvio"
  ]
}


```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> var query = {moves: {$all: [/lamina afiada/i , /ataque da grama/i]}}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5652a886a3f6e8b765214f2b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "lamina afiada",
    "ataque da grama",
    "desvio"
  ]
}


```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram>  var query = {$and: [ {moves: {$in: ['investida']}},  {attack: {$not: {$lte: 49}}} ]}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)


```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 7ms
WriteResult({
  "nRemoved": 1
})





```
