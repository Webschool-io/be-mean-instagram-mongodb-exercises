# MongoDB - Aula 04 - Exercício
*autor:*[André Rocha](http://github.com/andrecgro)

## Adicionar dois ataques ao mesmo tempo para os seguintes pokemons:

 1. Pikachu
 2. Squirtle
 3. Bulbassauro
 4. Charmander

 ```
 be_mean_pokemons> var query =
 {
   "$or": [
     {
       "name": /Pikachu/i
     },
     {
       "name": /Squirtle/i
     },
     {
       "name": /Charmander/i
     },
     {
       "name": /Bulbassauro/i
     }
   ]
 }

 be_mean_pokemons> var mod = {$set: {moves: ['fugir','atacar']}}

 be_mean_pokemons> var options = {multi:true}

 be_mean_pokemons> db.be_mean_pokemons.update(query,mod,options)
 Updated 4 existing record(s) in 4ms
 WriteResult({
   "nMatched": 4,
   "nUpserted": 0,
   "nModified": 4
 })

 be_mean_pokemons> db.be_mean_pokemons.find(query)
 {
   "_id": ObjectId("5645567c3deed03ff449f06a"),
   "name": "Bulbassauro",
   "description": "Chicote de trepadeira",
   "type": "grama",
   "attack": 49,
   "height": 0.4,
   "active": false,
   "moves": [
     "fugir",
     "atacar"
   ]
 }
 {
   "_id": ObjectId("56453ff950f757b5fdb43fa5"),
   "name": "Pikachu",
   "description": "Rato mudo, elétrico e fofo",
   "type": "eletric",
   "attack": 55,
   "defense": 40,
   "height": 0.4,
   "moves": [
     "fugir",
     "atacar"
   ],
   "active": false
 }
 {
   "_id": ObjectId("5658babd5e73f5d606630e64"),
   "name": "Squirtle",
   "description": "Pequena tartaruga que nada muito rápido",
   "type": "água",
   "attack": 30,
   "defense": 30,
   "height": 0.5,
   "moves": [
     "fugir",
     "atacar"
   ],
   "active": false
 }
 {
   "_id": ObjectId("5658bc215e73f5d606630e65"),
   "name": "Charmander",
   "description": "A chama de sua cauda representa suas emoções",
   "type": "fire",
   "attack": 30,
   "defense": 20,
   "height": 0.6,
   "moves": [
     "fugir",
     "atacar"
   ],
   "active": false
 }
```

# Adicionar o movimento 'desvio' em todos os pokemons.

 ```
 be_mean_pokemons> var mod = {$push: {moves : 'desvio'}}

 be_mean_pokemons> var options = {upsert : true, multi : true}

 be_mean_pokemons> var query = {}

 be_mean_pokemons> db.be_mean_pokemons.update(query,mod,options)

 Updated 11 existing record(s) in 126ms
 WriteResult({
   "nMatched": 11,
   "nUpserted": 0,
   "nModified": 11
 })

 ```

 # Adicionar o pokemon ```AindaNãoExisteMon```, caso ele não exista, e inserir todos os campos como ```null```

 ```


  var query= {name: /AindaNãoExisteMon/i}
  var mod = {$setOnInsert:
    {
      name: 'AindaNãoExisteMon',
      description: 'Sem maiores informações',
      type: null,
      attack: null,
      defense: null,
      height: null,
      active: null
    }
  }
  var options = {upsert:true}

  be_mean_pokemons> db.be_mean_pokemons.update(query,mod,options)

  Updated 1 new record(s) in 51ms
  WriteResult({
    "nMatched": 0,
    "nUpserted": 1,
    "nModified": 0,
    "_id": ObjectId("565927015514f660ab2c57c4")
  })

  be_mean_pokemons> db.be_mean_pokemons.find(query)
    {
      "_id": ObjectId("565927015514f660ab2c57c4"),
      "name": "AindaNãoExisteMon",
      "description": "Sem maiores informações",
      "type": null,
      "attack": null,
      "defense": null,
      "height": null,
      "active": null
    }


 ```

# Pesquisar todos os pokemons que possuam o ataque investida e mais um pokemon que você adicionou

```
 be_mean_pokemons> var query = {moves : {$in: ['investida']}}

 be_mean_pokemons> db.be_mean_pokemons.find(query)
 {
   "_id": ObjectId("56453ed050f757b5fdb43fa0"),
   "name": "Charmeleon",
   "description": "Destrói tudo saporra",
   "type": "fire",
   "attack": 40,
   "defense": 40,
   "height": 1.1,
   "active": false,
   "moves": [
     "desvio",
     "investida"
   ]
 }
 {
   "_id": ObjectId("56453ed050f757b5fdb43fa1"),
   "name": "Charizard",
   "description": "Evolução da destruição",
   "type": "fire",
   "attack": 50,
   "defense": 40,
   "height": 1.7,
   "active": false,
   "moves": [
     "lança-chamas",
     "desvio",
     "investida"
   ]
 }
 {
   "_id": ObjectId("56453ed050f757b5fdb43fa2"),
   "name": "Magikarp",
   "description": "Peixe inútil",
   "type": "água",
   "attack": 10,
   "defense": 30,
   "height": 0.9,
   "active": false,
   "moves": [
     "desvio",
     "investida"
   ]
 }
 {
   "_id": ObjectId("56453ed050f757b5fdb43fa4"),
   "name": "Blastoise",
   "description": "Tartaruga canhão",
   "type": "água",
   "attack": 40,
   "defense": 40,
   "height": 1.6,
   "active": false,
   "moves": [
     "desvio",
     "investida"
   ]
 }
 {
   "_id": ObjectId("5645567c3deed03ff449f06a"),
   "name": "Bulbassauro",
   "description": "Chicote de trepadeira",
   "type": "grama",
   "attack": 49,
   "height": 0.4,
   "active": false,
   "moves": [
     "fugir",
     "atacar",
     "desvio",
     "investida"
   ]
 }
 {
   "_id": ObjectId("564b186430934f2732a11692"),
   "description": "Pokemon de teste",
   "name": "Testemon",
   "attack": 8000,
   "defense": 8000,
   "height": 2.1,
   "active": false,
   "moves": [
     "desvio",
     "investida"
   ]
 }
 {
   "_id": ObjectId("56453ff950f757b5fdb43fa5"),
   "name": "Pikachu",
   "description": "Rato mudo, elétrico e fofo",
   "type": "eletric",
   "attack": 55,
   "defense": 40,
   "height": 0.4,
   "moves": [
     "fugir",
     "atacar",
     "desvio",
     "investida"
   ],
   "active": false
 }
 {
   "_id": ObjectId("5658ac3e5514f660ab2c57c3"),
   "active": false,
   "name": "NaoExisteMon",
   "attack": null,
   "defense": null,
   "height": null,
   "description": "Sem maiores informações",
   "moves": [
     "desvio",
     "investida"
   ]
 }
 {
   "_id": ObjectId("56453ed050f757b5fdb43fa3"),
   "name": "Gyarados",
   "description": "Agora sim!",
   "type": "água e ainda avua saporra",
   "attack": 60,
   "defense": 30,
   "height": 6.5,
   "active": false,
   "moves": [
     "desvio",
     "ataque aéreo rápido",
     "investida"
   ]
 }
 {
   "_id": ObjectId("5658babd5e73f5d606630e64"),
   "name": "Squirtle",
   "description": "Pequena tartaruga que nada muito rápido",
   "type": "água",
   "attack": 30,
   "defense": 30,
   "height": 0.5,
   "moves": [
     "fugir",
     "atacar",
     "desvio",
     "investida"
   ],
   "active": false
 }
 {
   "_id": ObjectId("5658bc215e73f5d606630e65"),
   "name": "Charmander",
   "description": "A chama de sua cauda representa suas emoções",
   "type": "fire",
   "attack": 30,
   "defense": 20,
   "height": 0.6,
   "moves": [
     "fugir",
     "atacar",
     "desvio",
     "investida"
   ],
   "active": false
 }
 Fetched 11 record(s) in 105ms

```
# Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito

```
be_mean_pokemons> var query = {moves:{$in:['fugir','atacar']}}

be_mean_pokemons> db.be_mean_pokemons.find(query)

{
  "_id": ObjectId("5645567c3deed03ff449f06a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "fugir",
    "atacar",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("56453ff950f757b5fdb43fa5"),
  "name": "Pikachu",
  "description": "Rato mudo, elétrico e fofo",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "fugir",
    "atacar",
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("5658babd5e73f5d606630e64"),
  "name": "Squirtle",
  "description": "Pequena tartaruga que nada muito rápido",
  "type": "água",
  "attack": 30,
  "defense": 30,
  "height": 0.5,
  "moves": [
    "fugir",
    "atacar",
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("5658bc215e73f5d606630e65"),
  "name": "Charmander",
  "description": "A chama de sua cauda representa suas emoções",
  "type": "fire",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "moves": [
    "fugir",
    "atacar",
    "desvio",
    "investida"
  ],
  "active": false
}

```

# Pesquisar todos os pokemons que não são do tipo 'eletric'

```
be_mean_pokemons> var query = {type: {$ne: 'eletric'}}

db.be_mean_pokemons.find(query)
{
  "_id": ObjectId("56453ed050f757b5fdb43fa0"),
  "name": "Charmeleon",
  "description": "Destrói tudo saporra",
  "type": "fire",
  "attack": 40,
  "defense": 40,
  "height": 1.1,
  "active": false,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("56453ed050f757b5fdb43fa1"),
  "name": "Charizard",
  "description": "Evolução da destruição",
  "type": "fire",
  "attack": 50,
  "defense": 40,
  "height": 1.7,
  "active": false,
  "moves": [
    "lança-chamas",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("56453ed050f757b5fdb43fa2"),
  "name": "Magikarp",
  "description": "Peixe inútil",
  "type": "água",
  "attack": 10,
  "defense": 30,
  "height": 0.9,
  "active": false,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("56453ed050f757b5fdb43fa4"),
  "name": "Blastoise",
  "description": "Tartaruga canhão",
  "type": "água",
  "attack": 40,
  "defense": 40,
  "height": 1.6,
  "active": false,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5645567c3deed03ff449f06a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "fugir",
    "atacar",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564b186430934f2732a11692"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "active": false,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5658ac3e5514f660ab2c57c3"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("56453ed050f757b5fdb43fa3"),
  "name": "Gyarados",
  "description": "Agora sim!",
  "type": "água e ainda avua saporra",
  "attack": 60,
  "defense": 30,
  "height": 6.5,
  "active": false,
  "moves": [
    "desvio",
    "ataque aéreo rápido",
    "investida"
  ]
}
{
  "_id": ObjectId("5658babd5e73f5d606630e64"),
  "name": "Squirtle",
  "description": "Pequena tartaruga que nada muito rápido",
  "type": "água",
  "attack": 30,
  "defense": 30,
  "height": 0.5,
  "moves": [
    "fugir",
    "atacar",
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("5658bc215e73f5d606630e65"),
  "name": "Charmander",
  "description": "A chama de sua cauda representa suas emoções",
  "type": "fire",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "moves": [
    "fugir",
    "atacar",
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("565927015514f660ab2c57c4"),
  "name": "AindaNãoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "active": null
}
Fetched 11 record(s) in 6ms

```

# Pesquisar todos os pokemons que tenham o ataque 'investida' **E** a defesa menor que 49.

 ```
 be_mean_pokemons> var query ={ $and:[
    {defense: {$not: {$lte:49}}},
    {moves: {$in: ['investida']}}
 ]}
 be_mean_pokemons> db.be_mean_pokemons.find(query)
                   {
                     "_id": ObjectId("5645567c3deed03ff449f06a"),
                     "name": "Bulbassauro",
                     "description": "Chicote de trepadeira",
                     "type": "grama",
                     "attack": 49,
                     "height": 0.4,
                     "active": false,
                     "moves": [
                       "fugir",
                       "atacar",
                       "desvio",
                       "investida"
                     ]
                   }
                   {
                     "_id": ObjectId("564b186430934f2732a11692"),
                     "description": "Pokemon de teste",
                     "name": "Testemon",
                     "attack": 8000,
                     "defense": 8000,
                     "height": 2.1,
                     "active": false,
                     "moves": [
                       "desvio",
                       "investida"
                     ]
                   }
                   {
                     "_id": ObjectId("5658ac3e5514f660ab2c57c3"),
                     "active": false,
                     "name": "NaoExisteMon",
                     "attack": null,
                     "defense": null,
                     "height": null,
                     "description": "Sem maiores informações",
                     "moves": [
                       "desvio",
                       "investida"
                     ]
                   }
                   Fetched 3 record(s) in 3ms

 ```

 # Remova todos os pokemons do tipo 'água' e com ataque menor que 50.

 ```
  be_mean_pokemons> var query=
  {
    "$and": [
      {
        "attack": {
          "$lte": 50
        }
      },
      {
       "type": "água"
      }
    ]
  }

  be_mean_pokemons> db.be_mean_pokemons.remove(query)
  Removed 3 record(s) in 39ms
  WriteResult({
    "nRemoved": 3
  })


 ```