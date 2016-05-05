# MongoDB - Aula 04 - Exercício
autor: João Paulo Ribeiro

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> var query = {name:{$in:['Pikachu','Squirtle','Bulbassauro','Charmander'] }}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> var mod = {$pushAll:{moves:['peido explosivo','amedrontar']}}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> var options = {multi:true}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod,options)
  Updated 4 existing record(s) in 1ms
  WriteResult({
    "nMatched": 4,
    "nUpserted": 0,
    "nModified": 4
  })
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
  {
  "_id": ObjectId("5643a29682df34495fb683a0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 57,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio",
    "peido explosivo",
    "amedrontar"
  ],
  "active": false
}
{
  "_id": ObjectId("5643a3ab82df34495fb683a3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 50,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio",
    "peido explosivo",
    "amedrontar"
  ]
}
{
  "_id": ObjectId("5643a2e882df34495fb683a1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 51,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio",
    "peido explosivo",
    "amedrontar"
  ]
}
{
  "_id": ObjectId("5643a3a482df34495fb683a2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 54,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio",
    "peido explosivo",
    "amedrontar"
  ]
}

  Fetched 4 record(s) in 2ms
  ```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> query = {}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> var mod = {$push:{moves:'desvio'}}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod,options)
  Updated 12 existing record(s) in 3ms
  WriteResult({
    "nMatched": 12,
    "nUpserted": 0,
    "nModified": 12
  })
  {
    "_id": ObjectId("564a4a6ec09df7bc502160ee"),
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
    "_id": ObjectId("5643a29682df34495fb683a0"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 57,
    "height": 0.4,
    "moves": [
      "investida",
      "choque do trovão",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ],
    "active": false
  }
  {
    "_id": ObjectId("5643a3ab82df34495fb683a3"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 50,
    "height": 0.5,
    "active": false,
    "moves": [
      "investida",
      "hidro bomba",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ]
  }
  {
    "_id": ObjectId("5643a42a82df34495fb683a4"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35,
    "active": false,
    "moves": [
      "investida",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("5643a2e882df34495fb683a1"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 51,
    "height": 0.4,
    "active": false,
    "moves": [
      "investida",
      "folha navalha",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ]
  }
  {
    "_id": ObjectId("5643a3a482df34495fb683a2"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 54,
    "height": 0.6,
    "active": false,
    "moves": [
      "investida",
      "lança-chamas",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ]
  }
  {
    "_id": ObjectId("564e3818ba7988fc242d0639"),
    "active": false,
    "moves": [
      "investida",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("5643ac6794505292b56f3b53"),
    "name": "Venusaur",
    "description": "Evolução do Ivysaur",
    "attack": 82,
    "defense": 83,
    "height": 2,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("5643ac8694505292b56f3b56"),
    "name": "Magneton",
    "description": "Magneton emits a powerful magnetic force that is fatal to mechanical devices.",
    "attack": 60,
    "defense": 95,
    "height": 1,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("5643ac7194505292b56f3b54"),
    "name": "Charizard",
    "description": "Evolução do Charmeleon",
    "attack": 84,
    "defense": 78,
    "height": 1.7,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("5643ac8d94505292b56f3b57"),
    "name": "Treecko",
    "description": "It's a very nice guy",
    "attack": 45,
    "defense": 35,
    "height": 0.5,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("5643ac7d94505292b56f3b55"),
    "name": "Weedle",
    "description": "Minhoca com chifre e nariz rosa",
    "attack": 35,
    "defense": 30,
    "height": 0.3,
    "moves": [
      "desvio"
    ]
  }
  Fetched 12 record(s) in 5ms

  ```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> var query = {name: 'AindaNaoExisteMon'}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> var mod = {$set:{description:'Sem maiores informações'},$setOnInsert:{name: 'AindaNaoExisteMon',type:null,attack:null,defense:null,height:null,moves:null}}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> var options = {upsert:true}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod,options)
  Updated 1 new record(s) in 2ms
  WriteResult({
    "nMatched": 0,
    "nUpserted": 1,
    "nModified": 0,
    "_id": ObjectId("5650c4cd69f4ca51eeda9a5b")
  })
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
  {
    "_id": ObjectId("5650c4cd69f4ca51eeda9a5b"),
    "name": "AindaNaoExisteMon",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "defense": null,
    "height": null,
    "moves": null
  }
  Fetched 1 record(s) in 1ms
  ```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> var query = {moves:{$all:['investida','amedrontar']}}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
  {
    "_id": ObjectId("5643a29682df34495fb683a0"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 57,
    "height": 0.4,
    "moves": [
      "investida",
      "choque do trovão",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ],
    "active": false
  }
  {
    "_id": ObjectId("5643a3ab82df34495fb683a3"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 50,
    "height": 0.5,
    "active": false,
    "moves": [
      "investida",
      "hidro bomba",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ]
  }
  {
    "_id": ObjectId("5643a2e882df34495fb683a1"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 51,
    "height": 0.4,
    "active": false,
    "moves": [
      "investida",
      "folha navalha",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ]
  }
  {
    "_id": ObjectId("5643a3a482df34495fb683a2"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 54,
    "height": 0.6,
    "active": false,
    "moves": [
      "investida",
      "lança-chamas",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ]
  }

  ```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> var query = {moves:{$in:['peido explosivo','amedrontar']}}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
  {
    "_id": ObjectId("5643a29682df34495fb683a0"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 57,
    "height": 0.4,
    "moves": [
      "investida",
      "choque do trovão",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ],
    "active": false
  }
  {
    "_id": ObjectId("5643a3ab82df34495fb683a3"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 50,
    "height": 0.5,
    "active": false,
    "moves": [
      "investida",
      "hidro bomba",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ]
  }
  {
    "_id": ObjectId("5643a2e882df34495fb683a1"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 51,
    "height": 0.4,
    "active": false,
    "moves": [
      "investida",
      "folha navalha",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ]
  }
  {
    "_id": ObjectId("5643a3a482df34495fb683a2"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 54,
    "height": 0.6,
    "active": false,
    "moves": [
      "investida",
      "lança-chamas",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ]
  }
  Fetched 4 record(s) in 6ms
  ```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> var query = {type:{$ne:'eletric'}}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
  {
    "_id": ObjectId("564a4a6ec09df7bc502160ee"),
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
    "_id": ObjectId("5643a42a82df34495fb683a4"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35,
    "active": false,
    "moves": [
      "investida",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("564e3818ba7988fc242d0639"),
    "active": false,
    "moves": [
      "investida",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("5643ac6794505292b56f3b53"),
    "name": "Venusaur",
    "description": "Evolução do Ivysaur",
    "attack": 82,
    "defense": 83,
    "height": 2,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("5643ac8694505292b56f3b56"),
    "name": "Magneton",
    "description": "Magneton emits a powerful magnetic force that is fatal to mechanical devices.",
    "attack": 60,
    "defense": 95,
    "height": 1,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("5643ac7194505292b56f3b54"),
    "name": "Charizard",
    "description": "Evolução do Charmeleon",
    "attack": 84,
    "defense": 78,
    "height": 1.7,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("5643ac8d94505292b56f3b57"),
    "name": "Treecko",
    "description": "It's a very nice guy",
    "attack": 45,
    "defense": 35,
    "height": 0.5,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("5643ac7d94505292b56f3b55"),
    "name": "Weedle",
    "description": "Minhoca com chifre e nariz rosa",
    "attack": 35,
    "defense": 30,
    "height": 0.3,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("5650c4cd69f4ca51eeda9a5b"),
    "name": "AindaNaoExisteMon",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "defense": null,
    "height": null,
    "moves": null
  }
  {
    "_id": ObjectId("5643a29682df34495fb683a0"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 57,
    "height": 0.4,
    "moves": [
      "investida",
      "choque do trovão",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ],
    "active": false
  }
  {
    "_id": ObjectId("5643a3ab82df34495fb683a3"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 50,
    "height": 0.5,
    "active": false,
    "moves": [
      "investida",
      "hidro bomba",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ]
  }
  {
    "_id": ObjectId("5643a2e882df34495fb683a1"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 51,
    "height": 0.4,
    "active": false,
    "moves": [
      "investida",
      "folha navalha",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ]
  }
  {
    "_id": ObjectId("5643a3a482df34495fb683a2"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 54,
    "height": 0.6,
    "active": false,
    "moves": [
      "investida",
      "lança-chamas",
      "desvio",
      "peido explosivo",
      "amedrontar"
    ]
  }
  Fetched 13 record(s) in 4ms

  ```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> var query = {moves:'investida',$and:[{defense:{$lte:49}}]}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
  {
    "_id": ObjectId("5643a42a82df34495fb683a4"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35,
    "active": false,
    "moves": [
      "investida",
      "desvio"
    ]
  }

  ```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> var query = {type:'agua',$and:[{attack:{$lt:50}}]}
  joao-Inspiron-5437(mongod-3.0.7) be-mean-instagram> db.pokemons.remove(query)
  Removed 0 record(s) in 10ms
  WriteResult({
    "nRemoved": 0
  })
  ```
## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not.

  `$ne` seleciona os documentos onde o valor do campo passado não é igual ao valor passado. Não aceita RegEx.
  
  `$not` seleciona todos os documentos que vão de encontro ao criterio passado. Aceita RegEx.
