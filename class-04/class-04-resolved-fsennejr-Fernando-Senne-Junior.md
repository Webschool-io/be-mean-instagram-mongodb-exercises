##1 - adicionar *** 2 ataques ao mesmo tempo para os seguintes pokemons: PIKACHU, SQUIRTLE, BULBASSAURO E CHARMANDER.
```
> var query = {$or: [{name: 'Pikachu'}, {name: 'Squirtle'}, {name:'Bulbassauro'}, {name: 'Charmander'}]}
> var mod = {$pushAll: {moves:["ataque strong", "ataque de raio"]}}
> var option = {multi: true}
> db.pokemons.update(query, mod, option)
Updated 1 existing record(s) in 97ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

```
> db.pokemons.find(query)
{
  "_id": ObjectId("58b4a420f5080f1ee3f50188"),
  "name": "Pikachu",
  "description": "Choque",
  "type": "elétrico",
  "attack": 9000,
  "defense": 9000,
  "height": 9.1,
  "moves": [
    "investida",
    "choque do trovão",
    "ataque strong",
    "ataque de raio"
  ],
  "active": false
}
Fetched 1 record(s) in 14ms
```



##2 - adicionar *** 1 movimento em todos os pokemons: "desvio"
```
> var query = {}
> var mod = {$set: {moves: ['desvio rapido']}}
> var option = {multi: true}
> db.pokemons.update(query, mod, option)
Updated 9 existing record(s) in 3ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})
```

```
> db.pokemons.find()
{
  "_id": ObjectId("58b45b07be365e7ac9eb7c00"),
  "name": "Blastoise",
  "description": "atira balas de agua",
  "type": "água",
  "attack": 48,
  "defense": "cria um escudo de agua",
  "height": 0.5,
  "active": false,
  "moves": [
    "desvio rapido"
  ]
}
{
  "_id": ObjectId("58b45baebe365e7ac9eb7c01"),
  "name": "Butterfree",
  "description": "atira flores",
  "type": "voa",
  "attack": 59,
  "defense": "paralisa o oponente",
  "height": 0.7,
  "active": false,
  "moves": [
    "desvio rapido"
  ]
}
{
  "_id": ObjectId("58b45c4fbe365e7ac9eb7c02"),
  "name": "Arbok",
  "description": "picada venenosa",
  "type": "rastejante",
  "attack": 79,
  "defense": "espiral de aço",
  "height": 0.8,
  "active": false,
  "moves": [
    "desvio rapido"
  ]
}
{
  "_id": ObjectId("58b45cbebe365e7ac9eb7c03"),
  "name": "Beedrill",
  "description": "ataca em conjunto com seu enxame mortal",
  "type": "voa",
  "attack": 95,
  "defense": "escudo de abelhas",
  "height": 0.11,
  "active": false,
  "moves": [
    "desvio rapido"
  ]
}
{
  "_id": ObjectId("58b45d56be365e7ac9eb7c04"),
  "name": "Arcanine",
  "description": "super veloz",
  "type": "tipo atlético",
  "attack": 100,
  "defense": "fulga ultra rápida",
  "height": 0.11,
  "active": false,
  "moves": [
    "desvio rapido"
  ]
}
{
  "_id": ObjectId("58b49e19f5080f1ee3f50187"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "desvio rapido"
  ]
}
{
  "_id": ObjectId("58b4a420f5080f1ee3f50188"),
  "name": "Pikachu",
  "description": "Choque",
  "type": "elétrico",
  "attack": 9000,
  "defense": 9000,
  "height": 9.1,
  "moves": [
    "desvio rapido"
  ],
  "active": false
}
{
  "_id": ObjectId("58b4ae2840b88b9835bccc1b"),
  "active": false,
  "moves": [
    "desvio rapido"
  ]
}
{
  "_id": ObjectId("58b80fd98e88fab06253741a"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "type": null,
  "height": null,
  "description": "Sem Maiores Informações",
  "moves": [
    "desvio rapido"
  ]
}
Fetched 9 record(s) in 92ms
```





##3 - adicionar *** o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição: 'sem maiores informações'
```
> query
{
  "name": /AindaNaoExisteMon/i
}
> var mod = {$setOnInsert: {name:"AindaNaoExisteMon", attack: null, defense: null, type: null, height: null, description: "Sem Maiores Informações"}}
> var option = {upsert: true}
> db.pokemons.update(query, mod, option)
Updated 1 new record(s) in 180ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("58b80fd98e88fab06253741a")
})
> db.pokemons.find(query)
{
  "_id": ObjectId("58b80fd98e88fab06253741a"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "type": null,
  "height": null,
  "description": "Sem Maiores Informações"
}
Fetched 1 record(s) in 10ms

```





##4 Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.
```
> var poke = {name: "GaviaonNon", type: 'fogo', attack: 99, defense:'bate asa', description:'Ave de rapina', moves:['voo rapido'], height:1.5, active: true}

> db.pokemons.insert(poke)
Inserted 1 record(s) in 45ms
WriteResult({
  "nInserted": 1
})

> var query = {$or:[ {moves:['investida']}, {name:"GaviaonNon"}]}
> db.pokemons.find(query)
{
  "_id": ObjectId("58b4a420f5080f1ee3f50188"),
  "name": "Pikachu",
  "description": "Choque",
  "type": "elétrico",
  "attack": 9000,
  "defense": 9000,
  "height": 9.1,
  "moves": [
    "desvio rapido",
    [
      "investida"
    ],
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ]
  ],
  "active": false
}
{
  "_id": ObjectId("58b81724e8f1c143edceacbd"),
  "name": "GaviaonNon",
  "type": "fogo",
  "attack": 99,
  "defense": "bate asa",
  "description": "Ave de rapina",
  "moves": [
    "voo rapido"
  ],
  "height": 1.5,
  "active": true
}
Fetched 2 record(s) in 27ms
```



##5 pesquisar "todos" os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
> var query = {}
> var mod = {$pushAll:{moves:['bater']}}
> var option = {multi:true}
> db.pokemons.update(query, mod, option)
Updated 10 existing record(s) in 3ms
WriteResult({
  "nMatched": 10,
  "nUpserted": 0,
  "nModified": 10
})

> var query = {$or:[{name:"Arbok"}, {moves:'bater'}]}
> db.pokemons.find(query)
{
  "_id": ObjectId("58b45b07be365e7ac9eb7c00"),
  "name": "Blastoise",
  "description": "atira balas de agua",
  "type": "água",
  "attack": 48,
  "defense": "cria um escudo de agua",
  "height": 0.5,
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b45baebe365e7ac9eb7c01"),
  "name": "Butterfree",
  "description": "atira flores",
  "type": "voa",
  "attack": 59,
  "defense": "paralisa o oponente",
  "height": 0.7,
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b45c4fbe365e7ac9eb7c02"),
  "name": "Arbok",
  "description": "picada venenosa",
  "type": "rastejante",
  "attack": 79,
  "defense": "espiral de aço",
  "height": 0.8,
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b45cbebe365e7ac9eb7c03"),
  "name": "Beedrill",
  "description": "ataca em conjunto com seu enxame mortal",
  "type": "voa",
  "attack": 95,
  "defense": "escudo de abelhas",
  "height": 0.11,
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b45d56be365e7ac9eb7c04"),
  "name": "Arcanine",
  "description": "super veloz",
  "type": "tipo atlético",
  "attack": 100,
  "defense": "fulga ultra rápida",
  "height": 0.11,
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b49e19f5080f1ee3f50187"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b4a420f5080f1ee3f50188"),
  "name": "Pikachu",
  "description": "Choque",
  "type": "elétrico",
  "attack": 9000,
  "defense": 9000,
  "height": 9.1,
  "moves": [
    "desvio rapido",
    [
      "investida"
    ],
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ],
  "active": false
}
{
  "_id": ObjectId("58b4ae2840b88b9835bccc1b"),
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b80fd98e88fab06253741a"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "type": null,
  "height": null,
  "description": "Sem Maiores Informações",
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b81724e8f1c143edceacbd"),
  "name": "GaviaonNon",
  "type": "fogo",
  "attack": 99,
  "defense": "bate asa",
  "description": "Ave de rapina",
  "moves": [
    "voo rapido",
    "bater"
  ],
  "height": 1.5,
  "active": true
}
Fetched 10 record(s) in 181ms
```


##6 pesquisar "todos" que não são do tipo "elétrico".
```
> var query = {type: {$not: /eletrico/i}}
> db.pokemons.find(query)
{
  "_id": ObjectId("58b45b07be365e7ac9eb7c00"),
  "name": "Blastoise",
  "description": "atira balas de agua",
  "type": "água",
  "attack": 48,
  "defense": "cria um escudo de agua",
  "height": 0.5,
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b45baebe365e7ac9eb7c01"),
  "name": "Butterfree",
  "description": "atira flores",
  "type": "voa",
  "attack": 59,
  "defense": "paralisa o oponente",
  "height": 0.7,
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b45c4fbe365e7ac9eb7c02"),
  "name": "Arbok",
  "description": "picada venenosa",
  "type": "rastejante",
  "attack": 79,
  "defense": "espiral de aço",
  "height": 0.8,
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b45cbebe365e7ac9eb7c03"),
  "name": "Beedrill",
  "description": "ataca em conjunto com seu enxame mortal",
  "type": "voa",
  "attack": 95,
  "defense": "escudo de abelhas",
  "height": 0.11,
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b45d56be365e7ac9eb7c04"),
  "name": "Arcanine",
  "description": "super veloz",
  "type": "tipo atlético",
  "attack": 100,
  "defense": "fulga ultra rápida",
  "height": 0.11,
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b49e19f5080f1ee3f50187"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b4a420f5080f1ee3f50188"),
  "name": "Pikachu",
  "description": "Choque",
  "type": "elétrico",
  "attack": 9000,
  "defense": 9000,
  "height": 9.1,
  "moves": [
    "desvio rapido",
    [
      "investida"
    ],
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ],
  "active": false
}
{
  "_id": ObjectId("58b4ae2840b88b9835bccc1b"),
  "active": false,
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b80fd98e88fab06253741a"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "type": null,
  "height": null,
  "description": "Sem Maiores Informações",
  "moves": [
    "desvio rapido",
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ]
}
{
  "_id": ObjectId("58b81724e8f1c143edceacbd"),
  "name": "GaviaonNon",
  "type": "fogo",
  "attack": 99,
  "defense": "bate asa",
  "description": "Ave de rapina",
  "moves": [
    "voo rapido",
    "bater"
  ],
  "height": 1.5,
  "active": true
}
Fetched 10 record(s) in 178ms
```


##7 pesquisar todos pokemons que tenham o ataque 'investida' ***E*** tenham a defesa ***Não menor ou igual*** a 49.
```
> var query =  {$and:[{moves:['investida']}, {defense:{$gte:49}}]}
> db.pokemons.find(query)
{
  "_id": ObjectId("58b4a420f5080f1ee3f50188"),
  "name": "Pikachu",
  "description": "Choque",
  "type": "elétrico",
  "attack": 9000,
  "defense": 9000,
  "height": 9.1,
  "moves": [
    "desvio rapido",
    [
      "investida"
    ],
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ],
  "active": false
}
Fetched 1 record(s) in 10ms

> var query =  {$and:[{moves:['investida']}, {defense:{$not:{$lte:49}}}]}
> db.pokemons.find(query)
{
  "_id": ObjectId("58b4a420f5080f1ee3f50188"),
  "name": "Pikachu",
  "description": "Choque",
  "type": "elétrico",
  "attack": 9000,
  "defense": 9000,
  "height": 9.1,
  "moves": [
    "desvio rapido",
    [
      "investida"
    ],
    "super fast",
    [
      "investida",
      "soco forte",
      "desvio rapido"
    ],
    "bater"
  ],
  "active": false
}
```

##8 Remova ***todos*** os pokemons do tipo água e com o attack menor que 50.
```

> var query = {$and:[{type:'agua'}, {attack:{$lt:50}}]}
> query
{
  "$and": [
    {
      "type": "agua"
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}
> db.pokemons.remove(query)
Removed 0 record(s) in 65ms
WriteResult({
  "nRemoved": 0
})
```