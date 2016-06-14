# MongoDB - Aula 04 - Exercício
Autor: Lucas Frutig

## Exercício

1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu,Squirtle,Bulbassauro,Charmander.
```
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {name: {$in: ['Pikachu','Squirtle','Bulbassauro','Charmander']}}
vahalla(mongod-3.2.7) be-mean-pokemons> var mod = {$set: {moves: ['investida','ataque rapido']}}
vahalla(mongod-3.2.7) be-mean-pokemons> var options = {multi:true}
vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 3ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```


2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.
```
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {}
vahalla(mongod-3.2.7) be-mean-pokemons> var mod = {$push: {moves:'desvio'}}
vahalla(mongod-3.2.7) be-mean-pokemons> var options = {multi:true}
vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 5 existing record(s) in 5ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})

```

3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados, crie ele com todos os dados com valor null e descrição: "Sem maiores informações".
```
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
vahalla(mongod-3.2.7) be-mean-pokemons> var mod = {$setOnInsert: {name:'AindaNaoExisteMon',description:'Sem maiors informações',type:'poison',attack:55,height:1.1}}
vahalla(mongod-3.2.7) be-mean-pokemons> var options = {upsert:true}
vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("575f3a741cd8af62d6bb2469")
})


```

4. Pesquisar todos os pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.
``` 
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {moves: {$in: [/investida/i,/ataque rapido/i]}}
vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("575f36a5c13d789680e74892"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("575f36a5c13d789680e74893"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("575f36a5c13d789680e74894"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("575f36cac13d789680e74895"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
Fetched 4 record(s) in 5ms
```

5. Pesquisar **todos** os pokemons que possuam ataques que você adicionou, escolha seu pokemon favorito.
```
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {moves: {$all: [/ataque rapido/i,/choque do trovao/i]}}
vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("575f36cac13d789680e74895"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio",
    "choque do trovao"
  ]
}
Fetched 1 record(s) in 1ms

```

6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
``` 
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {type: {$all: [/electric/i]}}
vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("575f36cac13d789680e74895"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio",
    "choque do trovao"
  ]
}
Fetched 1 record(s) in 2ms

```

7. Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.
``` 
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{moves: {$in: [/investida/i]}},{attack: {$gte:49}} ]}
vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("575f36a5c13d789680e74892"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("575f36a5c13d789680e74893"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("575f36cac13d789680e74895"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio",
    "choque do trovao"
  ]
}
Fetched 3 record(s) in 4ms
```

8. Remova **todos** os pokemons do tipo água e com attack menor que 50.
``` 
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {$and: [ {type:/água/i}, {attack: {$lt:50}} ]}
vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 3ms
WriteResult({
  "nRemoved": 1
})

```
