# MongoDB - Aula 02 - Exercício
autor: Davidson da Silva Nascimento
## Criar DataBase chamada be-mean-pokemons (passo 1)
```js
> use be-mean-pokemons
switched to db be-mean-pokemons
>
```
## Listagem das databases (passo 2)
```js
> show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
local              0.078GB
>
```
## Listagem das coleções (passo 3)
##### Antes de criar coleção pokemons:
```js
> show collections
>
```
#### Criando coleção pokemons e listando:
```js
> db.createCollection('pokemons')
{ "ok" : 1 }
> show collections
pokemons
system.indexes
>
```
## Cadastro dos pokemons (passo 4)
```js
var pokemonsAdd = [
    {"name":"Mewtwo","description":"Foi criado por um cientista depois de anos de manipulação genética horrível e experimentos de engenharia DNA.","attack":110,"defense":90,"height":2.0},
    {"name":"Charizard","description":"Cospe fogo que é quente o suficiente para derreter rochas. Conhecido por causar incêndios florestais sem querer.","attack":84,"defense":78,"height":1.7},
    {"name":"Yveltal","description":"Quando sua vida chega ao fim, ele absorve a energia da vida de todos os seres vivos e se transforma em um casulo mais uma vez.","attack":131,"defense":95,"height":5.8},{"name":"Alakazam","description":"Um aroma sedutor exala de sua flor. A fragrância deixa calmo seus oponentes em uma batalha.","attack":50,"defense":45,"height":1.5},
    {"name":"Zoroark","description":"Eles protegem seu covil com cenário ilusório.","attack":105,"defense":60,"height":1.6},
    {"name":"Zubat","description":"Quando ela cresce, ela lança a pele, cobre-se com seda, e torna-se um casulo.","attack":45,"defense":35,"height":0.8},
    {"name":"Aggron","description":"Suas balas de água pode pregar precisamente latas de uma distância de mais de 160 pés.","attack":110,"defense":180,"height":2.1}
]
> db.pokemons.insert(pokemonsAdd)
BulkWriteResult({
        "writeErrors" : [ ],
        "writeConcernErrors" : [ ],
        "nInserted" : 7,
        "nUpserted" : 0,
        "nMatched" : 0,
        "nModified" : 0,
        "nRemoved" : 0,
        "upserted" : [ ]
})
>
```
## Lista dos pokemons (passo 5)
```js
> db.pokemons.find().pretty()
{
        "_id" : ObjectId("565222b99a8f50a878c10890"),
        "name" : "Mewtwo",
        "description" : "Foi criado por um cientista depois de anos de manipulação genética horrível e experimentos de engenharia DNA.",
        "attack" : 110,
        "defense" : 90,
        "height" : 2
}
{
        "_id" : ObjectId("565222b99a8f50a878c10891"),
        "name" : "Charizard",
        "description" : "Cospe fogo que é quente o suficiente para derreter rochas. Conhecido por causar incêndios florestais sem querer.",
        "attack" : 84,
        "defense" : 78,
        "height" : 1.7
}
{
        "_id" : ObjectId("565222b99a8f50a878c10892"),
        "name" : "Yveltal",
        "description" : "Quando sua vida chega ao fim, ele absorve a energia da vida de todos os seres vivos e se transforma em um casulo mais uma vez.",
        "attack" : 131,
        "defense" : 95,
        "height" : 5.8
}
{
        "_id" : ObjectId("565222b99a8f50a878c10893"),
        "name" : "Alakazam",
        "description" : "Um aroma sedutor exala de sua flor. A fragrância deixa calmo seus oponentes em uma batalha.",
        "attack" : 50,
        "defense" : 45,
        "height" : 1.5
}
{
        "_id" : ObjectId("565222b99a8f50a878c10894"),
        "name" : "Zoroark",
        "description" : "Eles protegem seu covil com cenário ilusório.",
        "attack" : 105,
        "defense" : 60,
        "height" : 1.6
}
{
        "_id" : ObjectId("565222b99a8f50a878c10895"),
        "name" : "Zubat",
        "description" : "Quando ela cresce, ela lança a pele, cobre-se com seda, e torna-se um casulo.",
        "attack" : 45,
        "defense" : 35,
        "height" : 0.8
}
{
        "_id" : ObjectId("565222b99a8f50a878c10896"),
        "name" : "Aggron",
        "description" : "Suas balas de água pode pregar precisamente latas de um a distância de mais de 160 pés.",
        "attack" : 110,
        "defense" : 180,
        "height" : 2.1
}
>
```
## Busque um pokemon a sua escolha, que acabou de ser inserido, e armazene-o em uma variável chamada ```poke```
```js
> var poke = db.pokemons.findOne({name: "Mewtwo"})
> poke
{
        "_id" : ObjectId("565222b99a8f50a878c10890"),
        "name" : "Mewtwo",
        "description" : "Foi criado por um cientista depois de anos de manipulação genética horrível e experimentos de engenharia DNA.",
        "attack" : 110,
        "defense" : 90,
        "height" : 2
}
>
```
## Atualização, modifique sua ```description``` e salvê-o (passo 6)
```js
> poke.description = "Pokemon sangue nu ZÓI"
Pokemon sangue nu ZÓI
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
>
```