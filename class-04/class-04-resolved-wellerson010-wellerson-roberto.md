# MongoDB - Aula 04 - Exercício
autor: Wellerson Roberto

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
> db.pokemons.update({$or: [{name: "Ivysaur"},{name: "Poliwag"},{name: "Girafarig"}, {name: "Linoone"}]},{$pushAll: {moves: ["investida","raio elétrico"]}}, {multi: true})
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
>
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
> db.pokemons.update({},{$push: {moves: "desvio"}}, {multi: true});
WriteResult({ "nMatched" : 5, "nUpserted" : 0, "nModified" : 5 })
>
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
> db.pokemons.update({name: "AindaNaoExisteMon"}, {$setOnInsert: {name: "AindaNaoExisteMon",attack: null, moves: null, defense: null, description: "Sem maiores informações", type: null}},{upsert: true})
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("565147a7b68e52581d1c4b88")
})
>
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
> db.pokemons.find({moves: {$in: ["investida","raio elétrico"]}})
{ "_id" : ObjectId("5650a2b9414fed410978a3a7"), "name" : "Ivysaur", "description" : "Um pokemon com uma rosa em cima, bem viadão", "attack" : 62, "defense" : 63, "height" : 10, "moves" : [ "investida", "raio elétrico", "desvio" ] }
{ "_id" : ObjectId("5650a2b9414fed410978a3a8"), "name" : "Poliwag", "description" : "Um pokemon locão com uma parada no meio da barriga, dahora mesmo", "attack" : 50, "defense" : 40, "height" : 6, "moves" : [ "investida", "raio elétrico", "desvio" ] }
{ "_id" : ObjectId("5650a2b9414fed410978a3a9"), "name" : "Girafarig", "description" : "Um pokemon que é uma girafa com outra parada aí", "attack" : 80, "defense" : 65, "height" : 15, "moves" : [ "investida", "raio elétrico", "desvio" ] }
{ "_id" : ObjectId("5650a2b9414fed410978a3aa"), "name" : "Linoone", "description" : "Parece um roedor...", "attack" : 70, "defense" : 61, "height" : 5, "moves" : [ "investida", "raio elétrico", "desvio" ] }
>
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
> db.pokemons.find({moves: {$all: ["investida","raio elétrico"]}})
{ "_id" : ObjectId("5650a2b9414fed410978a3a7"), "name" : "Ivysaur", "description" : "Um pokemon com uma rosa em cima, bem viadão", "attack" : 62, "defense" : 63, "height" : 10, "moves" : [ "investida", "raio elétrico", "desvio" ] }
{ "_id" : ObjectId("5650a2b9414fed410978a3a8"), "name" : "Poliwag", "description" : "Um pokemon locão com uma parada no meio da barriga, dahora mesmo", "attack" : 50, "defense" : 40, "height" : 6, "moves" : [ "investida", "raio elétrico", "desvio" ] }
{ "_id" : ObjectId("5650a2b9414fed410978a3a9"), "name" : "Girafarig", "description" : "Um pokemon que é uma girafa com outra parada aí", "attack" : 80, "defense" : 65, "height" : 15, "moves" : [ "investida", "raio elétrico", "desvio" ] }
{ "_id" : ObjectId("5650a2b9414fed410978a3aa"), "name" : "Linoone", "description" : "Parece um roedor...", "attack" : 70, "defense" : 61, "height" : 5, "moves" : [ "investida", "raio elétrico", "desvio" ] }
>

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
> db.pokemons.find({type: {$ne: "elétrico"}});
{ "_id" : ObjectId("5650a2b9414fed410978a3a7"), "name" : "Ivysaur", "description" : "Um pokemon com uma rosa em cima, bem viadão", "attack" : 62, "defense" : 63, "height" : 10, "moves" : [ "investida", "raio elétrico", "desvio" ] }
{ "_id" : ObjectId("5650a2b9414fed410978a3a8"), "name" : "Poliwag", "description" : "Um pokemon locão com uma parada no meio da barriga, dahora mesmo", "attack" : 50, "defense" : 40, "height" : 6, "moves" : [ "investida", "raio elétrico", "desvio" ] }
{ "_id" : ObjectId("5650a2b9414fed410978a3a9"), "name" : "Girafarig", "description" : "Um pokemon que é uma girafa com outra parada aí", "attack" : 80, "defense" : 65, "height" : 15, "moves" : [ "investida", "raio elétrico", "desvio" ] }
{ "_id" : ObjectId("5650a2b9414fed410978a3aa"), "name" : "Linoone", "description" : "Parece um roedor...", "attack" : 70, "defense" : 61, "height" : 5, "moves" : [ "investida", "raio elétrico", "desvio" ] }
{ "_id" : ObjectId("5650a2b9414fed410978a3ab"), "name" : "Bibarel", "description" : "Biba...rel", "attack" : 85, "defense" : 60, "height" : 10, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("565147a7b68e52581d1c4b88"), "name" : "AindaNaoExisteMon", "attack" : null, "moves" : null, "defense" : null, "description" : "Sem maiores informações", "type" : null }
>

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
> db.pokemons.find({$and: [{moves: {$in: ["investida"]}},{defense: {$not: {$lte: 49}}}]})
{ "_id" : ObjectId("5650a2b9414fed410978a3a7"), "name" : "Ivysaur", "description" : "Um pokemon com uma rosa em cima, bem viadão", "attack" : 62, "defense" : 63, "height" : 10, "moves" : [ "investida", "raio elétrico", "desvio" ] }
{ "_id" : ObjectId("5650a2b9414fed410978a3a9"), "name" : "Girafarig", "description" : "Um pokemon que é uma girafa com outra parada aí", "attack" : 80, "defense" : 65, "height" : 15, "moves" : [ "investida", "raio elétrico", "desvio" ] }
{ "_id" : ObjectId("5650a2b9414fed410978a3aa"), "name" : "Linoone", "description" : "Parece um roedor...", "attack" : 70, "defense" : 61, "height" : 5, "moves" : [ "investida", "raio elétrico", "desvio" ] }
>

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
> db.pokemons.remove({type: "água", attack: {$lt: 50}})
WriteResult({ "nRemoved" : 0 })
>

##Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not.##

$ne é um operador de comparação, que serve para retornar um documento cujo valor do campo seja diferente do valor passado. 
$not é um operador lógico que retorna documentos que não batam com a expressão. Incluindo documentos que não contenham o campo.