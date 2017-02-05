#MongoDb - Aula01 - Exercício
autor: André Affonso

## 1º Criar DataBase
```
>use be-mean-pokemon
switched to db be-mean-pokemon
```
## 2º Listar quais databases possui
```
>show dbs
admin              0.000GB
be-mean            0.005GB
be-mean-instagram  0.000GB
local              0.000GB
```
## 3º Listar quais coleções possui
```
>show collections
pokemon      →  0.001MB / 0.035MB
pokemons     →  0.002MB / 0.035MB
restaurantes → 10.138MB / 3.914MB
test         →  0.000MB / 0.031MB
```

## 4º Inserir cinco pokemons
```
> var poke = {name: "Charizard", description:"Dragao que avoa", type: "fogo", attack:101, height: 3.2}
> db.pokemao.save(poke)
WriteResult({ "nInserted" : 1 })
> var poke = {name: "Snorlax", description:"Mais gordo que o faustão", type: "terra", attack:120, height: 3.7}
> db.pokemao.save(poke)
WriteResult({ "nInserted" : 1 })
> var poke = {name: "Toggeppie", description:"um ovo que fala", type: "ovos", attack:70, height: 0.4}
> db.pokemao.save(poke)
WriteResult({ "nInserted" : 1 })
> var poke = {name: "Mew two", description:"foda ba carai. Come o cu de todo mundo", type: "Deus", attack:999, height: 1.8}
> db.pokemao.save(poke)
WriteResult({ "nInserted" : 1 })
> var poke = {name: "Ratata", description:"Rato roxo desgraçado", type: "lixo", attack:1, height: 0.7}
> db.pokemao.save(poke)
WriteResult({ "nInserted" : 1 })
```
## 5º Listar os pokemons existentes
```
> db.pokemao.find()
{ "_id" : ObjectId("58865864a54af3de72f609c7"), "name" : "Charizard", "description" : "Dragao que avoa", "type" : "fogo", "attack" : 101, "height" : 3.2 }
{ "_id" : ObjectId("5886588ba54af3de72f609c8"), "name" : "Snorlax", "description" : "Mais gordo que o faustão", "type" : "terra", "attack" : 120, "height" : 3.7 }
{ "_id" : ObjectId("588658c0a54af3de72f609c9"), "name" : "Toggeppie", "description" : "um ovo que fala", "type" : "ovos", "attack" : 70, "height" : 0.4 }
{ "_id" : ObjectId("588658f1a54af3de72f609ca"), "name" : "Mew two", "description" : "foda ba carai. Come o cu de todo mundo", "type" : "Deus", "attack" : 999, "height" : 1.8 }
{ "_id" : ObjectId("58865934a54af3de72f609cb"), "name" : "Ratata", "description" : "Rato roxo desgraçado", "type" : "lixo", "attack" : 1, "height" : 0.7 }
```
## 6º Armazenar pokemons na variável 'poke'
```
> var query = {name: "Ratata"}
> var poke = db.pokemao.findOne(query)
```
## 7º Modificar descripition e salvar
```
> poke.description ="Ratasana roxa demoníaca que transmite leptospirose"
Ratasana roxa demoníaca que transmite leptospirose
> poke
{
        "_id" : ObjectId("58865934a54af3de72f609cb"),
        "name" : "Ratata",
        "description" : "Ratasana roxa demoníaca que transmite leptospirose",
        "type" : "lixo",
        "attack" : 1,
        "height" : 0.7
}
> db.pokemao.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```

ps: Não baixei o mongo-hacker ainda, mals.