# MongoDB - Aula 04 - Exercício
autor: **Francisco Henrique Ruiz Valério**

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander. ##

> var query = { $or: [{ name: /pikachu/i}, {name:/squirtle/i}, {name:/bulbassauro/i}, {name:/charmander/i }]}
> var mod = { $pushAll: { moves: ['run', 'esquiva' ] }}
> var options = { multi: true }
> db.pokemons.update(query,mod,options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
>
> db.pokemons.find(query)
{ "_id" : ObjectId("56429a2a65048c35cec000c5"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "choque do trovão", "run", "esquiva" ] }
{ "_id" : ObjectId("56429aaa65048c35cec000c6"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "run", "esquiva" ] }
{ "_id" : ObjectId("56429adb65048c35cec000c7"), "name" : "Charmander", "description" : "Esse é o cão chupando manda de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "run", "esquiva" ] }
{ "_id" : ObjectId("56429b0265048c35cec000c8"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "run", "esquiva" ] }
>

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

> var query = {}
> var mod = { $push: { moves: 'desvio' }}
> var options = { multi: true }
> db.pokemons.update(query,mod,options)
WriteResult({ "nMatched" : 6, "nUpserted" : 0, "nModified" : 6 })
>
> db.pokemons.find(query)
{ "_id" : ObjectId("56429a2a65048c35cec000c5"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "choque do trovão", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429aaa65048c35cec000c6"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429b0265048c35cec000c8"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429cd99f88c77ae6584059"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("56429cf29f88c77ae658405a"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("56429adb65048c35cec000c7"), "name" : "Charmander", "description" : "Esse é o cão chupando manda de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "run", "esquiva", "desvio" ] }
>

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

> var query = { name: /AindaNaoExisteMon/i }
> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", description: "Sem maiores informações", attack: null, defense: null, height: null, type: null, active: null, moves: null }}
> var options = {upsert: true }
> db.pokemons.update(query,mod,options)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("564d3541877f2b6605bc8035")
})
>
> db.pokemons.find(query)
{ "_id" : ObjectId("564d3541877f2b6605bc8035"), "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "attack" : null, "defense" : null, "height" : null, "type" : null, "active" : null, "moves" : null }
>

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

> var query = { moves: { $in: [/investida/i, /hidro bomba/i] } }
> db.pokemons.find(query)
{ "_id" : ObjectId("56429a2a65048c35cec000c5"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "choque do trovão", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429aaa65048c35cec000c6"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429b0265048c35cec000c8"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429cd99f88c77ae6584059"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("56429cf29f88c77ae658405a"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("56429adb65048c35cec000c7"), "name" : "Charmander", "description" : "Esse é o cão chupando manda de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "run", "esquiva", "desvio" ] }
>

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

> var query = { moves: { $all: [/run/i, /esquiva/i] } }
> db.pokemons.find(query)
{ "_id" : ObjectId("56429a2a65048c35cec000c5"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "choque do trovão", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429aaa65048c35cec000c6"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429b0265048c35cec000c8"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429adb65048c35cec000c7"), "name" : "Charmander", "description" : "Esse é o cão chupando manda de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "run", "esquiva", "desvio" ] }
>

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

> var query = { type: { $ne: "electric" } }
> db.pokemons.find(query)
{ "_id" : ObjectId("56429aaa65048c35cec000c6"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429b0265048c35cec000c8"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429cd99f88c77ae6584059"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("56429cf29f88c77ae658405a"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("56429adb65048c35cec000c7"), "name" : "Charmander", "description" : "Esse é o cão chupando manda de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("564d3541877f2b6605bc8035"), "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "attack" : null, "defense" : null, "height" : null, "type" : null, "active" : null, "moves" : null }
>

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

> var query = { $and: [ { moves : { $in: [/investida/i] } }, { defense: { $not: { $lte: 49 } } } ] }
> db.pokemons.find(query)
{ "_id" : ObjectId("56429a2a65048c35cec000c5"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "choque do trovão", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429aaa65048c35cec000c6"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429b0265048c35cec000c8"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "hidro bomba", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429cf29f88c77ae658405a"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("56429adb65048c35cec000c7"), "name" : "Charmander", "description" : "Esse é o cão chupando manda de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "run", "esquiva", "desvio" ] }
>

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

> var query = { $and: [{ type: { $in: [/água/i] }}, { attack: { $lt: 50 } }] }
> db.pokemons.remove(query)
WriteResult({ "nRemoved" : 1 })
>


## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not. ##

**$ne (not Equal): Com esse operador podemos fazer uma query com uma negação, Exemplo: Quero buscar todos os pokemons que não sejam do tipo electric. LEMBRANDO QUE ESSE OPERADO NAO ACEITA REGEX. **

> var query = { type: {$ne: 'electric' }}
> db.pokemons.find(query)
{ "_id" : ObjectId("56429aaa65048c35cec000c6"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429cd99f88c77ae6584059"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("56429cf29f88c77ae658405a"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("56429adb65048c35cec000c7"), "name" : "Charmander", "description" : "Esse é o cão chupando manda de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("564d3541877f2b6605bc8035"), "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "attack" : null, "defense" : null, "height" : null, "type" : null, "active" : null, "moves" : null }
>


**$not (not): Com esse operador eu posso fazer uma query que encontre todos os objetos que não possua o valor que for passado Exemplo: Quero busca todos pokemons que nao tenham o nome de pikachu. ESSE OPERADOR ACEITA REGEX**

> var query = { name: {$not: /pikachu/i }}
> db.pokemons.find(query)
{ "_id" : ObjectId("56429aaa65048c35cec000c6"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "folha navalha", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("56429cd99f88c77ae6584059"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("56429cf29f88c77ae658405a"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("56429adb65048c35cec000c7"), "name" : "Charmander", "description" : "Esse é o cão chupando manda de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "lança-chamas", "run", "esquiva", "desvio" ] }
{ "_id" : ObjectId("564d3541877f2b6605bc8035"), "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "attack" : null, "defense" : null, "height" : null, "type" : null, "active" : null, "moves" : null }
>






