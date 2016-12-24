## MongoDb - Aula 02
autor: Fernando Lucas Gontijo

Continuando nossa a aula sobre MongoDb, continuaremos utilizando o `Terminal` e faremos as primeiras funções do nosso CRUD.

O [CRUD](https://pt.wikipedia.org/wiki/CRUD) é uma silga que significa as 4 operações básicas que qualquer entidade deve ter, para ser gerenciável, em um sistema:

- Create: cria uma entidade nova;
- Retrieve/Read: busca uma entidade existente;
- Update: modifica uma entidade existente;
- Delete: excluí uma entidade existente.

Nessa aula aprenderemos como criar e buscar nossos registros.


Falar que qnd subir o `mongod` pode subir escolhendo qual database irá usar, executando assim:

### Subir escolhendo qual database (Passo 1)

```
➜  fernando git:(master) ✗ mongo use-be-mean-pokemons 
MongoDB shell version: 3.2.6
connecting to: use-be-mean-pokemons
Mongo-Hacker 0.0.13
Server has startup warnings: 
2016-05-07T00:03:41.190-0300 I CONTROL  [initandlisten] 
2016-05-07T00:03:41.190-0300 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/defrag is 'always'.
2016-05-07T00:03:41.190-0300 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2016-05-07T00:03:41.190-0300 I CONTROL  [initandlisten] 
fernando(mongod-3.2.6) use-be-mean-pokemons> 
```

### Listagem das databases (passo 2)
```
fernando(mongod-3.2.6) test> use be-mean-pokemons
switched to db be-mean-pokemons

fernando(mongod-3.2.6) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
local             → 0.078GB
```

### Show Collections (passo 3)
```
fernando(mongod-3.2.6) be-mean-pokemons> show collections
fernando(mongod-3.2.6) be-mean-pokemons> 
```

### Cadastro dos Pokemons (passo 4)
```
fernando(mongod-3.2.6) be-mean-pokemons> var pokemons = [{name: 'CunhaCu', description: 'Pokemon Ladrao', type: 'Ladrao', attack: 9999, defense: 9999, height: 1.80}, 
{name: 'AecioPo', description: 'Aspirador de Po', type: 'Cherador', attack: 9999, defense: 9999, height: 1.82}, 
{name: 'Fernando Collor', description: 'Aspirador Philco 2000', type: 'Cherador Nato', attack: 8000, defense: 8000, height: 1.90}, 
{name: 'Bolsonada', description: 'Militar Conservador', type: 'Careta', attack: 5000, defense: 5000, height: 1.90}, 
{name:'Luladrao', description: 'Rouba de pobre', type: 'Cara Dura', attack: 1000, defense: 1000, height: 1.80}]
fernando(mongod-3.2.6) be-mean-pokemons> pokemons
[
  {
    "name": "CunhaCu",
    "description": "Pokemon Ladrao",
    "type": "Ladrao",
    "attack": 9999,
    "defense": 9999,
    "height": 1.8
  },
  {
    "name": "AecioPo",
    "description": "Aspirador de Po",
    "type": "Cherador",
    "attack": 9999,
    "defense": 9999,
    "height": 1.82
  },
  {
    "name": "Fernando Collor",
    "description": "Aspirador Philco 2000",
    "type": "Cherador Nato",
    "attack": 8000,
    "defense": 8000,
    "height": 1.9
  },
  {
    "name": "Bolsonada",
    "description": "Militar Conservador",
    "type": "Careta",
    "attack": 5000,
    "defense": 5000,
    "height": 1.9
  },
  {
    "name": "Luladrao",
    "description": "Rouba de pobre",
    "type": "Cara Dura",
    "attack": 1000,
    "defense": 1000,
    "height": 1.8
  }
]



fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 169ms
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

### Listar Pokemons (passo 5)
```
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 169ms
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
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("572b61faa1e3052ea6fd023a"),
  "name": "CunhaCu",
  "description": "Pokemon Ladrao",
  "type": "Ladrao",
  "attack": 9999,
  "defense": 9999,
  "height": 1.8
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023b"),
  "name": "AecioPo",
  "description": "Aspirador de Po",
  "type": "Cherador",
  "attack": 9999,
  "defense": 9999,
  "height": 1.82
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023c"),
  "name": "Fernando Collor",
  "description": "Aspirador Philco 2000",
  "type": "Cherador Nato",
  "attack": 8000,
  "defense": 8000,
  "height": 1.9
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023d"),
  "name": "Bolsonada",
  "description": "Militar Conservador",
  "type": "Careta",
  "attack": 5000,
  "defense": 5000,
  "height": 1.9
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023e"),
  "name": "Luladrao",
  "description": "Rouba de pobre",
  "type": "Cara Dura",
  "attack": 1000,
  "defense": 1000,
  "height": 1.8
}
Fetched 5 record(s) in 2ms
```

### Pokemon (passo 6)
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {"name": "CunhaCu"}
fernando(mongod-3.2.6) be-mean-pokemons> var poke = db.pokemons.findOne(query)
fernando(mongod-3.2.6) be-mean-pokemons> poke
{
  "_id": ObjectId("572b61faa1e3052ea6fd023a"),
  "name": "CunhaCu",
  "description": "Pokemon Ladrao",
  "type": "Ladrao",
  "attack": 9999,
  "defense": 9999,
  "height": 1.8
}
```

### Atualizar Pokemon (passo 7)
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {"name": "CunhaCu"}
fernando(mongod-3.2.6) be-mean-pokemons> var poke = db.pokemons.findOne(query)
fernando(mongod-3.2.6) be-mean-pokemons> poke
{
  "_id": ObjectId("572b61faa1e3052ea6fd023a"),
  "name": "CunhaCu",
  "description": "Pokemon Ladrao",
  "type": "Ladrao",
  "attack": 9999,
  "defense": 9999,
  "height": 1.8
}
fernando(mongod-3.2.6) be-mean-pokemons> poke.description
Pokemon Ladrao
fernando(mongod-3.2.6) be-mean-pokemons> poke.description = "Pokemon Ladrao/Safado"
Pokemon Ladrao/Safado
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572b61faa1e3052ea6fd023a"),
  "name": "CunhaCu",
  "description": "Pokemon Ladrao/Safado",
  "type": "Ladrao",
  "attack": 9999,
  "defense": 9999,
  "height": 1.8
}
Fetched 1 record(s) in 2ms
```