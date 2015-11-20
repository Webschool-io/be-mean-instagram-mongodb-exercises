# MongoDB - Aula 04 - Exercício
# Autor: Rodrigo de Medeiros Gianotto 

## Step 1: Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var query = { $or: [{name: /pikachu/i},{name: /squirtle/i},{name: /bulbassauro/i},{name:/charmander/i}] }
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var mod = {$set: { attack: ['fogo veloz','tentaculo escuro'] } }
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var options = { multi: true }
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query, mod,options)
Updated 4 existing record(s) in 1ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 3
})
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5648bb0e258133224d47381a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.4,
  "moves": "teste2"
}
{
  "_id": ObjectId("5648bb7f258133224d47381b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.4,
  "moves": "teste2"
}
{
  "_id": ObjectId("5648bb92258133224d47381c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.6,
  "moves": "teste2"
}
{
  "_id": ObjectId("5648bbb7258133224d47381d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.5,
  "active": true,
  "moves": "teste2"
}
Fetched 4 record(s) in 3ms
```

## Step 2: Adicionar 1 movimento em todos os pokemons: desvio.
```
var query = {}
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var options = { multi: true}
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var mod = { $set: { moves: 'desvio' } } 
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query, mod,options)
Updated 6 existing record(s) in 1ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find()
{
  "_id": ObjectId("5648bb0e258133224d47381a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.4,
  "moves": "desvio"
}
{
  "_id": ObjectId("5648bb7f258133224d47381b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.4,
  "moves": "desvio"
}
{
  "_id": ObjectId("5648bb92258133224d47381c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.6,
  "moves": "desvio"
}
{
  "_id": ObjectId("5648bbb7258133224d47381d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.5,
  "active": true,
  "moves": "desvio"
}
{
  "_id": ObjectId("5648bc60258133224d47381e"),
  "name": "Caterpie",
  "description": "teste",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": "desvio"
}
{
  "_id": ObjectId("564aac4c258133224d473824"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 7210,
  "defense": 8000,
  "moves": "desvio"
}
Fetched 6 record(s) in 2ms
```

## Step 3: Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
```
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var query = {name: /aindanaoexistemon/i}
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var options = { upsert: true }
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var mod = { $push: {moves:'desvio'}, $setOnInsert: { name:'AindaNaoExisteMon', description: 'Sem Maiores Informações', type: null, attack:null, defense:null  } }
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query, mod,options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564da50f3bb7ea5938796ba3")
})
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find()
{
  "_id": ObjectId("5648bb0e258133224d47381a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.4,
  "moves": "desvio"
}
{
  "_id": ObjectId("5648bb7f258133224d47381b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.4,
  "moves": "desvio"
}
{
  "_id": ObjectId("5648bb92258133224d47381c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.6,
  "moves": "desvio"
}
{
  "_id": ObjectId("5648bbb7258133224d47381d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.5,
  "active": true,
  "moves": "desvio"
}
{
  "_id": ObjectId("5648bc60258133224d47381e"),
  "name": "Caterpie",
  "description": "teste",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": "desvio"
}
{
  "_id": ObjectId("564aac4c258133224d473824"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 7210,
  "defense": 8000,
  "moves": "desvio"
}
{
  "_id": ObjectId("564da50f3bb7ea5938796ba3"),
  "moves": [
    "desvio"
  ],
  "name": "AindaNaoExisteMon",
  "description": "Sem Maiores Informações",
  "type": null,
  "attack": null,
  "defense": null
}
Fetched 7 record(s) in 2ms
```

## Step 4: Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
```

```

## Step 5: Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

Existem essas duas opções de queries para este cenário:
```
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var query = {attack: { $all: ['investida', 'fogo veloz' ]  } }
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var query = {$and: [{attack: 'investida'},{attack:'fogo veloz'}] }
```

Os resultados serão os mesmos
```
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5648bb92258133224d47381c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": [
    "fogo veloz",
    "tentaculo escuro",
    "investida",
    "corrida vulcão"
  ],
  "height": 0.6,
  "moves": [
    "marcha atlética"
  ]
}
{
  "_id": ObjectId("5648bbb7258133224d47381d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": [
    "fogo veloz",
    "tentaculo escuro",
    "investida",
    "corrida vulcão"
  ],
  "height": 0.5,
  "active": true,
  "moves": [
    "marcha atlética"
  ]
}
Fetched 2 record(s) in 1ms
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> 
```

## Step 6: Pesquisar todos os pokemons que não são do tipo elétrico.

Aqui começamos a entender que você pode compor queries de uma maneira interessante, tipo: 
var query = {type: {$not: {$in: [/grama/i,/electric/i] } } } 

Enfim, vamos voltar ao foco do exercício.

```
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var query = {type: {$ne: 'electric' } }
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5648bb7f258133224d47381b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.4,
  "moves": [
    "marcha atlética"
  ]
}
{
  "_id": ObjectId("5648bc60258133224d47381e"),
  "name": "Caterpie",
  "description": "teste",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "marcha atlética"
  ]
}
{
  "_id": ObjectId("564aac4c258133224d473824"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 7210,
  "defense": 8000,
  "moves": [
    "marcha atlética"
  ]
}
{
  "_id": ObjectId("564da50f3bb7ea5938796ba3"),
  "name": "AindaNaoExisteMon",
  "description": "Sem Maiores Informações",
  "type": null,
  "attack": null,
  "defense": null,
  "moves": [
    "marcha atlética"
  ]
}
{
  "_id": ObjectId("5648bb92258133224d47381c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": [
    "fogo veloz",
    "tentaculo escuro",
    "investida",
    "corrida vulcão"
  ],
  "height": 0.6,
  "moves": [
    "marcha atlética"
  ]
}
{
  "_id": ObjectId("5648bbb7258133224d47381d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": [
    "fogo veloz",
    "tentaculo escuro",
    "investida",
    "corrida vulcão"
  ],
  "height": 0.5,
  "active": true,
  "moves": [
    "marcha atlética"
  ]
}
Fetched 6 record(s) in 2ms
```

## Step 7: Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 0.49.
```
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var query = {$and: [{attack: {$in: ["investida"]}}, {defense: {$gte:0.49}}]}
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5648bb92258133224d47381c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": [
    "fogo veloz",
    "tentaculo escuro",
    "investida",
    "corrida vulcão"
  ],
  "height": 0.6,
  "moves": [
    "marcha atlética"
  ],
  "defense": 0.54
}
Fetched 1 record(s) in 1ms
```

## Step 8: Remova todos os pokemons do tipo água e com defense menor que 1.
```
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var query = {$and: [{type: /água/i},{defense: {$lt: 1}}  ]}
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5648bbb7258133224d47381d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": [
    "fogo veloz",
    "tentaculo escuro",
    "investida",
    "corrida vulcão"
  ],
  "height": 0.5,
  "active": true,
  "moves": [
    "marcha atlética"
  ],
  "defense": 0.45
}
Fetched 1 record(s) in 0ms
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find()
{
  "_id": ObjectId("5648bb0e258133224d47381a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.4,
  "moves": [
    "marcha atlética"
  ],
  "defense": 0.72
}
{
  "_id": ObjectId("5648bb7f258133224d47381b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": [
    "fogo veloz",
    "tentaculo escuro"
  ],
  "height": 0.4,
  "moves": [
    "marcha atlética"
  ],
  "defense": 0.54
}
{
  "_id": ObjectId("5648bc60258133224d47381e"),
  "name": "Caterpie",
  "description": "teste",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "marcha atlética"
  ]
}
{
  "_id": ObjectId("564aac4c258133224d473824"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 7210,
  "defense": 8000,
  "moves": [
    "marcha atlética"
  ]
}
{
  "_id": ObjectId("564da50f3bb7ea5938796ba3"),
  "name": "AindaNaoExisteMon",
  "description": "Sem Maiores Informações",
  "type": null,
  "attack": null,
  "defense": null,
  "moves": [
    "marcha atlética"
  ]
}
{
  "_id": ObjectId("5648bb92258133224d47381c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": [
    "fogo veloz",
    "tentaculo escuro",
    "investida",
    "corrida vulcão"
  ],
  "height": 0.6,
  "moves": [
    "marcha atlética"
  ],
  "defense": 0.54
}
Fetched 6 record(s) in 1ms
```