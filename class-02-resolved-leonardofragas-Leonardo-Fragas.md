###MongoDB - Aula 02 - Exercício
Autor: Leonardo Fragas

##Criando database
```
fragas@fragas-VirtualBox ~ % mongo be-mean-instagram
MongoDB shell version: 3.2.7
connecting to: be-mean-instagram
Mongo-Hacker 0.0.13
```

##Listando databases
```
fragas-VirtualBox(mongod-3.2.7) be-mean-instagram> show dbs
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
local             → 0.000GB
meannn            → 0.000GB
```

##Listando collections
```
fragas-VirtualBox(mongod-3.2.7) be-mean-instagram> show collections
pokemons → 0.001MB / 0.035MB
```

##Cadastro de pokemons
```
fragas-VirtualBox(mongod-3.2.7) be-mean-instagram> pokemons
[
  {
    "name": "Blastoise",
    "description": "Pode atirar bolas de água",
    "type": "água",
    "attack": 40,
    "defense": 40,
    "height": 1.6
  },
  {
    "name": "Wartortle",
    "description": "A cauda desse bicho fica mais preta com a idade",
    "type": "água",
    "attack": 30,
    "defense": 40,
    "height": 1
  },
  {
    "name": "Metapod",
    "description": "Ele não se move muito, sabe...",
    "type": "inseto",
    "attack": 10,
    "defense": 30,
    "height": 0.7
  },
  {
    "name": "Butterfree",
    "description": "Ele busca docinho nas frô",
    "type": "inseto",
    "attack": 20,
    "defense": 20,
    "height": 1.1
  },
  {
    "name": "Weedle",
    "description": "Tem um olfato muito bom porque é da terra esse bichão",
    "type": "inseto",
    "attack": 20,
    "defense": 20,
    "height": 0.3
  }
]
fragas-VirtualBox(mongod-3.2.7) be-mean-instagram> db.pokemons.save(pokemons)
Inserted 1 record(s) in 119ms
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
fragas-VirtualBox(mongod-3.2.7) be-mean-instagram> db.pokemons.find()
{
  "_id": ObjectId("57855ec2af50de0e5871490a"),
  "name": "Pikachu",
  "description": "Rato elétrico do capeta",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("57855f30af50de0e5871490b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57855f60af50de0e5871490c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("57855f81af50de0e5871490d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("578561a27dd5434d073b6df7"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
{
  "_id": ObjectId("57856dbe1a4929b3e6aabf20"),
  "name": "Blastoise",
  "description": "Pode atirar bolas de água",
  "type": "água",
  "attack": 40,
  "defense": 40,
  "height": 1.6
}
{
  "_id": ObjectId("57856dbe1a4929b3e6aabf21"),
  "name": "Wartortle",
  "description": "A cauda desse bicho fica mais preta com a idade",
  "type": "água",
  "attack": 30,
  "defense": 40,
  "height": 1
}
{
  "_id": ObjectId("57856dbe1a4929b3e6aabf22"),
  "name": "Metapod",
  "description": "Ele não se move muito, sabe...",
  "type": "inseto",
  "attack": 10,
  "defense": 30,
  "height": 0.7
}
{
  "_id": ObjectId("57856dbe1a4929b3e6aabf23"),
  "name": "Butterfree",
  "description": "Ele busca docinho nas frô",
  "type": "inseto",
  "attack": 20,
  "defense": 20,
  "height": 1.1
}
{
  "_id": ObjectId("57856dbe1a4929b3e6aabf24"),
  "name": "Weedle",
  "description": "Tem um olfato muito bom porque é da terra esse bichão",
  "type": "inseto",
  "attack": 20,
  "defense": 20,
  "height": 0.3
}
Fetched 10 record(s) in 7ms
```

##Pokemon
```
fragas-VirtualBox(mongod-3.2.7) be-mean-instagram> var query = {name: "Weedle"}
fragas-VirtualBox(mongod-3.2.7) be-mean-instagram> var poke = db.pokemons.findOne(query)
fragas-VirtualBox(mongod-3.2.7) be-mean-instagram> poke
{
  "_id": ObjectId("57856dbe1a4929b3e6aabf24"),
  "name": "Weedle",
  "description": "Tem um olfato muito bom porque é da terra esse bichão",
  "type": "inseto",
  "attack": 20,
  "defense": 20,
  "height": 0.3
}
```

##Atualização do Pokemon
```
fragas-VirtualBox(mongod-3.2.7) be-mean-instagram> poke.description
Tem um olfato muito bom porque é da terra esse bichão
fragas-VirtualBox(mongod-3.2.7) be-mean-instagram> poke.description = "não cara como cê é burro descreveu errado"
não cara como cê é burro descreveu errado
fragas-VirtualBox(mongod-3.2.7) be-mean-instagram> db.pokemons.save(poke)
Updated 1 existing record(s) in 208ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
fragas-VirtualBox(mongod-3.2.7) be-mean-instagram> poke
{
  "_id": ObjectId("57856dbe1a4929b3e6aabf24"),
  "name": "Weedle",
  "description": "não cara como cê é burro descreveu errado",
  "type": "inseto",
  "attack": 20,
  "defense": 20,
  "height": 0.3
}
```
