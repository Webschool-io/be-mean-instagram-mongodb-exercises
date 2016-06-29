# MongoDB - Aula 02 - Exercício
autor: Vitor Capretz

# Crie uma database chamada be-mean-pokemons
```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean> use be-mean-pokemons
switched to db be-mean-pokemons
```

# Liste quais databases você possui nesse servidor
```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> show dbs
admin             → (empty)
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
local             → 0.078GB
teste             → (empty)
```

# Liste quais coleções você possui nessa database
```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> show collections
```

# Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height
```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons>var multi_pokemons = [
	{name: "Bulbassauro", description: "aquele verde", type: "Grama", attack: 49, defense: 49, height: 0.4}, 
	{name: "Charmander", description: "o que vira o charizard (fodelao)", type: "Fogo", attack: 52, defense: 43, height: 0.6},
	{name: "Squirtle", description: "esse evoluido tbm eh massa", type: "Água", attack: 48, defense: 65, height: 0.5},
	{name: "Pikachu", description: "o de poser", type: "Elétrico", attack: 55, defense: 40, height: 0.41},
	{name: "Jigglypuff", description: "prof da aula de historia", type: "Fada", attack: 45, defense: 40, height: 0.51},
]
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(multi_pokemons)
Inserted 1 record(s) in 345ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})

```

# Liste os pokemons existentes na sua coleção
```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57476d07361178273f8391d8"),
  "name": "Bulbassauro",
  "description": "aquele verde",
  "type": "Grama",
  "attack": 49,
  "defense": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57476d07361178273f8391d9"),
  "name": "Charmander",
  "description": "o que vira o charizard (fodelao)",
  "type": "Fogo",
  "attack": 52,
  "defense": 43,
  "height": 0.6
}
{
  "_id": ObjectId("57476d07361178273f8391da"),
  "name": "Squirtle",
  "description": "esse evoluido tbm eh massa",
  "type": "Água",
  "attack": 48,
  "defense": 65,
  "height": 0.5
}
{
  "_id": ObjectId("57476d07361178273f8391db"),
  "name": "Pikachu",
  "description": "o de poser",
  "type": "Elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
{
  "_id": ObjectId("57476d07361178273f8391dc"),
  "name": "Jigglypuff",
  "description": "prof da aula de historia",
  "type": "Fada",
  "attack": 45,
  "defense": 40,
  "height": 0.51
}
Fetched 5 record(s) in 2ms
```

# Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`
```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> var poke = db.pokemons.findOne({name: "Pikachu"})
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> poke
{
  "_id": ObjectId("57476d07361178273f8391db"),
  "name": "Pikachu",
  "description": "o de poser",
  "type": "Elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
```

# Modifique sua `description` e salvê-o
```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> poke.description = "pokemon de poser"
pokemon de poser
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
