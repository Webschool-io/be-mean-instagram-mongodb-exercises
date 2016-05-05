# MongoDB - Aula 04 - Exercício
autor: Mateus Cerezini Gomes

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
be-mean-instagram> query
{
  "name": {
    "$in": [
      /pikachu/i,
      /squirtle/i,
      /bulbassauro/i,
      /charmander/i
    ]
  }
}

be-mean-instagram> mod
{
  "$pushAll": {
    "moves": [
      "pirueta mortal",
      "cantiga sonífero"
    ]
  }
}

be-mean-instagram> options
{
  "multi": true
}

be-mean-instagram> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 373ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
be-mean-instagram> query = {}
be-mean-instagram> mod = {$push: {moves: "desvio"}}
be-mean-instagram> var options = {multi: true}
be-mean-instagram> db.pokemons.update(query,mod,options)
Updated 6 existing record(s) in 3ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
be-mean-instagram> query = {name: /AindaNaoExisteMon/i}
{
  "name": /AindaNaoExisteMon/i
}

be-mean-instagram> mod = {$setOnInsert: {name: 'AindaNaoExisteMon', description: "Sem maiores informações", type: null, attack: null, height: null, active: null, moves: null}}
{
  "$setOnInsert": {
    "name": "AindaNaoExisteMon",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "height": null,
    "active": null,
    "moves": null
  }
}

be-mean-instagram> options = {upsert: true}
{
  "upsert": true
}

be-mean-instagram> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 239ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5665c023f79f5010d6c8ed50")
})
```
## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
be-mean-instagram> query
{
  "moves": {
    "$all": [
      /investida/i,
      /pirueta mortal/i
    ]
  }
}

be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5642781cc41db98ac1c42f13"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "pirueta mortal",
    "cantiga sonífero",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56427a13c41db98ac1c42f14"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "pirueta mortal",
    "cantiga sonífero",
    "desvio"
  ]
}
{
  "_id": ObjectId("56427a37c41db98ac1c42f15"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "pirueta mortal",
    "cantiga sonífero",
    "desvio"
  ]
}
{
  "_id": ObjectId("56427a58c41db98ac1c42f16"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "pirueta mortal",
    "cantiga sonífero",
    "desvio"
  ]
}

```
## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
query = {moves: {$in: [/cantiga sonífero/i, /pirueta mortal/i] } }
{
  "moves": {
    "$in": [
      /cantiga sonífero/i,
      /pirueta mortal/i
    ]
  }
}

be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5642781cc41db98ac1c42f13"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "pirueta mortal",
    "cantiga sonífero",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56427a13c41db98ac1c42f14"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "pirueta mortal",
    "cantiga sonífero",
    "desvio"
  ]
}
{
  "_id": ObjectId("56427a37c41db98ac1c42f15"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "pirueta mortal",
    "cantiga sonífero",
    "desvio"
  ]
}
{
  "_id": ObjectId("56427a58c41db98ac1c42f16"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "pirueta mortal",
    "cantiga sonífero",
    "desvio"
  ]
}

```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
query = {type: {$not: /eletric/i}}
{
  "type": {
    "$not": /eletric/i
  }
}

be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56427befc41db98ac1c42f17"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 15,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a2ad8a778588eeef588c6"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56427a13c41db98ac1c42f14"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "pirueta mortal",
    "cantiga sonífero",
    "desvio"
  ]
}
{
  "_id": ObjectId("56427a37c41db98ac1c42f15"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "pirueta mortal",
    "cantiga sonífero",
    "desvio"
  ]
}
{
  "_id": ObjectId("56427a58c41db98ac1c42f16"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "pirueta mortal",
    "cantiga sonífero",
    "desvio"
  ]
}
{
  "_id": ObjectId("5665c023f79f5010d6c8ed50"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "active": null,
  "moves": null
}
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
be-mean-instagram> query = {$and: [{moves: {$in: [/investida/i]}},{defense: {$gt: 49}} ]}
{
  "$and": [
    {
      "moves": {
        "$in": [
          /investida/i
        ]
      }
    },
    {
      "defense": {
        "$not": {
            $lte: 49
        }
      }
    }
  ]
}

be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564a2ad8a778588eeef588c6"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
be-mean-instagram> query = {$and: [{type: /água/i},{attack: {$lt: 50}} ]}
{
  "$and": [
    {
      "type": /água/i
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}

be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 12ms
WriteResult({
  "nRemoved": 1
})
```

## Qual a diferença entre $ne e $not
O $ne significa `not equal`, logo é usado na comparação da não igualdade entre dois valores, como: `ataque diferente de 3`. Já o $not é uma negação lógica, logo pode se usar para criar sentenças lógicas como `não é maior ou igual a 3`.
