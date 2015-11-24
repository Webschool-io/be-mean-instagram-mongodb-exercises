# MongoDB - Aula 02 - Exercício
autor: Ramon Portela Santos

## Listagem das databases (passo 2)

```
Ramon-PC(mongod-3.0.7) be-mean-pokemons> show dbs;
be-mean-instagram ? 0.078GB
be-mean           ? 0.078GB
local             ? 0.078GB

```

## Listagem das coleções (passo 3)

```
Ramon-PC(mongod-3.0.7) be-mean-pokemons> show collections
pokemons       ? 0.000MB / 0.008MB
system.indexes ? 0.000MB / 0.008MB

```

## Cadastro dos pokemons (passo 4)

```
Ramon-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({'name':'Sudowoodo', 'description':'Uma árvore engraçada', 'attack':100, 'defense':115, 'height':12});
Inserted 1 record(s) in 8ms
WriteResult({
  "nInserted": 1
})
Ramon-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({'name':'Arbok', 'description':'Mata a cobra e mostra o pau', 'attack':85, 'defense':69, 'height':35});
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
Ramon-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({'name':'Nidoran', 'description':'Um rato com chifre de unicórnio', 'attack':57, 'defense':40, 'height':5});
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
Ramon-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({'name':'Jynx', 'description':'Filhote de cruz credo', 'attack':50, 'defense':35, 'height':14});
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
Ramon-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({'name':'Doduo', 'description':'Duas cabeças pensam melhor que uma', 'attack':85, 'defense':45, 'height':14});
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

```


## Lista dos pokemons (passo 5)

```
Ramon-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("565231fe6c327d14f3798b58"),
  "name": "Sudowoodo",
  "description": "Uma árvore engraçada",
  "attack": 100,
  "defense": 115,
  "height": 12
}
{
  "_id": ObjectId("565232466c327d14f3798b59"),
  "name": "Arbok",
  "description": "Mata a cobra e mostra o pau",
  "attack": 85,
  "defense": 69,
  "height": 35
}
{
  "_id": ObjectId("565232996c327d14f3798b5a"),
  "name": "Nidoran",
  "description": "Um rato com chifre de unicórnio",
  "attack": 57,
  "defense": 40,
  "height": 5
}
{
  "_id": ObjectId("565232ee6c327d14f3798b5b"),
  "name": "Jynx",
  "description": "Filhote de cruz credo",
  "attack": 50,
  "defense": 35,
  "height": 14
}
{
  "_id": ObjectId("565233746c327d14f3798b5c"),
  "name": "Doduo",
  "description": "Duas cabeças pensam melhor que uma",
  "attack": 85,
  "defense": 45,
  "height": 14
}
Fetched 5 record(s) in 10ms

```


## Pesquisar Pokemon (passo 6)

```
Ramon-PC(mongod-3.0.7) be-mean-pokemons> var query = {name: 'Jynx'}
Ramon-PC(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Ramon-PC(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("565232ee6c327d14f3798b5b"),
  "name": "Jynx",
  "description": "Filhote de cruz credo",
  "attack": 50,
  "defense": 35,
  "height": 14
}

```

## Atualização do Pokemon (passo 7)

```
Ramon-PC(mongod-3.0.7) be-mean-pokemons> poke.description = "Filha do senhor popo"
Filha do senhor popo
Ramon-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```