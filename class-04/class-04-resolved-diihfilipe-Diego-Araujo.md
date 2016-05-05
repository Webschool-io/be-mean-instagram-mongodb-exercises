####Adicionar 2 ataques aos pokemons Pikachu, Squirtle, Bulbassauro e Charmander ao mesmo tempo.
Zeus(mongod-3.0.7) be-mean-pokemons> var poke1 = name: /onix/i
2015-11-19T02:21:35.842-0200 E QUERY    SyntaxError: Unexpected token :
Zeus(mongod-3.0.7) be-mean-pokemons> var poke1 = {name: /onix/i}
Zeus(mongod-3.0.7) be-mean-pokemons> var poke2 = name: /blastoise/i
2015-11-19T02:21:54.690-0200 E QUERY    SyntaxError: Unexpected token :
Zeus(mongod-3.0.7) be-mean-pokemons> var poke2 = {name: /raticate/i}
Zeus(mongod-3.0.7) be-mean-pokemons> var poke3 = {name: /blastoise/i}
Zeus(mongod-3.0.7) be-mean-pokemons> var poke4 = {name: /butterfree/i}
Zeus(mongod-3.0.7) be-mean-pokemons> var query = {$and: [poke1, poke2, poke3, poke4]}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
Zeus(mongod-3.0.7) be-mean-pokemons> var query = {$or: [poke1, poke2, poke3, poke4]}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642b225db49f9570d8a5fb1"),
  "name": "Butterfree",
  "description": "Borboleta kawai kkkk",
  "type": "wind",
  "attack": 44,
  "defense": 44,
  "height": 3,
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("5642b281db49f9570d8a5fb2"),
  "name": "Blastoise",
  "description": "Tartaruga fodona com canhoes nas costas",
  "type": "water",
  "attack": 68,
  "defense": 63,
  "height": 7,
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("5642b301db49f9570d8a5fb4"),
  "name": "Raticate",
  "description": "Mestre Splinter antes da radiacao",
  "type": "normal",
  "attack": 44,
  "defense": 36,
  "height": 3,
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("5642b3a3db49f9570d8a5fb6"),
  "name": "Onix",
  "description": "Cobra de pedra",
  "type": "rock",
  "attack": 54,
  "defense": 76,
  "height": 6,
  "moves": [
    "investida"
  ]
}
Fetched 4 record(s) in 5ms
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 6ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642b225db49f9570d8a5fb1"),
  "name": "Butterfree",
  "description": "Borboleta kawai kkkk",
  "type": "wind",
  "attack": 44,
  "defense": 44,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai"
  ]
}
{
  "_id": ObjectId("5642b281db49f9570d8a5fb2"),
  "name": "Blastoise",
  "description": "Tartaruga fodona com canhoes nas costas",
  "type": "water",
  "attack": 68,
  "defense": 63,
  "height": 7,
  "moves": [
    "Soco na Cara",
    "Bankai"
  ]
}
{
  "_id": ObjectId("5642b301db49f9570d8a5fb4"),
  "name": "Raticate",
  "description": "Mestre Splinter antes da radiacao",
  "type": "normal",
  "attack": 44,
  "defense": 36,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai"
  ]
}
{
  "_id": ObjectId("5642b3a3db49f9570d8a5fb6"),
  "name": "Onix",
  "description": "Cobra de pedra",
  "type": "rock",
  "attack": 54,
  "defense": 76,
  "height": 6,
  "moves": [
    "Soco na Cara",
    "Bankai"
  ]
}
Fetched 4 record(s) in 5ms

######ahhhhhhh tremmmmm doidoooo =P


####Adicionar 1 movimento em todos pokemons ao mesmo tempo.

Zeus(mongod-3.0.7) be-mean-pokemons> var mod = {$push:{moves:['Soco na Cara', 'Bankai',]}}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 6 existing record(s) in 5ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642b225db49f9570d8a5fb1"),
  "name": "Butterfree",
  "description": "Borboleta kawai kkkk",
  "type": "wind",
  "attack": 44,
  "defense": 44,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ]
  ]
}
{
  "_id": ObjectId("5642b2dddb49f9570d8a5fb3"),
  "name": "Rattata",
  "description": "Apenas um rato",
  "type": "normal",
  "attack": 27,
  "defense": 30,
  "height": 2,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ]
  ]
}
{
  "_id": ObjectId("5642b33edb49f9570d8a5fb5"),
  "name": "Arbok",
  "description": "Serpente que fugiu do Eden",
  "type": "poison",
  "attack": 68,
  "defense": 64,
  "height": 6,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ]
  ]
}
{
  "_id": ObjectId("5642b3a3db49f9570d8a5fb6"),
  "name": "Onix",
  "description": "Cobra de pedra",
  "type": "rock",
  "attack": 54,
  "defense": 76,
  "height": 6,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ]
  ]
}
{
  "_id": ObjectId("5642b281db49f9570d8a5fb2"),
  "name": "Blastoise",
  "description": "Tartaruga fodona com canhoes nas costas",
  "type": "water",
  "attack": 68,
  "defense": 63,
  "height": 7,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ]
  ]
}
{
  "_id": ObjectId("5642b301db49f9570d8a5fb4"),
  "name": "Raticate",
  "description": "Mestre Splinter antes da radiacao",
  "type": "normal",
  "attack": 44,
  "defense": 36,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ]
  ]
}
Fetched 6 record(s) in 5ms
Zeus(mongod-3.0.7) be-mean-pokemons> var mod = {$remove:{moves:['Soco na Cara', 'Bankai',]}}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Unknown modifier: $remove
WriteResult({
  "nMatched": 0,
  "nUpserted": 0,
  "nModified": 0,
  "writeError": {
    "code": 9,
    "errmsg": "Unknown modifier: $remove"
  }
})
Zeus(mongod-3.0.7) be-mean-pokemons> var mod = {$push:{moves:['Pontape']}}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 6 existing record(s) in 6ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642b281db49f9570d8a5fb2"),
  "name": "Blastoise",
  "description": "Tartaruga fodona com canhoes nas costas",
  "type": "water",
  "attack": 68,
  "defense": 63,
  "height": 7,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b301db49f9570d8a5fb4"),
  "name": "Raticate",
  "description": "Mestre Splinter antes da radiacao",
  "type": "normal",
  "attack": 44,
  "defense": 36,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b225db49f9570d8a5fb1"),
  "name": "Butterfree",
  "description": "Borboleta kawai kkkk",
  "type": "wind",
  "attack": 44,
  "defense": 44,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b2dddb49f9570d8a5fb3"),
  "name": "Rattata",
  "description": "Apenas um rato",
  "type": "normal",
  "attack": 27,
  "defense": 30,
  "height": 2,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b33edb49f9570d8a5fb5"),
  "name": "Arbok",
  "description": "Serpente que fugiu do Eden",
  "type": "poison",
  "attack": 68,
  "defense": 64,
  "height": 6,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b3a3db49f9570d8a5fb6"),
  "name": "Onix",
  "description": "Cobra de pedra",
  "type": "rock",
  "attack": 54,
  "defense": 76,
  "height": 6,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
Fetched 6 record(s) in 17ms

###### fiz merda aqui e adicionei duas vezes os golpes anteriores porque dei um $set kkkkkkk um update sem where.

####Adicionar o pokemon 'AindaNaoExisteMon' caso ele ainda nao exista com os dados null e a descrição "Sem maiores informações".

Zeus(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
Zeus(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert: {name:"AindaNaoExisteMon", description: "Sem maiores informações", type:null, attack:null, defense:null, height:null, moves:null}}
Zeus(mongod-3.0.7) be-mean-pokemons> var options = {upsert:true}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564d52b1ce6211ffd6e7629c")
})
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564d52b1ce6211ffd6e7629c"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "moves": null
}
Fetched 1 record(s) in 2ms


####Pesquisar todos os pokemons que tenham ataque "investida" e mais um que voce adicionou

Zeus(mongod-3.0.7) be-mean-pokemons> var query1 = {moves: /investida/i}
Zeus(mongod-3.0.7) be-mean-pokemons> var query2 = {moves: /bankai/i}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$and: [query1, query2]})
Fetched 0 record(s) in 1ms

######No meu caso nao tem mas, ...

Zeus(mongod-3.0.7) be-mean-pokemons> var query1 = {moves: /bankai/i}
Zeus(mongod-3.0.7) be-mean-pokemons> var query2 = {moves: /soco na cara/i}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$and: [query1, query2]})
{
  "_id": ObjectId("5642b281db49f9570d8a5fb2"),
  "name": "Blastoise",
  "description": "Tartaruga fodona com canhoes nas costas",
  "type": "water",
  "attack": 68,
  "defense": 63,
  "height": 7,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b301db49f9570d8a5fb4"),
  "name": "Raticate",
  "description": "Mestre Splinter antes da radiacao",
  "type": "normal",
  "attack": 44,
  "defense": 36,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b225db49f9570d8a5fb1"),
  "name": "Butterfree",
  "description": "Borboleta kawai kkkk",
  "type": "wind",
  "attack": 44,
  "defense": 44,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b2dddb49f9570d8a5fb3"),
  "name": "Rattata",
  "description": "Apenas um rato",
  "type": "normal",
  "attack": 27,
  "defense": 30,
  "height": 2,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b33edb49f9570d8a5fb5"),
  "name": "Arbok",
  "description": "Serpente que fugiu do Eden",
  "type": "poison",
  "attack": 68,
  "defense": 64,
  "height": 6,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b3a3db49f9570d8a5fb6"),
  "name": "Onix",
  "description": "Cobra de pedra",
  "type": "rock",
  "attack": 54,
  "defense": 76,
  "height": 6,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
Fetched 6 record(s) in 7ms




####Pesquisar todos os pokemons que possuam ataques que você adicionou (a sua escolha).

Zeus(mongod-3.0.7) be-mean-pokemons> var query = {moves: /bankai/i}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642b281db49f9570d8a5fb2"),
  "name": "Blastoise",
  "description": "Tartaruga fodona com canhoes nas costas",
  "type": "water",
  "attack": 68,
  "defense": 63,
  "height": 7,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b301db49f9570d8a5fb4"),
  "name": "Raticate",
  "description": "Mestre Splinter antes da radiacao",
  "type": "normal",
  "attack": 44,
  "defense": 36,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b225db49f9570d8a5fb1"),
  "name": "Butterfree",
  "description": "Borboleta kawai kkkk",
  "type": "wind",
  "attack": 44,
  "defense": 44,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b2dddb49f9570d8a5fb3"),
  "name": "Rattata",
  "description": "Apenas um rato",
  "type": "normal",
  "attack": 27,
  "defense": 30,
  "height": 2,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b33edb49f9570d8a5fb5"),
  "name": "Arbok",
  "description": "Serpente que fugiu do Eden",
  "type": "poison",
  "attack": 68,
  "defense": 64,
  "height": 6,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b3a3db49f9570d8a5fb6"),
  "name": "Onix",
  "description": "Cobra de pedra",
  "type": "rock",
  "attack": 54,
  "defense": 76,
  "height": 6,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
Fetched 6 record(s) in 6ms

####Pesquisar todos os pokemons do tipo eletrico

Zeus(mongod-3.0.7) be-mean-pokemons> var query = {type: /eletric/i}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

######No meu caso nao tem, mas...

Zeus(mongod-3.0.7) be-mean-pokemons> var query = {type: /normal/i}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642b301db49f9570d8a5fb4"),
  "name": "Raticate",
  "description": "Mestre Splinter antes da radiacao",
  "type": "normal",
  "attack": 44,
  "defense": 36,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b2dddb49f9570d8a5fb3"),
  "name": "Rattata",
  "description": "Apenas um rato",
  "type": "normal",
  "attack": 27,
  "defense": 30,
  "height": 2,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
Fetched 2 record(s) in 5ms

####Pesquisar todos os pokemons que tenham ataque "investida" E tenham a defesa NÃO menor ou igual a 49.
Zeus(mongod-3.0.7) be-mean-pokemons> var query1 = {moves: /investida/i}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$and: [query1, query2]})
Fetched 0 record(s) in 2ms

######nao coloquei ninguem com investida, mas ...
Zeus(mongod-3.0.7) be-mean-pokemons> var query1 = {moves: /bankai/i}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$and: [query1, query2]})
{
  "_id": ObjectId("5642b281db49f9570d8a5fb2"),
  "name": "Blastoise",
  "description": "Tartaruga fodona com canhoes nas costas",
  "type": "water",
  "attack": 68,
  "defense": 63,
  "height": 7,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b301db49f9570d8a5fb4"),
  "name": "Raticate",
  "description": "Mestre Splinter antes da radiacao",
  "type": "normal",
  "attack": 44,
  "defense": 36,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b225db49f9570d8a5fb1"),
  "name": "Butterfree",
  "description": "Borboleta kawai kkkk",
  "type": "wind",
  "attack": 44,
  "defense": 44,
  "height": 3,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b2dddb49f9570d8a5fb3"),
  "name": "Rattata",
  "description": "Apenas um rato",
  "type": "normal",
  "attack": 27,
  "defense": 30,
  "height": 2,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b33edb49f9570d8a5fb5"),
  "name": "Arbok",
  "description": "Serpente que fugiu do Eden",
  "type": "poison",
  "attack": 68,
  "defense": 64,
  "height": 6,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
{
  "_id": ObjectId("5642b3a3db49f9570d8a5fb6"),
  "name": "Onix",
  "description": "Cobra de pedra",
  "type": "rock",
  "attack": 54,
  "defense": 76,
  "height": 6,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}
Fetched 6 record(s) in 5ms



####Remova todos os pokemons tipo agua e com attack menor que 50.

Zeus(mongod-3.0.7) be-mean-pokemons> var query1 = {type: /water/i}
Zeus(mongod-3.0.7) be-mean-pokemons> var query2 = {attack: {$lt:50}}
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.delete({$and: [query1, query2]})
2015-11-19T03:03:29.183-0200 E QUERY    TypeError: Property 'delete' of object be-mean-pokemons.pokemons is not a function
    at (shell):1:19
Zeus(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove({$and: [query1, query2]})
Removed 0 record(s) in 5ms
WriteResult({
  "nRemoved": 0
})


######Vacilando na query achando que e mysql, meu pokemon agua blastoise tem attack maior que 50

{
  "_id": ObjectId("5642b281db49f9570d8a5fb2"),
  "name": "Blastoise",
  "description": "Tartaruga fodona com canhoes nas costas",
  "type": "water",
  "attack": 68,
  "defense": 63,
  "height": 7,
  "moves": [
    "Soco na Cara",
    "Bankai",
    [
      "Soco na Cara",
      "Bankai"
    ],
    [
      "Pontape"
    ]
  ]
}

