# MongoDb - Aula 02 - Exercício
Autor: Hélio Marcondes

## Criar database chamada be-mean-pokemons

```
    use be-mean-pokemons
    switched to db be-mean-pokemons
```

## Listagem de todas dbs

```
    show dbs
    be-mean-pokemons  0.078GB
    local             0.078GB
```

## Listagem de todas as collections

```
    show collections
```

## Criar cinco pokemons

```
    var pok = {'name':'Eevee','description':'Raposinha bonitinha','type':'normal',attack:30,defense:20,height:6.5}
    db.pokemons.insert(pok)
    WriteResult({ "nInserted" : 1 })

    var pok2 = {'name':'Umbreon','description':'Raposinha bonitinha versão do mau','type':'dark',attack:45,defense:30,height:27.0}
    db.pokemons.insert(pok2)
    WriteResult({ "nInserted" : 1 })

    var pok3 = {'name':'Flareon','description':'Raposinha bonitinha versão de fogo','type':'fire',attack:40,defense:40,height:0.9}
    db.pokemons.insert(pok3)
    WriteResult({ "nInserted" : 1 })

    var pok4 = {'name':'Jolteon','description':'Raposinha bonitinha versão de choque','type':'eletric',attack:50,defense:25,height:1.5}
    db.pokemons.insert(pok4)
    WriteResult({ "nInserted" : 1 })

    var pok5 = {'name':'Vaporeon','description':'Raposinha bonitinha versão de água','type':'água',attack:38,defense:32,height:1.0}
    db.pokemons.insert(pok5)
    WriteResult({ "nInserted" : 1 })
```

## Listar todos os pokemons

```
    db.pokemons.find()
    { "_id" : ObjectId("56a7f3a952aa820658a173fe"), "name" : "Eevee", "description" : "Raposinha bonitinha", "type" : "normal", "attack" : 30, "defense" : 20, "height" : 6.5 }
    { "_id" : ObjectId("56a7f40052aa820658a173ff"), "name" : "Umbreon", "description" : "Raposinha bonitinha versão do mau", "type" : "dark", "attack" : 45, "defense" : 30, "height" : 27 }
    { "_id" : ObjectId("56a7f43c52aa820658a17400"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4 }
    { "_id" : ObjectId("56a7f45a52aa820658a17401"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
    { "_id" : ObjectId("56a7f47052aa820658a17402"), "name" : "Charmandar", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
    { "_id" : ObjectId("56a7f47e52aa820658a17403"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
    { "_id" : ObjectId("56a7f50f52aa820658a17404"), "name" : "Flareon", "description" : "Raposinha bonitinha versão de fogo", "type" : "fire", "attack" : 40, "defense" : 40, "height" : 0.9 }
    { "_id" : ObjectId("56a7f51952aa820658a17405"), "name" : "Jolteon", "description" : "Raposinha bonitinha versão de choque", "type" : "eletric", "attack" : 50, "defense" : 25, "height" : 1.5 }
    { "_id" : ObjectId("56a7f52652aa820658a17406"), "name" : "Vaporeon", "description" : "Raposinha bonitinha versão de água", "type" : "água", "attack" : 38, "defense" : 32, "height" : 1 }
```

## Buscar um pokemon

```
    var poke = db.pokemons.findOne(query)
    poke
    {
        "_id" : ObjectId("56a7f51952aa820658a17405"),
        "name" : "Jolteon",
        "description" : "Raposinha bonitinha versão de choque",
        "type" : "eletric",
        "attack" : 50,
        "defense" : 25,
        "height" : 1.5
    }
```

## Editar a description do pokemon escolhido

```
    poke.description = "Raposinha braba versão de choque"
    Raposinha braba versão de choque

    db.pokemons.save(poke)
    WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```