MongoDB - Aula 04 - Exercício

autor: Eliel das Virgens


01 - Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = { $or: [{name:'pikachu'},{name:'Squirtle'},{name:'Bulbassauro'},{name:'Charmander'}]}
darkSide(mongod-2.6.3) be-mean-pokemons> var attacks = ['Pegar Visao da malandragem','Dichavação profunda']
darkSide(mongod-2.6.3) be-mean-pokemons> var mod = { $pushAll: {attacks : attacks}}
darkSide(mongod-2.6.3) be-mean-pokemons> var options = {multi:true}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 3ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```

02 - Adicionar 1 movimento em todos os pokemons: desvio.
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {}
darkSide(mongod-2.6.3) be-mean-pokemons> var moves = ['desvio']
darkSide(mongod-2.6.3) be-mean-pokemons> var mod = { $pushAll: {moves : moves} }
darkSide(mongod-2.6.3) be-mean-pokemons> var options = {multi:true}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 12 existing record(s) in 3ms
WriteResult({
  "nMatched": 12,
  "nUpserted": 0,
  "nModified": 12
})

```

03 - Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {name :/aindaNaoExisteMon/i}
darkSide(mongod-2.6.3) be-mean-pokemons> var mod = {$setOnInsert : {name:'aindaNaoExisteMon' , type:null , attack:null , defense:null , height:null , description : 'sem maiores informações'}
... }
darkSide(mongod-2.6.3) be-mean-pokemons> mod
{
  "$setOnInsert": {
    "name": "aindaNaoExisteMon",
    "type": null,
    "attack": null,
    "defense": null,
    "height": null,
    "description": "sem maiores informações"
  }
}
darkSide(mongod-2.6.3) be-mean-pokemons> var opt = {upsert : true}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.update(query,mod,opt)
Updated 1 new record(s) in 15ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56b7e6cced74435f14db2cc8")
})

```

04 - Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {moves:{$in : [/investida/i , /esfera eletrica/i]}}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b7478eb4620a5d4ec2cb52"),
  "name": "Black Alien Mon",
  "description": "Pokemon da Rima",
  "attack": "250",
  "defense": "300",
  "height": 1.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74890b4620a5d4ec2cb53"),
  "name": "Bnegao",
  "description": "Pokemon pensador",
  "attack": "150",
  "defense": "400",
  "height": 1.1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74894b4620a5d4ec2cb54"),
  "name": "Marcelo D2",
  "description": "Pokemon Smoke Hard",
  "attack": "350",
  "defense": "500",
  "height": 1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74897b4620a5d4ec2cb55"),
  "name": "Formiga",
  "description": "Pokemon do Baixo",
  "attack": "50",
  "defense": "200",
  "height": 1.4,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74899b4620a5d4ec2cb56"),
  "name": "Pedrinho",
  "description": "Bateria psichodelica",
  "attack": "80",
  "defense": "220",
  "height": 1.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7489bb4620a5d4ec2cb57"),
  "name": "Speed Freaks",
  "description": "Pokemon Flow ou Levada",
  "attack": "500",
  "defense": 900,
  "height": 1.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7d127b4620a5d4ec2cb5c"),
  "description": "Pokemon de Teste",
  "name": "Testemon",
  "attack": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56b7dc4ded74435f14db2cc7"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7bbf7b4620a5d4ec2cb5b"),
  "name": "pikachu",
  "description": "poderes eletricos",
  "attack": 48,
  "defense": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false,
  "attacks": [
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda"
  ]
}
Fetched 9 record(s) in 8ms

```

05 - Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {moves : {$all : [/desvio/i]}}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b7478eb4620a5d4ec2cb52"),
  "name": "Black Alien Mon",
  "description": "Pokemon da Rima",
  "attack": "250",
  "defense": "300",
  "height": 1.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74890b4620a5d4ec2cb53"),
  "name": "Bnegao",
  "description": "Pokemon pensador",
  "attack": "150",
  "defense": "400",
  "height": 1.1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74894b4620a5d4ec2cb54"),
  "name": "Marcelo D2",
  "description": "Pokemon Smoke Hard",
  "attack": "350",
  "defense": "500",
  "height": 1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74897b4620a5d4ec2cb55"),
  "name": "Formiga",
  "description": "Pokemon do Baixo",
  "attack": "50",
  "defense": "200",
  "height": 1.4,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74899b4620a5d4ec2cb56"),
  "name": "Pedrinho",
  "description": "Bateria psichodelica",
  "attack": "80",
  "defense": "220",
  "height": 1.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7489bb4620a5d4ec2cb57"),
  "name": "Speed Freaks",
  "description": "Pokemon Flow ou Levada",
  "attack": "500",
  "defense": 900,
  "height": 1.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7d127b4620a5d4ec2cb5c"),
  "description": "Pokemon de Teste",
  "name": "Testemon",
  "attack": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56b7dc4ded74435f14db2cc7"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7bbf7b4620a5d4ec2cb5b"),
  "name": "pikachu",
  "description": "poderes eletricos",
  "attack": 48,
  "defense": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false,
  "attacks": [
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda"
  ]
}
{
  "_id": ObjectId("56b7e2c9b4620a5d4ec2cb5d"),
  "name": "Squirtle",
  "attack": 55,
  "defense": 90,
  "height": 0.3,
  "attacks": [
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7e2cfb4620a5d4ec2cb5e"),
  "name": "Bulbassauro",
  "attack": 52,
  "defense": 85,
  "height": 0.4,
  "attacks": [
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7e2d5b4620a5d4ec2cb5f"),
  "name": "Charmander",
  "attack": 60,
  "defense": 65,
  "height": 0.4,
  "attacks": [
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 12 record(s) in 6ms

```

06 - Pesquisar todos os pokemons que não são do tipo elétrico.
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {type:{ $not : /eletrico/i}
... }
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b7478eb4620a5d4ec2cb52"),
  "name": "Black Alien Mon",
  "description": "Pokemon da Rima",
  "attack": "250",
  "defense": "300",
  "height": 1.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74890b4620a5d4ec2cb53"),
  "name": "Bnegao",
  "description": "Pokemon pensador",
  "attack": "150",
  "defense": "400",
  "height": 1.1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74894b4620a5d4ec2cb54"),
  "name": "Marcelo D2",
  "description": "Pokemon Smoke Hard",
  "attack": "350",
  "defense": "500",
  "height": 1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74897b4620a5d4ec2cb55"),
  "name": "Formiga",
  "description": "Pokemon do Baixo",
  "attack": "50",
  "defense": "200",
  "height": 1.4,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74899b4620a5d4ec2cb56"),
  "name": "Pedrinho",
  "description": "Bateria psichodelica",
  "attack": "80",
  "defense": "220",
  "height": 1.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7489bb4620a5d4ec2cb57"),
  "name": "Speed Freaks",
  "description": "Pokemon Flow ou Levada",
  "attack": "500",
  "defense": 900,
  "height": 1.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7d127b4620a5d4ec2cb5c"),
  "description": "Pokemon de Teste",
  "name": "Testemon",
  "attack": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56b7dc4ded74435f14db2cc7"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7bbf7b4620a5d4ec2cb5b"),
  "name": "pikachu",
  "description": "poderes eletricos",
  "attack": 48,
  "defense": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false,
  "attacks": [
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda"
  ]
}
{
  "_id": ObjectId("56b7e2c9b4620a5d4ec2cb5d"),
  "name": "Squirtle",
  "attack": 55,
  "defense": 90,
  "height": 0.3,
  "attacks": [
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7e2cfb4620a5d4ec2cb5e"),
  "name": "Bulbassauro",
  "attack": 52,
  "defense": 85,
  "height": 0.4,
  "attacks": [
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7e2d5b4620a5d4ec2cb5f"),
  "name": "Charmander",
  "attack": 60,
  "defense": 65,
  "height": 0.4,
  "attacks": [
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda",
    "Pegar Visao da malandragem",
    "Dichavação profunda"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7e6cced74435f14db2cc8"),
  "name": "aindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "sem maiores informações"
}
Fetched 13 record(s) in 19ms

```

07 - Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = { $and: [{moves: {$in:['investida']}},{attack: {$not: {$lte:49}}} ]}
darkSide(mongod-2.6.3) be-mean-pokemons> query
{
  "$and": [
    {
      "moves": {
        "$in": [
          "investida"
        ]
      }
    },
    {
      "attack": {
        "$not": {
          "$lte": 49
        }
      }
    }
  ]
}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b7478eb4620a5d4ec2cb52"),
  "name": "Black Alien Mon",
  "description": "Pokemon da Rima",
  "attack": "250",
  "defense": "300",
  "height": 1.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74890b4620a5d4ec2cb53"),
  "name": "Bnegao",
  "description": "Pokemon pensador",
  "attack": "150",
  "defense": "400",
  "height": 1.1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74894b4620a5d4ec2cb54"),
  "name": "Marcelo D2",
  "description": "Pokemon Smoke Hard",
  "attack": "350",
  "defense": "500",
  "height": 1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74897b4620a5d4ec2cb55"),
  "name": "Formiga",
  "description": "Pokemon do Baixo",
  "attack": "50",
  "defense": "200",
  "height": 1.4,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b74899b4620a5d4ec2cb56"),
  "name": "Pedrinho",
  "description": "Bateria psichodelica",
  "attack": "80",
  "defense": "220",
  "height": 1.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7489bb4620a5d4ec2cb57"),
  "name": "Speed Freaks",
  "description": "Pokemon Flow ou Levada",
  "attack": "500",
  "defense": 900,
  "height": 1.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b7d127b4620a5d4ec2cb5c"),
  "description": "Pokemon de Teste",
  "name": "Testemon",
  "attack": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56b7dc4ded74435f14db2cc7"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 8 record(s) in 6ms

```

08 - Remova todos os pokemons do tipo água E com attack menor que 50.
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {$and: [ {name:/charmander/i},{attack:{$lte:100}}]}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 4ms
WriteResult({
  "nRemoved": 1
})

```
