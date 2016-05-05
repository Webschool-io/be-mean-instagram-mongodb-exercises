# MongoDB - Aula 04 / 05 - Exercício
autor: Eduardo Chaves

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
> var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}
> var atack = ['soquinho', 'voadora']
> var mod = {$pushAll:{moves:atack}}
> var options = {multi:true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
>
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
> var query = {}
> var options = {multi: true}
> var mod = {$push: {moves: 'desvio'}}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 17, "nUpserted" : 0, "nModified" : 17 })
>
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
> var query = {name: /AindaNaoExisteMon/i}
> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', "description" : null, "type" : null, "attack" : null, "height" : null, "defense" : null}, }
> var options = {upsert: true}
> db.pokemons.update(query, mod, options)
WriteResult({
	"nMatched" : 0,
	"nUpserted" : 1,
	"nModified" : 0,
	"_id" : ObjectId("56507799a32e7cb3f9e948c6")
})
> db.pokemons.find(query)
{ "_id" : ObjectId("56507799a32e7cb3f9e948c6"), "name" : "AindaNaoExisteMon", "description" : null, "type" : null, "attack" : null, "height" : null, "defense" : null }
>
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
> var query = {moves: {$in: [/soquinho/i, /investida/i]}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564fd636793b2b526913ebd6"), "name" : "Pikachu", "description" : "Rato eletrico bem fofinho", "type" : "electrico", "attack" : 55, "height" : 0.4, "defense" : 32, "moves" : [ "soquinho", "voadora", "desvio" ] }
{ "_id" : ObjectId("564fd636793b2b526913ebd7"), "name" : "Bulbassauro", "description" : "Monstro com rabo de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "defense" : 41, "moves" : [ "soquinho", "voadora", "desvio" ] }
{ "_id" : ObjectId("564fd636793b2b526913ebd9"), "name" : "Squirtle", "description" : "Animal com esguinchos de água", "type" : "agua", "attack" : 55, "height" : 0.5, "defense" : 48, "moves" : [ "soquinho", "voadora", "desvio" ] }
{ "_id" : ObjectId("564fd636793b2b526913ebda"), "name" : "Charmander", "description" : "Monstro que lança fogo pela boca", "type" : "fogo", "attack" : 52, "height" : 0.6, "defense" : 43, "moves" : [ "soquinho", "voadora", "desvio" ] }
>

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
> var query = {moves: {$in: [/soquinho/i, /voadora/i, /desvio/i]}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564f9168793b2b526913ebc8"), "name" : "Ivysaur", "description" : "Mostro de feito de plantas", "type" : "grama", "attack" : 65, "defense" : 41, "height" : 1, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564f9168793b2b526913ebc9"), "name" : "Blastoise", "description" : "Monstro de água muito poderoso", "type" : "água", "attack" : 75, "defense" : "32", "height" : 1.6, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564f9168793b2b526913ebca"), "name" : "Venusaur", "description" : "Monstro de veneno muito poderoso", "type" : "grama", "attack" : 82, "defense" : "68", "height" : 2.2, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564f9168793b2b526913ebcb"), "name" : "Mega Venusaur", "description" : "Monstro de grama e veneno extremamente poderoso", "type" : "grama", "attack" : 100, "defense" : "90", "height" : 2.4, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564f9168793b2b526913ebcc"), "name" : "Charmeleon", "description" : "Monstro de Fogo muito poderoso", "type" : "fogo", "attack" : 32, "defense" : "31", "height" : 1.1, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebce"), "name" : "Butterfree", "description" : "Inseto Venenoso que repele água", "type" : "inseto", "attack" : 45, "defense" : 50, "height" : 0.8, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebcf"), "name" : "Arbok", "description" : "Um monstro cavernoso e barrigudo.", "type" : "veneno", "attack" : 85, "defense" : 69, "height" : 0.6, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebd0"), "name" : "Ninetales", "description" : "Monstro de 9 caldas", "type" : "fogo", "attack" : 76, "defense" : 75, "height" : 0.3, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebd1"), "name" : "Grimer", "description" : "Limpa dejetos fecais", "type" : "veneno", "attack" : 80, "defense" : 50, "height" : 0.4, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebd2"), "name" : "Dewgong", "description" : "Estoca energia termal no corpo", "type" : "água", "attack" : 70, "defense" : 80, "height" : 0.2, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebd3"), "name" : "Beedrill", "description" : "Um dos Mais perigosos insetos", "type" : "inseto", "attack" : 90, "defense" : 40, "height" : 10, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebd4"), "name" : "Nidorina", "description" : "Filho do Suissamon", "type" : "veneno", "attack" : 62, "defense" : 67, "height" : 0.4, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564fd636793b2b526913ebd6"), "name" : "Pikachu", "description" : "Rato eletrico bem fofinho", "type" : "electrico", "attack" : 55, "height" : 0.4, "defense" : 32, "moves" : [ "soquinho", "voadora", "desvio" ] }
{ "_id" : ObjectId("564fd636793b2b526913ebd7"), "name" : "Bulbassauro", "description" : "Monstro com rabo de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "defense" : 41, "moves" : [ "soquinho", "voadora", "desvio" ] }
{ "_id" : ObjectId("564fd636793b2b526913ebd8"), "name" : "Caterpie", "description" : "Lava Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564fd636793b2b526913ebd9"), "name" : "Squirtle", "description" : "Animal com esguinchos de água", "type" : "agua", "attack" : 55, "height" : 0.5, "defense" : 48, "moves" : [ "soquinho", "voadora", "desvio" ] }
{ "_id" : ObjectId("564fd636793b2b526913ebda"), "name" : "Charmander", "description" : "Monstro que lança fogo pela boca", "type" : "fogo", "attack" : 52, "height" : 0.6, "defense" : 43, "moves" : [ "soquinho", "voadora", "desvio" ] }

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
> var query = {type: {$ne: 'electrico'}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564f9168793b2b526913ebc8"), "name" : "Ivysaur", "description" : "Mostro de feito de plantas", "type" : "grama", "attack" : 65, "defense" : 41, "height" : 1, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564f9168793b2b526913ebc9"), "name" : "Blastoise", "description" : "Monstro de água muito poderoso", "type" : "água", "attack" : 75, "defense" : "32", "height" : 1.6, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564f9168793b2b526913ebca"), "name" : "Venusaur", "description" : "Monstro de veneno muito poderoso", "type" : "grama", "attack" : 82, "defense" : "68", "height" : 2.2, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564f9168793b2b526913ebcb"), "name" : "Mega Venusaur", "description" : "Monstro de grama e veneno extremamente poderoso", "type" : "grama", "attack" : 100, "defense" : "90", "height" : 2.4, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564f9168793b2b526913ebcc"), "name" : "Charmeleon", "description" : "Monstro de Fogo muito poderoso", "type" : "fogo", "attack" : 32, "defense" : "31", "height" : 1.1, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebce"), "name" : "Butterfree", "description" : "Inseto Venenoso que repele água", "type" : "inseto", "attack" : 45, "defense" : 50, "height" : 0.8, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebcf"), "name" : "Arbok", "description" : "Um monstro cavernoso e barrigudo.", "type" : "veneno", "attack" : 85, "defense" : 69, "height" : 0.6, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebd0"), "name" : "Ninetales", "description" : "Monstro de 9 caldas", "type" : "fogo", "attack" : 76, "defense" : 75, "height" : 0.3, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebd1"), "name" : "Grimer", "description" : "Limpa dejetos fecais", "type" : "veneno", "attack" : 80, "defense" : 50, "height" : 0.4, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebd2"), "name" : "Dewgong", "description" : "Estoca energia termal no corpo", "type" : "água", "attack" : 70, "defense" : 80, "height" : 0.2, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebd3"), "name" : "Beedrill", "description" : "Um dos Mais perigosos insetos", "type" : "inseto", "attack" : 90, "defense" : 40, "height" : 10, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564faaaf793b2b526913ebd4"), "name" : "Nidorina", "description" : "Filho do Suissamon", "type" : "veneno", "attack" : 62, "defense" : 67, "height" : 0.4, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564fd636793b2b526913ebd7"), "name" : "Bulbassauro", "description" : "Monstro com rabo de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "defense" : 41, "moves" : [ "soquinho", "voadora", "desvio" ] }
{ "_id" : ObjectId("564fd636793b2b526913ebd8"), "name" : "Caterpie", "description" : "Lava Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564fd636793b2b526913ebd9"), "name" : "Squirtle", "description" : "Animal com esguinchos de água", "type" : "agua", "attack" : 55, "height" : 0.5, "defense" : 48, "moves" : [ "soquinho", "voadora", "desvio" ] }
{ "_id" : ObjectId("564fd636793b2b526913ebda"), "name" : "Charmander", "description" : "Monstro que lança fogo pela boca", "type" : "fogo", "attack" : 52, "height" : 0.6, "defense" : 43, "moves" : [ "soquinho", "voadora", "desvio" ] }
{ "_id" : ObjectId("56507799a32e7cb3f9e948c6"), "name" : "AindaNaoExisteMon", "description" : null, "type" : null, "attack" : null, "height" : null, "defense" : null }
>
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
> var query = {$and: [{moves: {$in: ['investida']}}, {defense: {lte: 49}}]}
> db.pokemons.find(query)
>
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
> var query = {$and: [{type: /água/i}, {attack: {lt: 50}}]}
> db.pokemons.remove(query)
WriteResult({ "nRemoved" : 0 })
>
```
