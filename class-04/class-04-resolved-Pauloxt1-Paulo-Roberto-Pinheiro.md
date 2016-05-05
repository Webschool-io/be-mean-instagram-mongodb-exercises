# MongoDB - Aula 04 - Exercício
Autor: Paulo Roberto

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
> query
{
        "$or" : [
                {
                        "name" : /pikachu/i
                },
                {
                        "name" : /squirtle/i
                },
                {
                        "name" : /bulbassauro/i
                },
                {
                        "name" : /charmander/i
                }
        ]
}
> mod
{ "$pushAll" : { "moves" : [ "poder1", "poder2" ] } }
> options
{ "multi" : 1 }
> db.pokemons.update(query,mod,options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
```
## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
> var query = {}
> var mod = {"$push":{moves:'desvio'}}
> db.pokemons.update(query,mod,options)
WriteResult({ "nMatched" : 7, "nUpserted" : 0, "nModified" : 7 })
```
## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
> var query = {name:'AindaNaoExisteMon'}
> query
{ "name" : "AindaNaoExisteMon" }
> mod = {$setOnInsert:{name:null, description:'Sem maiores informações',type:null, attack:null, defense:null, height:null,  moves:[]}}
{
        "$setOnInsert" : {
                "name" : null,
                "description" : "Sem maiores informações",
                "type" : null,
                "attack" : null,
                "defense" : null,
                "height" : null,
                "moves" : [ ]
        }
}
> var options = {upsert: 1}
> db.pokemons.update(query,mod,options)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("56802475434ffa9b22e104e9")
})
> db.pokemons.find({"_id" : ObjectId("56802475434ffa9b22e104e9")})
{ "_id" : ObjectId("56802475434ffa9b22e104e9"), "name" : null, "description" : "Sem maiores informações", "type" : null, 
"attack" : null, "defense" : null, "height" : null, "moves" : [ ] }
```
## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
> var query =  {moves:{$all:['investida','poder1']}}
> db.pokemons.find(query)
{ "_id" : ObjectId("567ae99e38081f084b27fc7e"), "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, 
"height" : 0.4, "name" : "Pikachu", "moves" : [ "investida", "choque do trovão", "poder1", "poder2", "desvio" ], "active" : false }

{ "_id" : ObjectId("567aeac938081f084b27fc7f"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", 
"type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "poder1", "poder2", "desvio" ] }

{ "_id" : ObjectId("567aeadc38081f084b27fc80"), "name" : "Charmander", "description" : "Esse é o cão chupando manga fofinho", 
"type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "poder1", "poder2", "desvio" ] }

{ "_id" : ObjectId("567aeae838081f084b27fc81"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", 
"type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "poder1", "poder2", "desvio" ] }
```
## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
> var query =  {moves:{$all:['poder2','poder1', 'desvio']}}
> db.pokemons.find(query)
{ "_id" : ObjectId("567ae99e38081f084b27fc7e"), "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, 
"height" : 0.4, "name" : "Pikachu", "moves" : [ "investida", "choque do trovão", "poder1", "poder2", "desvio" ], "active" : false }

{ "_id" : ObjectId("567aeac938081f084b27fc7f"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", 
"attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "poder1", "poder2", "desvio" ] }

{ "_id" : ObjectId("567aeadc38081f084b27fc80"), "name" : "Charmander", "description" : "Esse é o cão chupando manga fofinho", 
"type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "poder1", "poder2", "desvio" ] }

{ "_id" : ObjectId("567aeae838081f084b27fc81"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", 
"type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "poder1", "poder2", "desvio" ] }
```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
> var query = {type:/elétrico/i}
> db.pokemons.find(query)
> var query = {type:/eletric/i}
> db.pokemons.find(query)

{ "_id" : ObjectId("567ae99e38081f084b27fc7e"), "description" : "Rato elétrico bem fofinho", "type" : "eletric", 
"attack" : 55, "height" : 0.4, "name" : "Pikachu", "moves" : [ "investida", "choque do trovão", "poder1", "poder2", "desvio" ], "active" : false }
```
## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
> query
{
        "$and" : [
                {
                        "attack" : {
                                "$in" : [
                                        "investida"
                                ]
                        }
                },
                {
                        "defesa" : {
                                "$gt" : 49
                        }
                }
        ]
}
> db.pokemons.find(query)
```
## Remova **todos** os pokemons do tipo água e com attack menor que 50
```
> var query = {$and:[{'type':/água/i}, {attack:{$lt:50}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("567aeae838081f084b27fc81"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe",
"type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "poder1", "poder2", "desvio" ] }
```
