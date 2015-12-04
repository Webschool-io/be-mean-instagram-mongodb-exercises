# MongoDB - Aula 04 - Exercício
autor: Luciano Silva de Lima


## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pickachu, Squirtle, Bulbassauro 
##    e Charmander.

> var query  = { "name" : { "$in" : [ /pikachu/i, /Squirtle/i, /Bulbassauro/i, /Charmander/i ] } }
> query
```
{
        "name" : {
                "$in" : [
                        /pikachu/i,
                        /Squirtle/i,
                        /Bulbassauro/i,
                        /Charmander/i
                ]
        }
}
```
> var attacks = ['estilingue','estalinho']
> attacks
```
[ "estilingue", "estalinho" ]
```
> var mod = {$pushAll:{moves:attacks}}
> mod
```
{ "$pushAll" : { "moves" : [ "estilingue", "estalinho" ] } }
```
> var options = {multi:true}
> options
```
{ "multi" : true }
```
> db.pokemons.find(query)
```
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "defense" : 30, "active" : true, "moves" : [ "investida" ] }
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando MANGA de
fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "defense" : 32, "active" : true, "moves" : [ "investida" ] }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "defense" : 33, "active" : true, "moves" : [ "investida" ] }
{ "_id" : ObjectId("565ccb66e8503ecc1aa4da32"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "defense" : 34, "active" : true, "moves" : [ "investida", "choque do trovão", "ataque rápido", "hidro bomba" ] }
```
> db.pokemons.update(query,mod,options)
```
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
```
> db.pokemons.find(query)
```
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "defense" : 30, "active" : true, "moves" : [ "investida", "estilingue", "estalinho" ] }
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando MANGA de
fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "defense" : 32, "active" : true, "moves" : [ "investida", "estilingue", "estalinho" ] }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "defense" : 33, "active" : true, "moves" : [ "investida", "estilingue", "estalinho" ] }
{ "_id" : ObjectId("565ccb66e8503ecc1aa4da32"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "defense" : 34, "active" : true, "moves" : [ "investida", "choque do trovão", "ataque rápido", "hidro bomba", "estilingue", "estalinho" ] }
```

## 2. Adicionar 1 movimento em todos os pokemons: 'devio'.

> query = {}
```
{ }
```
> query
```
{ }
```
> db.pokemons.find(query)
```
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 51, "height" : 0.4, "defense" : 30, "active" : true, "moves" : [ "investida", "estilingue", "estalinho" ] }
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando MANGA de
fofinho", "type" : "fogo", "attack" : 54, "height" : 0.6, "defense" : 32, "active" : true, "moves" : [ "investida", "estilingue", "estalinho" ] }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 50, "height" : 0.5, "defense" : 33, "active" : true, "moves" : [ "investida", "estilingue", "estalinho" ] }
{ "_id" : ObjectId("565ccda9e8503ecc1aa4da36"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : true, "moves" : [ "investida" ] }
{ "_id" : ObjectId("565dfb16e8503ecc1aa4da37"), "description" : "Pokemon de teste", "name" : "Testemon", "attack" : 8000, "defense" : 8000, "active" : true, "moves" : [ "investida" ] }
{ "_id" : ObjectId("565ccb66e8503ecc1aa4da32"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 57, "height" : 0.4, "defense" : 34, "active" : true, "moves" : [ "investida", "choque do trovão", "ataque rápido", "hidro bomba", "estilingue", "estalinho" ] }
{ "_id" : ObjectId("565f1cd2c6221b2b5721733f"), "active" : true, "moves" : [ "investida" ] }
```
> mod = {$push:{moves:"desvio"}}
```
{ "$push" : { "moves" : "desvio" } }
```
> mod
```
{ "$push" : { "moves" : "desvio" } }
```
> options
```
{ "multi" : true }
```
> db.pokemons.update(query, mod, options)
```
WriteResult({ "nMatched" : 7, "nUpserted" : 0, "nModified" : 7 })
> db.pokemons.find(query)
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 51, "height" : 0.4, "defense" : 30, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565ccda9e8503ecc1aa4da36"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : true, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565dfb16e8503ecc1aa4da37"), "description" : "Pokemon de teste", "name" : "Testemon", "attack" : 8000, "defense" : 8000, "active" : true, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565ccb66e8503ecc1aa4da32"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 57, "height" : 0.4, "defense" : 34, "active" : true, "moves" : [ "investida", "choque do trovão", "ataque rápido", "hidro bomba", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565f1cd2c6221b2b5721733f"), "active" : true, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando MANGA de
fofinho", "type" : "fogo", "attack" : 54, "height" : 0.6, "defense" : 32, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 50, "height" : 0.5, "defense" : 33, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
```

##  3. Adicionar o pokemon 'AindaNaoExisteMon'. Caso ele não exista com todos os dados com o valor
##    `null` e a descrição: "Sem maiores informações".

> query = {name:/AindaNaoExisteMon/i}
```
{ "name" : /AindaNaoExisteMon/i }
```
> query
```
{ "name" : /AindaNaoExisteMon/i }
```
> db.pokemons.find(query)
> mod = {$setOnInsert:{name:"AindaNaoExisteMon",description:"Sem maiores informações", type: null,attack:null,height:null,defense:null,active:null,moves:null}}
```
{
        "$setOnInsert" : {
                "name" : "AindaNaoExisteMon",
                "description" : "Sem maiores informações",
                "type" : null,
                "attack" : null,
                "height" : null,
                "defense" : null,
                "active" : null,
                "moves" : null
        }
}
```
> var options= {upsert:true}
> db.pokemons.update(query,mod,options)
```
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("5660664cc6221b2b57217341")
})
```
> db.pokemons.find(query)
```
{ "_id" : ObjectId("5660664cc6221b2b57217341"), "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "type" : null, "attack" : null, "height" : null, "defense" : null, "active" : null, "moves" : null }
```

##  4. Pesquisar todos os pokemons que possuam o ataque `investida`e mais um que você adicionou, escolha
##     seu pokemon favorito.

> query = {moves:{$all:['investida','estalinho']}}
```
{ "moves" : { "$all" : [ "investida", "estalinho" ] } }
```
> db.pokemons.find(query)
```
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 51, "height" : 0.4, "defense" : 30, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565ccb66e8503ecc1aa4da32"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 57, "height" : 0.4, "defense" : 34, "active" : true, "moves" : [ "investida", "choque do trovão", "ataque rápido", "hidro bomba", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando MANGA de
fofinho", "type" : "fogo", "attack" : 54, "height" : 0.6, "defense" : 32, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 50, "height" : 0.5, "defense" : 33, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
```

##  5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou,escolha seu pokemon favorito.

> query = { "moves" : { "$all" : [ "estilingue", "estalinho" ] } }
```
{ "moves" : { "$all" : [ "estilingue", "estalinho" ] } }
```
> db.pokemons.find(query)
```
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 51, "height" : 0.4, "defense" : 30, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565ccb66e8503ecc1aa4da32"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 57, "height" : 0.4, "defense" : 34, "active" : true, "moves" : [ "investida", "choque do trovão", "ataque rápido", "hidro bomba", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando MANGA de
fofinho", "type" : "fogo", "attack" : 54, "height" : 0.6, "defense" : 32, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 50, "height" : 0.5, "defense" : 33, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
```

##  6. Pesquisar **todos** que não são do tipo `elétrico`.

> query = {type:{$ne:"electric"}}
```
{ "type" : { "$ne" : "electric" } }
```
> db.pokemons.find(query)
```
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 51, "height" : 0.4, "defense" : 30, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565ccda9e8503ecc1aa4da36"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : true, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565dfb16e8503ecc1aa4da37"), "description" : "Pokemon de teste", "name" : "Testemon", "attack" : 8000, "defense" : 8000, "active" : true, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565f1cd2c6221b2b5721733f"), "active" : true, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando MANGA de
fofinho", "type" : "fogo", "attack" : 54, "height" : 0.6, "defense" : 32, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 50, "height" : 0.5, "defense" : 33, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("5660664cc6221b2b57217341"), "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "type" : null, "attack" : null, "height" : null, "defense" : null, "active" : null, "moves" : null }
```

##  7. Pesquisar **todos** pokemons que tenham o ataque ´investida´ **E** tenham a defesa **menor ou igual** a 49.

> query = {$and:[{moves:{$in:['investida']}}]}  --> pokemons que têm 'investida'
```
{
        "$and" : [
                {
                        "moves" : {
                                "$in" : [
                                        "investida"
                                ]
                        }
                }
        ]
}
```
> db.pokemons.find(query)
```
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 51, "height" : 0.4, "defense" : 30, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565ccda9e8503ecc1aa4da36"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : true, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565dfb16e8503ecc1aa4da37"), "description" : "Pokemon de teste", "name" : "Testemon", "attack" : 8000, "defense" : 8000, "active" : true, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565ccb66e8503ecc1aa4da32"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 57, "height" : 0.4, "defense" : 34, "active" : true, "moves" : [ "investida", "choque do trovão", "ataque rápido", "hidro bomba", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565f1cd2c6221b2b5721733f"), "active" : true, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando MANGA de
fofinho", "type" : "fogo", "attack" : 54, "height" : 0.6, "defense" : 32, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 50, "height" : 0.5, "defense" : 33, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
```
> query = {$and:[{moves:{$in:['investida']}},{defense:{$lte:49}}]} --> pokemons que têm 'investida' e 'defense' <=49
```
{
        "$and" : [
                {
                        "moves" : {
                                "$in" : [
                                        "investida"
                                ]
                        }
                },
                {
                        "defense" : {
                                "$lte" : 49
                        }
                }
        ]
}
```
> db.pokemons.find(query)
```
{ "_id" : ObjectId("565ccc51e8503ecc1aa4da33"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 51, "height" : 0.4, "defense" : 30, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565ccda9e8503ecc1aa4da36"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : true, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("565ccb66e8503ecc1aa4da32"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 57, "height" : 0.4, "defense" : 34, "active" : true, "moves" : [ "investida", "choque do trovão", "ataque rápido", "hidro bomba", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565cccd2e8503ecc1aa4da34"), "name" : "Charmander", "description" : "Esse é o cão chupando MANGA de
fofinho", "type" : "fogo", "attack" : 54, "height" : 0.6, "defense" : 32, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 50, "height" : 0.5, "defense" : 33, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
```

##  8. Remova **todos** os pokemons do tipo água e com attack menor que 50.

> query = {$and:[{ type: "água" },{attack:{$lt:50}}]}
```
{
        "$and" : [
                {
                        "type" : "água"
                },
                {
                        "attack" : {
                                "$lt" : 50
                        }
                }
        ]
}
```
> db.pokemons.find(query)
```
{ "_id" : ObjectId("565ccd4fe8503ecc1aa4da35"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "defense" : 33, "active" : true, "moves" : [ "investida", "estilingue", "estalinho", "desvio" ] }
```
> db.pokemons.remove(query)
```
WriteResult({ "nRemoved" : 1 })
```
> query
```
{
        "$and" : [
                {
                        "type" : "água"
                },
                {
                        "attack" : {
                                "$lt" : 50
                        }
                }
        ]
}
```
> db.pokemons.find(query)
>












































