# MongoDB - Aula 02 - Exercício
autor: Alex de Miranda

## Listagem das databases (passo 2)
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram undefined 0.078GB
be-mean           undefined 0.078GB
local             undefined 0.078GB
test              undefined 0.078GB

## Listagem das coleções (passo 3)
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> show collections
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons>

## Cadastro dos pokemons (passo 4)
pokemon = {name:'Butterfree', description:'tem uma capacidade superior de procurar delicioso mel de flores', attack:45, defense:50, height:'1,1m'}

db.pokemons.insert(pokemon)

Inserted 1 record(s) in 283ms
WriteResult({
    "nInserted": 1
})

pokemon = {name:'Weedle', description:'tem o olfato bem apurado', attack:35, defense:30, height:'0,3m'}

db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
    "nInserted": 1
})


pokemon = {name:'Kakuna', description:'permanece parado numa arvore até sua evolução', attack:25, defense:50, height:'0,6m'}

db.pokemons.insert(pokemon)

Inserted 1 record(s) in 0ms
WriteResult({
    "nInserted": 1
})

pokemon = {name:'Beedrill', description:'Extremamente territorial, ninguém deve se aproximar do seu ninho', attack:90, defense:40, height:'1,0m'}

db.pokemons.insert(pokemon)


Inserted 1 record(s) in 1ms
WriteResult({
    "nInserted": 1
})


pokemon = {name:'Pidgey', description:'Tem um incrivel senso de direção, capaz de voltar para casa não importa o quão longe esteja dela', attack:45, defense:40, height:'0,3m'}

db.pokemons.insert(pokemon)

Inserted 1 record(s) in 1ms
WriteResult({
    "nInserted": 1
})


## Lista dos pokemons (passo 5)
{
    "_id": ObjectId("564beb614b6d7ef94f2db0d9"),
    "name": "Butterfree",
    "description": "tem uma capacidade superior de procurar delicioso mel de flo
res",
    "attack": 45,
    "defense": 50,
    "height": "1,1m"
}
{
    "_id": ObjectId("564beba64b6d7ef94f2db0da"),
    "name": "Weedle",
    "description": "tem o olfato bem apurado",
    "attack": 35,
    "defense": 30,
    "height": "0,3m"
}
{
    "_id": ObjectId("564bebe04b6d7ef94f2db0db"),
    "name": "Kakuna",
    "description": "permanece parado numa arvore até sua evolução",
    "attack": 25,
    "defense": 50,
    "height": "0,6m"
}
{
    "_id": ObjectId("564bec004b6d7ef94f2db0dc"),
    "name": "Beedrill",
    "description": "Extremamente territorial, ninguém deve se aproximar do seu n
inho",
    "attack": 90,
    "defense": 40,
    "height": "1,0m"
}
{
    "_id": ObjectId("564bec214b6d7ef94f2db0dd"),
    "name": "Pidgey",
    "description": "Tem um incrivel senso de direção, capaz de voltar para casa
não importa o quão longe esteja dela",
    "attack": 45,
    "defense": 40,
    "height": "0,3m"
}
Fetched 5 record(s) in 4ms

## Pidgey (passo 6)

Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = {name:"Pidgey"}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> poke
{
    "_id": ObjectId("564bec214b6d7ef94f2db0dd"),
    "name": "Pidgey",
    "description": "Tem um incrivel senso de direção, capaz de voltar para casa não importa o quão longe esteja dela",
    "attack": 45,
    "defense": 40,
    "height": "0,3m"
}

## Atualização do Pidgey (passo 6)

Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = {name:"Pidge
y"}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var poke = db.pokemons.f
indOne(query)
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> poke
{
    "_id": ObjectId("564bec214b6d7ef94f2db0dd"),
    "name": "Pidgey",
    "description": "Volta pra casa mesmo bebado. Esse poke é doidão.",
    "attack": 45,
    "defense": 40,
    "height": "0,3m"
}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> poke.description = "Esse
 pokemon é zica, acha sua casa mesmo quando esta bebado"
Esse pokemon é zica, acha sua casa mesmo quando esta bebado
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 5ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> poke
{
    "_id": ObjectId("564bec214b6d7ef94f2db0dd"),
    "name": "Pidgey",
    "description": "Esse pokemon é zica, acha sua casa mesmo quando esta bebado"
,
    "attack": 45,
    "defense": 40,
    "height": "0,3m"
}