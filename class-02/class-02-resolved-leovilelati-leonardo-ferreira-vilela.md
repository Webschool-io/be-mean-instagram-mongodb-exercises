# MongoDB - Aula 02 - Exercício
autor: Leonardo Ferreira Vilela

## Listagem das databases (Passo 2)
```
Command: show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
local              0.078GB
```

## Listagem das coleções (Passo 3)
```
Command: show collections
nada, pois não há collections no database be-mean-pokemon até o momento.
```

## Cadastro dos pokemons (Passo 4)
```
Command: var pokemons = [{
                            name: "Venusaur",
                            description: "Bicho bunito de papai",
                            attack: 20,
                            defense: 30,
                            height: 0.4
                        }, {
                            name: "Charmander",
                            description: "Bichinho fofinho",
                            attack: 40,
                            defense: 50,
                            height: 0.6
                        }, {
                            name: "Charizard",
                            description: "Top demais",
                            attack: 50,
                            defense: 80,
                            height: 0.6
                        }, {
                            name: "Metapod",
                            description: "Que bicho mais estranho",
                            attack: 60,
                            defense: 10,
                            height: 0.1
                        }, {
                            name: "Weedle",
                            description: "Metabee",
                            attack: 40,
                            defense: 80,
                            height: 14
                        }]

Command: db.pokemons.insert(pokemons)


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
 
})
```

## Lista dos pokemons (Passo 5)
```
Command: db.pokemons.find()


{ "_id" : ObjectId("564be0166c04f578f355b78d"), "name" : "Venusaur", "descriptio
n" : "Bicho bunito de papai", "attack" : 20, "defense" : 30, "height" : 0.4 }
{ "_id" : ObjectId("564be0166c04f578f355b78e"), "name" : "Charmander", "descript
ion" : "Bichinho fofinho", "attack" : 40, "defense" : 50, "height" : 0.6 }
{ "_id" : ObjectId("564be0166c04f578f355b78f"), "name" : "Charizard", "descripti
on" : "Top demais", "attack" : 50, "defense" : 80, "height" : 0.6 }
{ "_id" : ObjectId("564be0166c04f578f355b790"), "name" : "Metapod", "description
" : "Que bicho mais estranho", "attack" : 60, "defense" : 10, "height" : 0.1 }
{ "_id" : ObjectId("564be0166c04f578f355b791"), "name" : "Weedle", "description"
 : "Metabee", "attack" : 40, "defense" : 80, "height" : 14 }
```

##  Weedle (Passo 6)
```

Command: var query = {'name':'Weedle'}
Command: query

{ "name" : "Weedle" }


Command: var poke = db.pokemons.findOne(query)
{
        "_id" : ObjectId("564be0166c04f578f355b791"),
        "name" : "Weedle",
        "description" : "Metabee",
        "attack" : 40,
        "defense" : 80,
        "height" : 14
}

```

## Atualização do Metabee (Passo 7)
```
poke.description = "Essa document foi alterado"

Command: db.pokemons.save(poke)

Updated 1 existing record(s) in 42ms
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

Command: > db.pokemons.findOne(poke)
{
        "_id" : ObjectId("564be0166c04f578f355b791"),
        "name" : "Weedle",
        "description" : "Este document foi aletrado.",
        "attack" : 40,
        "defense" : 80,
        "height" : 14
}
```
