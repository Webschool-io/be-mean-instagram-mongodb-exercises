###MongoDB - Aula 02 - Exercício
Autor: Vinícius Dutra

##Criando database
```
vinicius@vinicius:~/Documentos/be-mean$ mongo be-mean-pokemons
MongoDB shell version: 2.6.11
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.14
```

##Listando databases
```
vinicius(mongod-2.6.11) mongo be-mean-pokemons> show dbs
admin   → (empty)
be-mean → 0.078GB
local   → 0.078GB
test    → 0.078GB
       
```

##Listando collections
```
vinicius(mongod-2.6.11) be-mean-pokemons> show collections
vinicius(mongod-2.6.11) be-mean-pokemons> 

```

##Cadastro de pokemons
```
vinicius(mongod-2.6.11) be-mean-pokemons> poke =  [{name: "Blastoise", description: "tartaruga gigante com canhões de água nas costas", attack: 45, defense: 43, height: 1.6}, {name: "Butterfree", description: "Borboleta feiosa pra krlho", attack: 17, defense: 13, height: 1.1}, {name: "Beedrill", description: "Abelha com finco nas mãos", attack: 51, defense: 16, height: 1.0}, {name: "Charizard", description: "Dragão teimoso", attack: 42, defense: 34, height: 1.7}, {name: "Ekans", description: "Cobrinha roxa (tô fora...)", attack: 31, defense: 28, height: 2.0}]

vinicius(mongod-2.6.11) be-mean-pokemons> for (var i = 0;i < poke.length; i++ ){db.pokemons.insert(poke[i])}
Inserted 1 record(s) in 76ms
Inserted 1 record(s) in 1ms
Inserted 1 record(s) in 1ms
Inserted 1 record(s) in 1ms
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

```

##Lista dos pokemons
```
vinicius(mongod-2.6.11) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("58967e5e922ca46a0a4d0720"),
  "name": "Blastoise",
  "description": "tartaruga gigante com canhões de água nas costas",
  "attack": 45,
  "defense": 43,
  "height": 1.6
}
{
  "_id": ObjectId("58967e5e922ca46a0a4d0721"),
  "name": "Butterfree",
  "description": "Borboleta feiosa pra krlho",
  "attack": 17,
  "defense": 13,
  "height": 1.1
}
{
  "_id": ObjectId("58967e5e922ca46a0a4d0722"),
  "name": "Beedrill",
  "description": "Abelha com finco nas mãos",
  "attack": 51,
  "defense": 16,
  "height": 1
}
{
  "_id": ObjectId("58967e5e922ca46a0a4d0723"),
  "name": "Charizard",
  "description": "Dragão teimoso",
  "attack": 42,
  "defense": 34,
  "height": 1.7
}
{
  "_id": ObjectId("58967e5e922ca46a0a4d0724"),
  "name": "Ekans",
  "description": "Cobrinha roxa (tô fora...)",
  "attack": 31,
  "defense": 28,
  "height": 2
}
Fetched 5 record(s) in 2ms
```

##Pokemon
```
vinicius(mongod-2.6.11) be-mean-pokemons> var query = {name: /ekans/i}
vinicius(mongod-2.6.11) be-mean-pokemons> poke = db.pokemons.findOne(query)
{
  "_id": ObjectId("58967e5e922ca46a0a4d0724"),
  "name": "Ekans",
  "description": "Cobrinha roxa (tô fora...)",
  "attack": 31,
  "defense": 28,
  "height": 2
}
```

##Atualização do Pokemon
```
vinicius(mongod-2.6.11) be-mean-pokemons> poke.description = "Cobra roxa dusinfernu"
Cobra roxa dusinfernu
vinicius(mongod-2.6.11) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 8ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
