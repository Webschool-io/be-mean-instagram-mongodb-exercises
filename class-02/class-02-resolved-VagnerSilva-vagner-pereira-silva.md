pokemon# MongoDb - Aula 02 - Exercício
autor: Vagner Pereira Silva

## Criando a database
```
> use be-mean-pokemons
switched to db be-mean-pokemons


```

## Listando as databases
```
> show databases

> show dbs

be-mean             0.063GB
be-mean-instragram  0.031GB
local               0.031GB
test                0.031GB

>

```

## Listando as collections
```
> show collections
```

## Inserindo 5 pokemons na coeleção pokemons
```
> var pokemon = { name:'Pikachu', description:'Rato', type:'Electric', attack:55, height:4 }
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> var pokemon = { name:'Psyduck', description:'Pato', type:'Water', attack:52, height:8 }
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> var pokemon = { name:'Charizard', description:'Dragao', type:'Fire', attack:84, height:17 }
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> var pokemon = { name:'Squirtle', description:'Tartaruga', type:'Water', attack:48, height:5 }
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> var pokemon = { name:'Meowth', description:'Gato', type:'Normal', attack:45, height:4 }
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

```

## Listando os pokemons existentes na coleção pokemons
```
> db.pokemons.find()

> db.pokemons.find().pretty()
{
        "_id" : ObjectId("567b8a2119e6c47b0b11c1ac"),
        "name" : "Pikachu",
        "description" : "Rato",
        "type" : "Electric",
        "attack" : 55,
        "height" : 4
}
{
        "_id" : ObjectId("567b8a2f19e6c47b0b11c1ad"),
        "name" : "Psyduck",
        "description" : "Pato",
        "type" : "Water",
        "attack" : 52,
        "height" : 8
}
{
        "_id" : ObjectId("567b8a3a19e6c47b0b11c1ae"),
        "name" : "Charizard",
        "description" : "Dragao",
        "type" : "Fire",
        "attack" : 84,
        "height" : 17
}
{
        "_id" : ObjectId("567b8a4e19e6c47b0b11c1af"),
        "name" : "Squirtle",
        "description" : "Tartaruga",
        "type" : "Water",
        "attack" : 48,
        "height" : 5
}
{
        "_id" : ObjectId("567b8a5f19e6c47b0b11c1b0"),
        "name" : "Meowth",
        "description" : "Gato",
        "type" : "Normal",
        "attack" : 45,
        "height" : 4
}


```

## Busca do pokemon pelo nome
```

> var poke = db.pokemons.findOne({name:'Pikachu'})
> poke
{
        "_id" : ObjectId("567b8a2119e6c47b0b11c1ac"),
        "name" : "Pikachu",
        "description" : "Rato",
        "type" : "Electric",
        "attack" : 55,
        "height" : 4
}


```

## Modificando a 'description' do pokemon encontrado e salvando na collection a alteração
```
> poke.description = 'Pika-Pika'
Pika-Pika
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

```
