# MongoDB - Aula 02 - Exercício
autor: Luã Mota

## Listagem das databases (passo 2)

```
mocallu-svf-elementary(mongod-3.0.7) be-mean-instagram> show dbs
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
local             → 0.078GB

```

## Listagem das coleções (passo 3)

```
mocallu-svf-elementary(mongod-3.0.7) be-mean-instagram> show collections
system.indexes → 0.000MB / 0.008MB
teste          → 0.000MB / 0.008MB

```

## Cadastro dos pokemons (passo 4)
```
mocallu-svf-elementary(mongod-3.0.7) be-mean-instagram> var pokemons = [{'name':'Bulbassauro','description':'Chicote de trepadeira','type': 'grama', 'attack': 49, height: 0.4 }, {'name':'Charmander','description':'Esse é o cão chupando manga de fofinho','type': 'fogo', 'attack': 52, height: 0.6 }, {'name':'Squirtle','description':'Ejeta água que passarinho não bebe','type': 'água', 'attack': 48, height: 0.5 }, {'name':'Pikachu','description':'Rato elétrico bem fofinho','type': 'electric', attack: 55, height: 0.4 }, {'name':'Caterpie','description':'Larva lutadora','type': 'inseto', attack: 30, height: 0.3 }];

mocallu-svf-elementary(mongod-3.0.7) be-mean-instagram> db.pokemons.save(pokemons)
Inserted 1 record(s) in 356ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
});

```
## Lista dos pokemons (passo 5)
```
mocallu-svf-elementary(mongod-3.0.7) be-mean-instagram> db.pokemons.find();
{
  "_id": ObjectId("56483253bb1537395057bdf8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56483253bb1537395057bdf9"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56483253bb1537395057bdfa"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56483253bb1537395057bdfb"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56483253bb1537395057bdfc"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3
}
Fetched 5 record(s) in 3ms

```


## Pikachu (passo 6)

```
mocallu-svf-elementary(mongod-3.0.7) be-mean-instagram> var query = {name: 'Pikachu'};

mocallu-svf-elementary(mongod-3.0.7) be-mean-instagram> var poke = db.pokemons.findOne(query);

mocallu-svf-elementary(mongod-3.0.7) be-mean-instagram> poke
{
  "_id": ObjectId("56482b27bb1537395057bdf2"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}

```

## Atualização do Pikachu (passo 6)

```
mocallu-svf-elementary(mongod-3.0.7) be-mean-instagram> poke.description = 'Rato amarelo que da choque';
Rato amarelo que da choque

mocallu-svf-elementary(mongod-3.0.7) be-mean-instagram> poke
{
  "_id": ObjectId("56482b27bb1537395057bdf2"),
  "name": "Pikachu",
  "description": "Rato amarelo que da choque",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}

mocallu-svf-elementary(mongod-3.0.7) be-mean-instagram> db.pokemons.save(poke);
Updated 1 existing record(s) in 24ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

mocallu-svf-elementary(mongod-3.0.7) be-mean-instagram> db.pokemons.findOne(query);
{
  "_id": ObjectId("56482b27bb1537395057bdf2"),
  "name": "Pikachu",
  "description": "Rato amarelo que da choque",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}

```
