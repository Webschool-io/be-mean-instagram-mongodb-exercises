# MongoDB - Aula 04 - Exercício
autor: Guilherme Catini

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```javascript
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var q = { $or: [ {name: /lulamon/i}, {name: /willismon/i}, {name: /collormon/i}, {name: /dilmamon/i} ]}
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var m = { $pushAll: { moves: ['roubo em lote', 'recolher impostos']}}
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var o = { multi: true };
corporacao-catini(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(q, m, o);
Updated 3 existing record(s) in 2ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```javascript
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var q = {}
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var m = { $push: { moves: "desvio"}}
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var o = { multi: true }
corporacao-catini(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(q, m, o)
Updated 5 existing record(s) in 1ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```javascript
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var q = { name: /AindaNaoExisteMon/i }
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var m = { $setOnInsert: { name: "AindaNaoExisteMon", attack: null, height: null, defense: null, moves: [], description: "Sem maiores informações"
... }};
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var o = { upsert: true };
corporacao-catini(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(q,m,o)
Updated 1 new record(s) in 32ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("578cfbe6912d4c7516c974b9")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```javascript
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var q = {moves:{$in:['investida',/roubo em lote/i]}}
corporacao-catini(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("578a4404689050fd26372fdc"),
  "name": "Dilmamon",
  "description": "Fantoche",
  "type": "desconhecido",
  "attack": 55,
  "defense": 25,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "roubo em lote",
    "recolher impostos",
    "desvio"
  ]
}
{
  "_id": ObjectId("578a4404689050fd26372fde"),
  "name": "Nevesmon",
  "description": "Aspirador de pó",
  "type": "desconhecido",
  "attack": 65,
  "defense": 50,
  "height": 0.7,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("578a8e5f5989263791688d1f"),
  "name": "Testemon",
  "description": "Pokemon de teste",
  "type": "grama",
  "attack": 7901,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("578a4404689050fd26372fd9"),
  "name": "Lulamon",
  "description": "Retardado mental chorão da porra",
  "type": "grama",
  "attack": 50,
  "defense": 40,
  "height": 0.5,
  "moves": [
    "investida",
    "roubo em lote",
    "recolher impostos",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("578a4404689050fd26372fdd"),
  "name": "Collormon",
  "description": "Sem descrição",
  "type": "desconhecido",
  "attack": 60,
  "defense": 45,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "roubo em lote",
    "recolher impostos",
    "desvio"
  ]
}
Fetched 5 record(s) in 3ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```javascript
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var q = {moves:/roubo em lote/i}
corporacao-catini(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("578a4404689050fd26372fdc"),
  "name": "Dilmamon",
  "description": "Fantoche",
  "type": "desconhecido",
  "attack": 55,
  "defense": 25,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "roubo em lote",
    "recolher impostos",
    "desvio"
  ]
}
{
  "_id": ObjectId("578a4404689050fd26372fd9"),
  "name": "Lulamon",
  "description": "Retardado mental chorão da porra",
  "type": "grama",
  "attack": 50,
  "defense": 40,
  "height": 0.5,
  "moves": [
    "investida",
    "roubo em lote",
    "recolher impostos",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("578a4404689050fd26372fdd"),
  "name": "Collormon",
  "description": "Sem descrição",
  "type": "desconhecido",
  "attack": 60,
  "defense": 45,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "roubo em lote",
    "recolher impostos",
    "desvio"
  ]
}
Fetched 3 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```javascript
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var q = {type:{$ne:'eletrico'}}
corporacao-catini(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("578a4404689050fd26372fdc"),
  "name": "Dilmamon",
  "description": "Fantoche",
  "type": "desconhecido",
  "attack": 55,
  "defense": 25,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "roubo em lote",
    "recolher impostos",
    "desvio"
  ]
}
{
  "_id": ObjectId("578a4404689050fd26372fde"),
  "name": "Nevesmon",
  "description": "Aspirador de pó",
  "type": "desconhecido",
  "attack": 65,
  "defense": 50,
  "height": 0.7,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("578a8e5f5989263791688d1f"),
  "name": "Testemon",
  "description": "Pokemon de teste",
  "type": "grama",
  "attack": 7901,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("578a4404689050fd26372fd9"),
  "name": "Lulamon",
  "description": "Retardado mental chorão da porra",
  "type": "grama",
  "attack": 50,
  "defense": 40,
  "height": 0.5,
  "moves": [
    "investida",
    "roubo em lote",
    "recolher impostos",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("578a4404689050fd26372fdd"),
  "name": "Collormon",
  "description": "Sem descrição",
  "type": "desconhecido",
  "attack": 60,
  "defense": 45,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "roubo em lote",
    "recolher impostos",
    "desvio"
  ]
}
{
  "_id": ObjectId("578cfbe6912d4c7516c974b9"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informações"
}
Fetched 6 record(s) in 25ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```javascript
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var q = {$and:[{moves:{$in:[/investida/i]},defense:{$gte:49}}]}
corporacao-catini(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("578a4404689050fd26372fde"),
  "name": "Nevesmon",
  "description": "Aspirador de pó",
  "type": "desconhecido",
  "attack": 65,
  "defense": 50,
  "height": 0.7,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("578a8e5f5989263791688d1f"),
  "name": "Testemon",
  "description": "Pokemon de teste",
  "type": "grama",
  "attack": 7901,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 2 record(s) in 1ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```javascript
corporacao-catini(mongod-2.6.10) be-mean-pokemons> var q = {$and:[{type:'água'},{attack:{$lt:50}}]}
corporacao-catini(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(q)
Fetched 0 record(s) in 0ms
```
