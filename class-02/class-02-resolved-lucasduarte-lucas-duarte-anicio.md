# MongoDB - Aula 02 - Exercício
autor : Lucas Duarte Anício

## 1 - Criando a database be-mean-pokemons

```
lucas-Aspire-E5-573G(mongod-2.6.3) test> use be-mean-pokemons
switched to db be-mean-pokemons
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons>
```

## 2 - Listar as databases do servidor

```
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> show dbs
admin             → (empty)
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
be-mean-pokemons  → 0.078GB
local             → 0.078GB

```

## 3 - Listar coleções da database

```
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> show collections
pokemons       → 0.001MB / 0.008MB
system.indexes → 0.000MB / 0.008MB
```

## 4 - Inserir 5 pokemons

```
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> var pokemon = { 'name': 'Caterpie', 'description': 'Larva doida', 'type': 'Inseto', 'attack': 30, 'height': 0.3 }
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 17ms
WriteResult({
  "nInserted": 1
})

lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> var pokemon = { 'name': 'Raichu', 'description': 'Quase um pikachu', 'type': 'Elétrico', 'attack': 45, 'height': 0.8 }
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 5ms
WriteResult({
  "nInserted": 1
})

lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> var pokemon = { 'name': 'Sandshrew', 'description': 'Tau locão', 'type': 'Terra', 'attack': 42, 'height': 0.6 }
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> var pokemon = { 'name': 'Nidoran', 'description': 'Rato do diabo', 'type': 'Venenoso', 'attack': 34, 'height': 0.4 }
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> var pokemon = { 'name': 'Clefairy', 'description': 'Sa Fada', 'type': 'Fada', 'attack': 27, 'height': 0.6 }
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})

```

## 5 - Listar os pokemons existentes na collection

```
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56acaf241a90b82afaaf0cfa"),
  "name": "Caterpie",
  "description": "Larva doida",
  "type": "Inseto",
  "attack": 30,
  "height": 0.3
}
{
  "_id": ObjectId("56acb03c6907bdfeb234608f"),
  "name": "Raichu",
  "description": "Quase um pikachu",
  "type": "Elétrico",
  "attack": 45,
  "height": 0.8
}
{
  "_id": ObjectId("56acb0506907bdfeb2346090"),
  "name": "Sandshrew",
  "description": "Tau locão",
  "type": "Terra",
  "attack": 42,
  "height": 0.6
}
{
  "_id": ObjectId("56acb05f6907bdfeb2346091"),
  "name": "Nidoran",
  "description": "Rato do diabo",
  "type": "Venenoso",
  "attack": 34,
  "height": 0.4
}
{
  "_id": ObjectId("56acb07bb087f83dd11a9e6e"),
  "name": "Clefairy",
  "description": "Sa Fada",
  "type": "Fada",
  "attack": 27,
  "height": 0.6
}
Fetched 5 record(s) in 2ms

```

## 6 - Buscar pokemons e armazenar na variavel poke

```
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> var query = {'name': 'Clefairy'}
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> var poke = db.pokemons.findOne(query)
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> poke
{
  "_id": ObjectId("56acb07bb087f83dd11a9e6e"),
  "name": "Clefairy",
  "description": "Sa Fada",
  "type": "Fada",
  "attack": 27,
  "height": 0.6
}
```

## 7 - Modificar a description e salvar

```
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> poke.description = "Fada"
Fada
lucas-Aspire-E5-573G(mongod-2.6.3) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```


