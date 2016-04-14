###MongoDB - Aula 02 - Exercício
Autor: Wagner Dlugosz Donato

##Criando database
```
donato-dell(mongod-3.2.4) test> use be-mean-pokemons
switched to db be-mean-pokemons
```

##Listando databases
```
donato-dell(mongod-3.2.4) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
local             → 0.078GB
```

##Listando collections
```
donato-dell(mongod-3.2.4) be-mean-pokemons> show collections
donato-dell(mongod-3.2.4) be-mean-pokemons> 
```

##Cadastro de pokemons
```

var pokemons = [{'name':'Blastoise','description': 'Tem bicas de água que se projetam de sua concha','type':'Water', attack: 75 , height: 1.6 },{'name':'Wurmple','description': 'Descasca a casca das árvores e se alimenta de seiva que escorre para fora','type':'Bug', attack: 35 , height: 0.3 },{'name':'Zigzagoon','description': 'Inquieto vagueia em todos os lugares em todos os momentos','type':'Normal', attack: 45 , height: 0.4 },{'name':'Raicu','description':'Raichu plantas a cauda no chão e descargas','type':'Electric', attack: 55 , height: 0.8 },{'name':'Arbok','description':'Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo','type':'Poison', attack: 65 , height: 3.5 }]

donato-dell(mongod-3.2.4) be-mean-pokemons> pokemons
[
  {
    "name": "Blastoise",
    "description": "Tem bicas de água que se projetam de sua concha",
    "type": "Water",
    "attack": 75,
    "height": 1.6
  },
  {
    "name": "Wurmple",
    "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
    "type": "Bug",
    "attack": 35,
    "height": 0.3
  },
  {
    "name": "Zigzagoon",
    "description": "Inquieto vagueia em todos os lugares em todos os momentos",
    "type": "Normal",
    "attack": 45,
    "height": 0.4
  },
  {
    "name": "Raicu",
    "description": "Raichu plantas a cauda no chão e descargas",
    "type": "Electric",
    "attack": 55,
    "height": 0.8
  },
  {
    "name": "Arbok",
    "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
    "type": "Poison",
    "attack": 65,
    "height": 3.5
  }
]

donato-dell(mongod-3.2.4) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 1ms
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

##Lista dos pokemons
```
donato-dell(mongod-3.2.4) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("570ea5d0f5ba6e1deb4e4849"),
  "name": "Blastoise",
  "description": "Tem bicas de água que se projetam de sua concha",
  "type": "Water",
  "attack": 75,
  "height": 1.6
}
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484a"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484b"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484c"),
  "name": "Raicu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
{
  "_id": ObjectId("570ea670f5ba6e1deb4e484d"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5
}
{
  "_id": ObjectId("570ea7d5f5ba6e1deb4e484e"),
  "name": "Blastoise",
  "description": "Tem bicas de água que se projetam de sua concha",
  "type": "Water",
  "attack": 75,
  "height": 1.6
}
{
  "_id": ObjectId("570ea807f5ba6e1deb4e484f"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
{
  "_id": ObjectId("570ea89bf5ba6e1deb4e4850"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4851"),
  "name": "Blastoise",
  "description": "Tem bicas de água que se projetam de sua concha",
  "type": "Water",
  "attack": 75,
  "height": 1.6
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4852"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4853"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4854"),
  "name": "Raicu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4855"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5
}
Fetched 13 record(s) in 7ms

```

##Pokemon
```
donato-dell(mongod-3.2.4) be-mean-pokemons> var query ={"name": "Raicu"}
donato-dell(mongod-3.2.4) be-mean-pokemons> var poke = db.pokemons.findOne(query)
donato-dell(mongod-3.2.4) be-mean-pokemons> poke
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484c"),
  "name": "Raicu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}


```

##Atualização do Pokemon
```
donato-dell(mongod-3.2.4) be-mean-pokemons> poke.description
Raichu plantas a cauda no chão e descargas
donato-dell(mongod-3.2.4) be-mean-pokemons> poke.description = "não é nada disso"
não é nada disso
donato-dell(mongod-3.2.4) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
donato-dell(mongod-3.2.4) be-mean-pokemons> poke
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484c"),
  "name": "Raicu",
  "description": "não é nada disso",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}

```
