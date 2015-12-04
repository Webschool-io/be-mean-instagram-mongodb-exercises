##Criação do database ```be-mean-pokemons```
> use be-mean-pokemons
```
switched to db be-mean-pokemons
```

##Exibindo os bancos do servidor
> show dbs
```
be-mean            0.078GB
be-mean-instagram  0.078GB
local              0.078GB
test               0.078GB
```

##Exibindo as coleções do banco corrente (```be-mean-pokemons```)
> show collections
```
>
```

##Inserindo o primeiro pokemon na coleção ```pokemons```
> var poke = {  "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "defense" : 34 }
> poke
```
{
        "name" : "Pikachu",
        "description" : "Rato elétrico bem fofinho",
        "type" : "electric",
        "attack" : 55,
        "height" : 0.4,
        "defense" : 34
}
```
> db.pokemons.insert(poke)
```
WriteResult({ "nInserted" : 1 })
```

##Inserindo o segundo pokemon na coleção ```pokemons```
> poke = {  "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49,
"height" : 0.4, "defense" : 30 }
```
{
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "height" : 0.4,
        "defense" : 30
}
```
> db.pokemons.insert(poke)
```
WriteResult({ "nInserted" : 1 })
```

##Inserindo o terceiro pokemon na coleção ```pokemons```
> poke = {  "name" : "Charmander", "description" : "Esse é o cão chupando de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "defense" : 32 }

```
{
    "name" : "Charmander",
        "description" : "Esse é o cão chupando de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "height" : 0.6,
        "defense" : 32
}
```
> db.pokemons.insert(poke)
```
WriteResult({ "nInserted" : 1 })
```

##Inserindo o quarto pokemon na coleção ```pokemons```
> poke = {  "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5,"defense" : 33 }
```
{
		"name" : "Squirtle",
        "description" : "Ejeta água que passarinho não bebe",
        "type" : "água",
        "attack" : 48,
        "height" : 0.5,
        "defense" : 33
}
```
> db.pokemons.insert(poke)
```
WriteResult({ "nInserted" : 1 })
```
##Inserindo o quinto pokemon na coleção ```pokemons```
> poke ={  "name" : "Caterpie", "description" : "Larva lutadora", "type": "inseto", "attack" : 30, "height" :0.3, "defense" : 35 }
```
{
		"name" : "Caterpie",
        "description" : "Larva lutadora",
        "type" : "inseto",
        "attack" : 30,
        "height" : 0.3,
        "defense" : 35
}
```
> db.pokemons.insert(poke)
```
WriteResult({ "nInserted" : 1 })
```

##Listagens dos pokemons da coleção
> db.pokemons.find()
```
{ "_id" : ObjectId("565ccb66e8503ecc1aa4da32"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "defense" : 34 }
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "defense" : 30 }
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando
de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "defense" : 32 }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "defense" : 33 }
{ "_id" : ObjectId("565ccda9e8503ecc1aa4da36"), "name" : "Caterpie", "description" : "Larva lutadora", "type"
: "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }
> db.pokemons.find()
{ "_id" : ObjectId("565ccb66e8503ecc1aa4da32"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "defense" : 34 }
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "defense" : 30 }
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando
de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "defense" : 32 }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "defense" : 33 }
{ "_id" : ObjectId("565ccda9e8503ecc1aa4da36"), "name" : "Caterpie", "description" : "Larva lutadora", "type"
: "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }
```

## Buscando o pokemon `Charmander`
> var filter = {"name":"Charmander"}
> var poke = db.pokemons.findOne(filter)
> poke
```
{
        "_id" : ObjectId("565cccd2e8503ecc1aa4da34"),
        "name" : "Charmander",
        "description" : "Esse é o cão chupando de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "height" : 0.6,
        "defense" : 32
}
```

##Alterando a descrição do pokemon ```Charmander```

> poke.description = "Esse é o cão chupando MANGA de fofinho"
```
Esse é o cão chupando MANGA de fofinho
```
> db.pokemons.save(poke)
```
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```
> poke
```
{
        "_id" : ObjectId("565cccd2e8503ecc1aa4da34"),
        "name" : "Charmander",
        "description" : "Esse é o cão chupando MANGA de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "height" : 0.6,
        "defense" : 32
}
```