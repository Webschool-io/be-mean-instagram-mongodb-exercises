# MongoDB - Aula 02 - Exercício
autor: Douglas Salin Zuqueto

## criar banco de dados (passo 1)
```
fedora(mongod-3.0.4) be-mean> use be-mean-pokemons
switched to db be-mean-pokemons

```

## Listagem das databases (passo 2)

```
fedora(mongod-3.0.4) be-mean-pokemons> show dbs
mqtt             → 0.078GB
MonitorDeEnergia → 0.078GB
powerevent-test  → 0.078GB
mean             → 0.078GB
mean-dev         → 0.078GB
be-mean          → 0.078GB
local            → 0.078GB
```

## Listagem das coleções (passo 3)

```
fedora(mongod-3.0.4) be-mean-pokemons> show collections
```

## Cadastro dos pokemons (passo 4)

```
fedora(mongod-3.0.4) be-mean-pokemons> var pokemons = [{"name": "Pikachu", "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.", "attack":"30", "defense":"20", "height":"0.4"}, {"name": "Sandslash",  "description": "Sandslash's body is covered by tough spikes, which are hardened sections of its hide.", "attack":"50", "defense":"50", "height":"1.0"}, {"name": "Nidoran",  "description": "Nidoran? has barbs that secrete a powerful poison.", "attack":"30", "defense":"20", "height":"0.4"}, {"name": "Raichu",  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.", "attack":"50", "defense":"30", "height":"0.8"}, {"name": "Sandshrew",  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert.", "attack":"40", "defense":"40", "height":"0.6"}]
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 68ms
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

## Lista dos pokemons (passo 5)

```
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e2"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.",
  "attack": "30",
  "defense": "20",
  "height": "0.4"
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e3"),
  "name": "Sandslash",
  "description": "Sandslash's body is covered by tough spikes, which are hardened sections of its hide.",
  "attack": "50",
  "defense": "50",
  "height": "1.0"
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e4"),
  "name": "Nidoran",
  "description": "Nidoran? has barbs that secrete a powerful poison.",
  "attack": "30",
  "defense": "20",
  "height": "0.4"
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e5"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.",
  "attack": "50",
  "defense": "30",
  "height": "0.8"
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e6"),
  "name": "Sandshrew",
  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert.",
  "attack": "40",
  "defense": "40",
  "height": "0.6"
}
Fetched 5 record(s) in 1ms
```

## Pikachu (passo 6)

```
fedora(mongod-3.0.4) be-mean-pokemons> var query = {name: /pikachu/i}
fedora(mongod-3.0.4) be-mean-pokemons> var poke = db.pokemons.findOne(query)
fedora(mongod-3.0.4) be-mean-pokemons> poke
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e2"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.",
  "attack": "30",
  "defense": "20",
  "height": "0.4"
}

```

## Atualização do Pikachu (passo 6)

```
fedora(mongod-3.0.4) be-mean-pokemons> poke.description = "Modificando a Descrição do Pikachu"
Modificando a Descrição do Pikachu
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
fedora(mongod-3.0.4) be-mean-pokemons> var poke = db.pokemons.findOne(query)
fedora(mongod-3.0.4) be-mean-pokemons> poke
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e2"),
  "name": "Pikachu",
  "description": "Modificando a Descrição do Pikachu",
  "attack": "30",
  "defense": "20",
  "height": "0.4"
}

```
