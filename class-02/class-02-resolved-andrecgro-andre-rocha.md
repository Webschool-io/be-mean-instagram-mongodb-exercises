# MongoDB - Aula 02 - Exercício
autor: André Rocha

## Criando database be_mean_pokemons
```
> use be_mean_pokemons
switched to db be_mean_pokemons
```
## Listando databases do servidor local
```
be_mean_pokemons> show dbs
local            → 0.078GB
test             → 0.078GB
be_mean_pokemons → 0.078GB
be-mean          → 0.078GB
```

## Listando coleções da database be_mean_pokemons
```
be_mean_pokemons> show collections
be_mean_pokemons → 0.001MB / 0.008MB
system.indexes   → 0.000MB / 0.008MB

```
## Inserindo 6 Pokemons em be_mean_pokemons
```
var pokemons = [

 { 'name':'Charmeleon', 'description':'Destrói tudo saporra', 'type':'fire', 'attack':'40', 'defense':'40', height:1.1 },
 { 'name':'Charizard', 'description':'Evolução da destruição', 'type':'fire', 'attack':50, 'defense':40, height:1.7, },
 { 'name':'Magikarp', 'description':'Peixe inútil', 'type':'água', 'attack':10, 'defense':30, height:0.9 },
 { 'name':'Gyarados', 'description':'Agora sim!', 'type':'água e ainda avua saporra', 'attack':60, 'defense':30, height:6.5 },
 { 'name':'Blastoise', 'description':'Tartaruga canhão', 'type':'água','attack':'40','defense':40,height:1.6},
 { 'name':'Pikachu','description':'Rato elétrico fofo','type':'eletric','attack':55,'defense':40,height:0.4}

]

be_mean_pokemons> db.be_mean_pokemons.save(pokemons)

Inserted 1 record(s) in 435ms
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
## Listando Pokemons existentes
```
be_mean_pokemons> db.be_mean_pokemons.find()
{
  "_id": ObjectId("56453ed050f757b5fdb43fa0"),
  "name": "Charmeleon",
  "description": "Destrói tudo saporra",
  "type": "fire",
  "attack": 40,
  "defense": 40,
  "height": 1.1
}
{
  "_id": ObjectId("56453ed050f757b5fdb43fa1"),
  "name": "Charizard",
  "description": "Evolução da destruição",
  "type": "fire",
  "attack": 50,
  "defense": 40,
  "height": 1.7
}
{
  "_id": ObjectId("56453ed050f757b5fdb43fa2"),
  "name": "Magikarp",
  "description": "Peixe inútil",
  "type": "água",
  "attack": 10,
  "defense": 30,
  "height": 0.9
}
{
  "_id": ObjectId("56453ed050f757b5fdb43fa3"),
  "name": "Gyarados",
  "description": "Agora sim!",
  "type": "água e ainda avua saporra",
  "attack": 60,
  "defense": 30,
  "height": 6.5
}
{
  "_id": ObjectId("56453ed050f757b5fdb43fa4"),
  "name": "Blastoise",
  "description": "Tartaruga canhão",
  "type": "água",
  "attack": 40,
  "defense": 40,
  "height": 1.6
}
{
  "_id": ObjectId("56453ff950f757b5fdb43fa5"),
  "name": "Pikachu",
  "description": "Rato mudo, elétrico e fofo",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
Fetched 6 record(s) in 5ms

```
## Buscando Pikachu e armazenando-o em uma variável chamada poke
```
be_mean_pokemons> var query = {name:'Pikachu'}

be_mean_pokemons> var poke = db.be_mean_pokemons.findOne(query)

be_mean_pokemons> poke
{
  "_id": ObjectId("56453ff950f757b5fdb43fa5"),
  "name": "Pikachu",
  "description": "Rato elétrico fofo",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}

```
## Modificando e salvando Pikachu
```
be_mean_pokemons> poke.description = "Rato mudo, elétrico e fofo"

be_mean_pokemons> db.be_mean_pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```