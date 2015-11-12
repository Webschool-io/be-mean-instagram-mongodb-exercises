
# MongoDB - Aula 02 - Exercício
autor: Higor Diego

## Listagem das databases (passo 2)

```
m0nk3y(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons


m0nk3y(mongod-3.0.7) be-mean-pokemons> show dbs;
local    → 0.078GB
testando → 0.203GB
app      → 0.203GB
loteria  → 0.078GB
be-mean  → 0.078GB
```

## Listagem das coleções (passo 3)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> show collections;

```

## Cadastro dos pokemons (passo 4)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var pokemons = 
... [{name: 'Testandomon', description: 'teste', type: 'exercio', attack: 7001, defense: 600, height: 0.69},
... {name: 'testando2', description: 'testando2', type: 'teste2', attack: 2, defense: 100, height: 2.60},
... {name: 'testando3', description: 'testando3', type: 'teste3', attack: 3, defense: 300, height: 3.60},
... {name: 'testando4', description: 'testando4', type: 'teste4', attack: 4, defense: 400, height: 4.60},
... {name: 'testando5', description: 'testando5', type: 'teste5', attack: 5, defense: 500, height: 5.60},
... {name: 'testando6', description: 'testando6', type: 'teste6', attack: 6, defense: 600, height: 6.60}
suissacorp(mongod-3.0.6) be-mean-pokemons> pokemons
[
  {
    "name": "Testandomon",
    "description": "teste",
    "type": "exercio",
    "attack": 7001,
    "defense": 600,
    "height": 0.69
  },
  {
    "name": "testando2",
    "description": "testando2",
    "type": "teste2",
    "attack": 2,
    "defense": 100,
    "height": 2.6
  },
  {
    "name": "testando3",
    "description": "testando3",
    "type": "teste3",
    "attack": 3,
    "defense": 300,
    "height": 3.6
  },
  {
    "name": "testando4",
    "description": "testando4",
    "type": "teste4",
    "attack": 4,
    "defense": 400,
    "height": 4.6
  },
  {
    "name": "testando5",
    "description": "testando5",
    "type": "teste5",
    "attack": 5,
    "defense": 500,
    "height": 5.6
  },
  {
    "name": "testando6",
    "description": "testando6",
    "type": "teste6",
    "attack": 6,
    "defense": 600,
    "height": 6.6
  }
]
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 574ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 6,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

## Lista dos pokemons (passo 5)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a22"),
  "name": "Testandomon",
  "description": "teste",
  "type": "exercio",
  "attack": 7001,
  "defense": 600,
  "height": 0.69
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a23"),
  "name": "testando2",
  "description": "testando2",
  "type": "teste2",
  "attack": 2,
  "defense": 100,
  "height": 2.6
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a24"),
  "name": "testando3",
  "description": "testando3",
  "type": "teste3",
  "attack": 3,
  "defense": 300,
  "height": 3.6
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a25"),
  "name": "testando4",
  "description": "testando4",
  "type": "teste4",
  "attack": 4,
  "defense": 400,
  "height": 4.6
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a26"),
  "name": "testando5",
  "description": "testando5",
  "type": "teste5",
  "attack": 5,
  "defense": 500,
  "height": 5.6
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a27"),
  "name": "testando6",
  "description": "testando6",
  "type": "teste6",
  "attack": 6,
  "defense": 600,
  "height": 6.6
}
Fetched 6 record(s) in 2ms

```

## Pokemon (passo 6)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {"name" : 'testando2'}
m0nk3y(mongod-3.0.7) be-mean-pokemons> var pok = db.pokemons.findOne(query);

m0nk3y(mongod-3.0.7) be-mean-pokemons> pok
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a23"),
  "name": "testando2",
  "description": "testando2",
  "type": "teste2",
  "attack": 2,
  "defense": 100,
  "height": 2.6
}


```

## Atualização do Pokemon (passo 7)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {'name' : 'testando2'}
m0nk3y(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query);
m0nk3y(mongod-3.0.7) be-mean-pokemons> poke

m0nk3y(mongod-3.0.7) be-mean-pokemons> poke.description
testando2
m0nk3y(mongod-3.0.7) be-mean-pokemons> poke.description = "Pokemon além do teste";
Pokemon além do teste
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke);
Updated 1 existing record(s) in 47ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne(query);
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a23"),
  "name": "testando2",
  "description": "Pokemon além do teste",
  "type": "teste2",
  "attack": 2,
  "defense": 100,
  "height": 2.6
}


```


# MongoDB - Aula 02 - Exercício
autor: Higor Diego

## Listagem das databases (passo 2)

```
m0nk3y(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons


m0nk3y(mongod-3.0.7) be-mean-pokemons> show dbs;
local    → 0.078GB
testando → 0.203GB
app      → 0.203GB
loteria  → 0.078GB
be-mean  → 0.078GB
```

## Listagem das coleções (passo 3)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> show collections;

```

## Cadastro dos pokemons (passo 4)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var pokemons = 
... [{name: 'Testandomon', description: 'teste', type: 'exercio', attack: 7001, defense: 600, height: 0.69},
... {name: 'testando2', description: 'testando2', type: 'teste2', attack: 2, defense: 100, height: 2.60},
... {name: 'testando3', description: 'testando3', type: 'teste3', attack: 3, defense: 300, height: 3.60},
... {name: 'testando4', description: 'testando4', type: 'teste4', attack: 4, defense: 400, height: 4.60},
... {name: 'testando5', description: 'testando5', type: 'teste5', attack: 5, defense: 500, height: 5.60},
... {name: 'testando6', description: 'testando6', type: 'teste6', attack: 6, defense: 600, height: 6.60}
suissacorp(mongod-3.0.6) be-mean-pokemons> pokemons
[
  {
    "name": "Testandomon",
    "description": "teste",
    "type": "exercio",
    "attack": 7001,
    "defense": 600,
    "height": 0.69
  },
  {
    "name": "testando2",
    "description": "testando2",
    "type": "teste2",
    "attack": 2,
    "defense": 100,
    "height": 2.6
  },
  {
    "name": "testando3",
    "description": "testando3",
    "type": "teste3",
    "attack": 3,
    "defense": 300,
    "height": 3.6
  },
  {
    "name": "testando4",
    "description": "testando4",
    "type": "teste4",
    "attack": 4,
    "defense": 400,
    "height": 4.6
  },
  {
    "name": "testando5",
    "description": "testando5",
    "type": "teste5",
    "attack": 5,
    "defense": 500,
    "height": 5.6
  },
  {
    "name": "testando6",
    "description": "testando6",
    "type": "teste6",
    "attack": 6,
    "defense": 600,
    "height": 6.6
  }
]
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 574ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 6,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

## Lista dos pokemons (passo 5)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a22"),
  "name": "Testandomon",
  "description": "teste",
  "type": "exercio",
  "attack": 7001,
  "defense": 600,
  "height": 0.69
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a23"),
  "name": "testando2",
  "description": "testando2",
  "type": "teste2",
  "attack": 2,
  "defense": 100,
  "height": 2.6
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a24"),
  "name": "testando3",
  "description": "testando3",
  "type": "teste3",
  "attack": 3,
  "defense": 300,
  "height": 3.6
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a25"),
  "name": "testando4",
  "description": "testando4",
  "type": "teste4",
  "attack": 4,
  "defense": 400,
  "height": 4.6
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a26"),
  "name": "testando5",
  "description": "testando5",
  "type": "teste5",
  "attack": 5,
  "defense": 500,
  "height": 5.6
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a27"),
  "name": "testando6",
  "description": "testando6",
  "type": "teste6",
  "attack": 6,
  "defense": 600,
  "height": 6.6
}
Fetched 6 record(s) in 2ms

```

## Pokemon (passo 6)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {"name" : 'testando2'}
m0nk3y(mongod-3.0.7) be-mean-pokemons> var pok = db.pokemons.findOne(query);

m0nk3y(mongod-3.0.7) be-mean-pokemons> pok
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a23"),
  "name": "testando2",
  "description": "testando2",
  "type": "teste2",
  "attack": 2,
  "defense": 100,
  "height": 2.6
}


```

## Atualização do Pokemon (passo 7)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {'name' : 'testando2'}
m0nk3y(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query);
m0nk3y(mongod-3.0.7) be-mean-pokemons> poke

m0nk3y(mongod-3.0.7) be-mean-pokemons> poke.description
testando2
m0nk3y(mongod-3.0.7) be-mean-pokemons> poke.description = "Pokemon além do teste";
Pokemon além do teste
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke);
Updated 1 existing record(s) in 47ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne(query);
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a23"),
  "name": "testando2",
  "description": "Pokemon além do teste",
  "type": "teste2",
  "attack": 2,
  "defense": 100,
  "height": 2.6
}


```

