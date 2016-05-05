# MongoDB - Aula 04 - Exercício
autor: Islanilton Rodrigues

## 1 - **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var query = {
...   "$or": [
...     {
...       "name": /pikachu/i
...     },
...     {
...       "name": /squirtle/i
...     },
...     {
...       "name": /bulbassauro/i
...     },
...     {
...       "name": /charmander/i
...     }
...   ]
... }

ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var mod = {$pushAll: {moves: ['esquiva','ataque bruto']}};
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var opts = {multi: true};
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> db.pokemons.update(query, mod, opts);
Updated 4 existing record(s) in 20ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## 2 - **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var query = {}
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var mod = {$push: {moves: "desvio"}};
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var opts = {multi: true};
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> db.pokemons.update(query, mod, opts);
Updated 9 existing record(s) in 7ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})

```

## 3 -  **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i};
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var mod = { $setOnInsert: {
...     name: "AindaNaoExisteMon"
...   , attack: null
...   , height: null
...   , defense: null
...   , moves: []
...   , description: "Sem maiores informações"
... }}
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var opts = {upsert: true}
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> db.pokemons.update(query, mod, opts);
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564d36d03e3c2d6a9ed74499")
})
```

## 4 - Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var query = {moves: {$in: ['investida', /ataque bruto/i] }};
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> db.pokemons.find();
{
  "_id": ObjectId("5642c54453f28318ac852fdc"),
  "name": "Venusaur",
  "description": "Este é um Pokémon de força, com um alto Sp. Atk e Sp. Def",
  "attack": 82,
  "defense": 83,
  "height": 2.5,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642c54453f28318ac852fdd"),
  "name": "Meganium",
  "description": "Pokémon que se destaca não pelo seu ataque, mas sim pela sua defesa",
  "attack": 100,
  "defense": 105,
  "height": 1.8,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642c54453f28318ac852fde"),
  "name": "Sceptile",
  "description": "Sceptile apresenta uma combinação de alta velocidade",
  "attack": 85,
  "defense": 65,
  "height": 1.7,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642c54453f28318ac852fdf"),
  "name": "Torterra",
  "description": "Pokémon pesado e lento, porém com defesa e ataque muito altos",
  "attack": 109,
  "defense": 105,
  "height": 2.1,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642c54453f28318ac852fe0"),
  "name": "Serperior",
  "description": "Serperior tem um grande destaque pela sua velocidade",
  "attack": 75,
  "defense": 95,
  "height": 3.3,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d301c2adc67538d71b30d"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d301c2adc67538d71b30e"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d301c2adc67538d71b30f"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d301c2adc67538d71b310"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d36d03e3c2d6a9ed74499"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [
    "investida"
  ],
  "description": "Sem maiores informações"
}
Fetched 10 record(s) in 7ms
```

## 5 -  Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var query = { moves: { $all: [/desvio/i, /ataque bruto/i] }}
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("564d301c2adc67538d71b30d"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d301c2adc67538d71b30e"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d301c2adc67538d71b30f"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d301c2adc67538d71b310"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
Fetched 4 record(s) in 5ms
```

## 6 - Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var query = {type: {$ne: "elétrico"}}
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5642c54453f28318ac852fdc"),
  "name": "Venusaur",
  "description": "Este é um Pokémon de força, com um alto Sp. Atk e Sp. Def",
  "attack": 82,
  "defense": 83,
  "height": 2.5,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642c54453f28318ac852fdd"),
  "name": "Meganium",
  "description": "Pokémon que se destaca não pelo seu ataque, mas sim pela sua defesa",
  "attack": 100,
  "defense": 105,
  "height": 1.8,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642c54453f28318ac852fde"),
  "name": "Sceptile",
  "description": "Sceptile apresenta uma combinação de alta velocidade",
  "attack": 85,
  "defense": 65,
  "height": 1.7,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642c54453f28318ac852fdf"),
  "name": "Torterra",
  "description": "Pokémon pesado e lento, porém com defesa e ataque muito altos",
  "attack": 109,
  "defense": 105,
  "height": 2.1,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642c54453f28318ac852fe0"),
  "name": "Serperior",
  "description": "Serperior tem um grande destaque pela sua velocidade",
  "attack": 75,
  "defense": 95,
  "height": 3.3,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d301c2adc67538d71b30e"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d301c2adc67538d71b30f"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d301c2adc67538d71b310"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d36d03e3c2d6a9ed74499"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [
    "investida"
  ],
  "description": "Sem maiores informações"
}
Fetched 9 record(s) in 12ms

```

## 7 - Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var query =  {
...   $and: [
...     {
...       moves: {
...         $in: [
...           /investida/i
...         ]
...       }
...     },
...     {
...       attack: {
...         $not: {
...           $lte: 49
...         }
...       }
...     }
...   ]
... }
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5642c54453f28318ac852fdc"),
  "name": "Venusaur",
  "description": "Este é um Pokémon de força, com um alto Sp. Atk e Sp. Def",
  "attack": 82,
  "defense": 83,
  "height": 2.5,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642c54453f28318ac852fdd"),
  "name": "Meganium",
  "description": "Pokémon que se destaca não pelo seu ataque, mas sim pela sua defesa",
  "attack": 100,
  "defense": 105,
  "height": 1.8,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642c54453f28318ac852fde"),
  "name": "Sceptile",
  "description": "Sceptile apresenta uma combinação de alta velocidade",
  "attack": 85,
  "defense": 65,
  "height": 1.7,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642c54453f28318ac852fdf"),
  "name": "Torterra",
  "description": "Pokémon pesado e lento, porém com defesa e ataque muito altos",
  "attack": 109,
  "defense": 105,
  "height": 2.1,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642c54453f28318ac852fe0"),
  "name": "Serperior",
  "description": "Serperior tem um grande destaque pela sua velocidade",
  "attack": 75,
  "defense": 95,
  "height": 3.3,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d301c2adc67538d71b30d"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d301c2adc67538d71b30f"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "esquiva",
    "ataque bruto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564d36d03e3c2d6a9ed74499"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [
    "investida"
  ],
  "description": "Sem maiores informações"
}
Fetched 8 record(s) in 6ms

```

## 8 - Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> var query = {
...     $and: [
...         { attack: { $lt: 50 } },
...         { type: 'água'}
...     ]
... }
ubuntu-dev(mongod-2.6.3) be-mean-pokemons> db.pokemons.remove(query);
Removed 1 record(s) in 15ms
WriteResult({
  "nRemoved": 1
})
```
## 9 - Qual a diferença entre os operadores $ne e $not.
```
$ne : Encontra  valores não iguais  ao  valor especificado. E não aceita REGEX "ex: var query = {type:{$ne: \grama\i}}"

O $not "Operador Lógico": Inverte  o efeito  da  consulta  e retorna os  documentos  que não 
satisfazem  o critério  informadoaceita REGEX
```