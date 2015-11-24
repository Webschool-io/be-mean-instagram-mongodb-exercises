# MongoDB - Aula 02 - Exercício
autor: Bruno Micaela

## Criar Database (passo 1)
```
> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases (passo 2)
```
> show dbs
be-mean  0.078GB
local    0.078GB
test     0.078GB
```

## Listagem das coleções (passo 3)
```
> show collections
>                 
```

## Cadastro dos pokemons (passo 4)
```
> var pokemons = [{'name':'Blastoise', 'description':'Blastoise has water spouts that protrude from its shell.', 'type':'Water', 'attack':'40', 'defense':'40', height:1.6},{'name':'Charizard', 'description':'Charizard flies around the sky in search of powerful opponents', 'type':'Fire', 'attack':40, 'defense':30, height:1.7},{'name':'Venusaur', 'description':'There is a large flower on Venusaurs back', 'type':'Grass', 'attack':'40', 'defense':40, height:2.0},{'name':'Butterfree', 'description':'Butterfree has a superior ability to search for delicious honey from flowers', 'type':'Bug', 'attack':'20', 'defense':20, height:1.1},{'name':'Pikachu', 'description':'Rato elétrico fofo', 'type':'eletric', 'attack':55, 'defense':40, height:0.4}]
> db.pokemons.insert(pokemons)
BulkWriteResult({
        "writeErrors" : [ ],
        "writeConcernErrors" : [ ],
        "nInserted" : 5,
        "nUpserted" : 0,
        "nMatched" : 0,
        "nModified" : 0,
        "nRemoved" : 0,
        "upserted" : [ ]
})
```

## Lista dos pokemons (passo 5)
```
> db.pokemons.find()                                                                                                                                                      
{ "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb018"), "name" : "Blastoise", "description" : "Blastoise has water spouts that protrude from its shell.", "type" : "Water", "attac
k" : "40", "defense" : "40", "height" : 1.6 }                                                                                                                             
{ "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb019"), "name" : "Charizard", "description" : "Charizard flies around the sky in search of powerful opponents", "type" : "Fire", "
attack" : 40, "defense" : 30, "height" : 1.7 }                                                                                                                            
{ "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb01a"), "name" : "Venusaur", "description" : "There is a large flower on Venusaurs back", "type" : "Grass", "attack" : "40", "defe
nse" : 40, "height" : 2 }                                                                                                                                                 
{ "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb01b"), "name" : "Butterfree", "description" : "Butterfree has a superior ability to search for delicious honey from flowers", "ty
pe" : "Bug", "attack" : "20", "defense" : 20, "height" : 1.1 }                                                                                                            
{ "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb01c"), "name" : "Pikachu", "description" : "Rato elétrico fofo", "type" : "eletric", "attack" : 55, "defense" : 40, "height" : 0.
4 }                                                                                                                                                                       
```

## Pikachu (passo 6)
```
> var query = {"name": "Pikachu"}
> var poke = db.pokemons.findOne(query)
> poke
{
        "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb01c"),
        "name" : "Pikachu",
        "description" : "Rato elétrico fofo",
        "type" : "eletric",
        "attack" : 55,
        "defense" : 40,
        "height" : 0.4
}
```

## Atualização do Pikachu (passo 6)
```
> poke.description
Rato elétrico fofo
> poke.description = "Nova Descrição do Pikachu"
Nova Descrição do Pikachu
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.findOne(query)
{
        "_id" : ObjectId("564fdfe0a1a0ef1c5ccdb01c"),
        "name" : "Pikachu",
        "description" : "Nova Descrição do Pikachu",
        "type" : "eletric",
        "attack" : 55,
        "defense" : 40,
        "height" : 0.4
}
```