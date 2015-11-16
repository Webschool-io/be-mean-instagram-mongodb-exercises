
# MongoDB - Aula 02 - Exercício
# Autor: Rodrigo de Medeiros Gianotto 

## Step 1: Criando database be-mean-pokemons
```
use be-mean-pokemons;
switched to db be-mean-pokemons

```

## Step 2: Listando as Databases 
```
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB
```

## Step 3: Listando as Coleções do DB
```
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> show collections
```

## Step 4: Inserindo 5 Pokemons
```
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Poke Steve Jobs','description':'Inovador mais ousado do planeta','type': 'CEO', attack: 99, height: 0.2 }
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1765ms
WriteResult({
  "nInserted": 1
})
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Poke Bill Gates','description':'Inventou o SO mais escroto do planeta.','type': 'CEO', attack: 88, height: 0.3 }
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Poke Dilma Roussef','description':'Presidenta que acaba com o Brasil dia após dia.','type': 'Presidanta', attack: 77, height: 0.4 }
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Poke Tarzan','description':'Bem louco esse cara', attack: 66, height: 0.5 }
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Poke Ayrton Senna','description':'Melhor piloto de todos os tempos','type': 'Piloto', attack: 55, height: 0.6 }
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

```

## Step 5: Listando os Pokemons da Coleção
```
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5648c16f258133224d47381f"),
  "name": "Poke Steve Jobs",
  "description": "Inovador mais ousado do planeta",
  "type": "CEO",
  "attack": 99,
  "height": 0.2
}
{
  "_id": ObjectId("5648c180258133224d473820"),
  "name": "Poke Bill Gates",
  "description": "Inventou o SO mais escroto do planeta.",
  "type": "CEO",
  "attack": 88,
  "height": 0.3
}
{
  "_id": ObjectId("5648c189258133224d473821"),
  "name": "Poke Dilma Roussef",
  "description": "Presidenta que acaba com o Brasil dia após dia.",
  "type": "Presidanta",
  "attack": 77,
  "height": 0.4
}
{
  "_id": ObjectId("5648c190258133224d473822"),
  "name": "Poke Tarzan",
  "description": "Bem louco esse cara",
  "attack": 66,
  "height": 0.5
}
{
  "_id": ObjectId("5648c198258133224d473823"),
  "name": "Poke Ayrton Senna",
  "description": "Melhor piloto de todos os tempos",
  "type": "Piloto",
  "attack": 55,
  "height": 0.6
}
Fetched 5 record(s) in 1ms

```

## Step 6: Busque um Pokemon a sua escolha na variável poke
```
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> var query =  { name: 'Poke Dilma Roussef' }
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("5648c189258133224d473821"),
  "name": "Poke Dilma Roussef",
  "description": "Presidenta que acaba com o Brasil dia após dia.",
  "type": "Presidanta",
  "attack": 77,
  "height": 0.4
}

```

## Step 7: Modifique a description e salve-o
```
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> poke.description = 'Presidenta que mais roubou o Brasil em todos os tempos'
Presidenta que mais roubou o Brasil em todos os tempos
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
Rodrigos-iMac(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5648c16f258133224d47381f"),
  "name": "Poke Steve Jobs",
  "description": "Inovador mais ousado do planeta",
  "type": "CEO",
  "attack": 99,
  "height": 0.2
}
{
  "_id": ObjectId("5648c180258133224d473820"),
  "name": "Poke Bill Gates",
  "description": "Inventou o SO mais escroto do planeta.",
  "type": "CEO",
  "attack": 88,
  "height": 0.3
}
{
  "_id": ObjectId("5648c189258133224d473821"),
  "name": "Poke Dilma Roussef",
  "description": "Presidenta que mais roubou o Brasil em todos os tempos",
  "type": "Presidanta",
  "attack": 77,
  "height": 0.4
}
{
  "_id": ObjectId("5648c190258133224d473822"),
  "name": "Poke Tarzan",
  "description": "Bem louco esse cara",
  "attack": 66,
  "height": 0.5
}
{
  "_id": ObjectId("5648c198258133224d473823"),
  "name": "Poke Ayrton Senna",
  "description": "Melhor piloto de todos os tempos",
  "type": "Piloto",
  "attack": 55,
  "height": 0.6
}
Fetched 5 record(s) in 2ms

```
