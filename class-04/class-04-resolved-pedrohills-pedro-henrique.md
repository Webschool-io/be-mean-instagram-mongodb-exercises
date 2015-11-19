# MongoDB - Aula 04 - Exercício
autor: Pedro Henrique

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```js
> var query = {$or: [{name: /pikachu/i},{ name: /squirtle/i},{name: /bulbasauro/i},{name: /charmander/i}]}
> var mod = {$set: {'moves' : ['Ataque 1', 'Ataque 2']}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({"nMatched" : 4,"nUpserted" : 0,"nModified" : 4})
```
## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```js
> var query = {}
> var mod = {$push: {moves: "Desvio"}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 6, "nUpserted" : 0, "nModified" : 6 })

```


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```js
> var query = {name: /aindanaoexistemon/i}
> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", description: "Sem maiores informações", type: null, attack: null, height: null, defense: null, moves: []}}
> var options = {upsert: true}
> db.pokemons.update(query, mod, options)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("564c593abc3caee13b9622af")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```js
> var query = {moves: {$all: ['Ataque 1', 'Ataque 2']}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564291b535f1b5fe4ead743f"),
        "name" : "Charmander",
        "description" : "Um pokémon de fogo muito forte",
        "attack" : 40,
        "defense" : 35,
        "height" : 0.4,
        "moves" : [
                "Ataque 1",
                "Ataque 2",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7440"),
        "name" : "Squirtle",
        "description" : "Um pokémon de água muito forte",
        "attack" : 37,
        "defense" : 30,
        "height" : 0.3,
        "moves" : [
                "Ataque 1",
                "Ataque 2",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7441"),
        "name" : "Bulbasauro",
        "description" : "Um pokémon de planta muito forte",
        "attack" : 45,
        "defense" : 28,
        "height" : 0.4,
        "moves" : [
                "Ataque 1",
                "Ataque 2",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead743e"),
        "name" : "Pikachu",
        "description" : "Descrição editada, porém, continua sendo um pokémon de choque muito forte.",
        "attack" : 35,
        "defense" : 40,
        "height" : 0.5,
        "moves" : [
                "Ataque 1",
                "Ataque 2",
                "Desvio"
        ]
}
>
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```js
> var query = {moves: {$all: [/ataque 1/i, /ataque 2/i, /desvio/i]}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564291b535f1b5fe4ead743f"),
        "name" : "Charmander",
        "description" : "Um pokémon de fogo muito forte",
        "attack" : 40,
        "defense" : 35,
        "height" : 0.4,
        "moves" : [
                "Ataque 1",
                "Ataque 2",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7440"),
        "name" : "Squirtle",
        "description" : "Um pokémon de água muito forte",
        "attack" : 37,
        "defense" : 30,
        "height" : 0.3,
        "moves" : [
                "Ataque 1",
                "Ataque 2",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7441"),
        "name" : "Bulbasauro",
        "description" : "Um pokémon de planta muito forte",
        "attack" : 45,
        "defense" : 28,
        "height" : 0.4,
        "moves" : [
                "Ataque 1",
                "Ataque 2",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead743e"),
        "name" : "Pikachu",
        "description" : "Descrição editada, porém, continua sendo um pokémon de choque muito forte.",
        "attack" : 35,
        "defense" : 40,
        "height" : 0.5,
        "moves" : [
                "Ataque 1",
                "Ataque 2",
                "Desvio"
        ]
}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```js
> var query = {type: {$ne: /eletrico/i}}
> db.pokemons.find(query).pretty()
Error: error: {
        "$err" : "Can't canonicalize query: BadValue Can't have regex as arg to $ne.",
        "code" : 17287
}
> var query = {type: {$ne: "eletrico"}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564291b535f1b5fe4ead743f"),
        "name" : "Charmander",
        "description" : "Um pokémon de fogo muito forte",
        "attack" : 40,
        "defense" : 35,
        "height" : 0.4,
        "moves" : [
                "Ataque 1",
                "Ataque 2",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7440"),
        "name" : "Squirtle",
        "description" : "Um pokémon de água muito forte",
        "attack" : 37,
        "defense" : 30,
        "height" : 0.3,
        "moves" : [
                "Ataque 1",
                "Ataque 2",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7441"),
        "name" : "Bulbasauro",
        "description" : "Um pokémon de planta muito forte",
        "attack" : 45,
        "defense" : 28,
        "height" : 0.4,
        "moves" : [
                "Ataque 1",
                "Ataque 2",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7442"),
        "name" : "Pidgey",
        "description" : "Um pokémon de vento muito forte",
        "attack" : 30,
        "defense" : 50,
        "height" : 0.5,
        "moves" : [
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564a4bf5db4bef5e9999a550"),
        "description" : "Pokemon de teste",
        "name" : "Testemon",
        "attack" : 8000,
        "defense" : 8000,
        "moves" : [
                "Desvio"
        ]
}
{
		// Campo type não foi adicionado... Por isso o Pikachu também foi retornado..
        "_id" : ObjectId("564291b535f1b5fe4ead743e"),
        "name" : "Pikachu",
        "description" : "Descrição editada, porém, continua sendo um pokémon de choque muito forte.",
        "attack" : 35,
        "defense" : 40,
        "height" : 0.5,
        "moves" : [
                "Ataque 1",
                "Ataque 2",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564c593abc3caee13b9622af"),
        "name" : "AindaNaoExisteMon",
        "description" : "Sem maiores informações",
        "type" : null,
        "attack" : null,
        "height" : null,
        "defense" : null,
        "moves" : [ ]
}
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```js
> var query = {$and: [{moves: {$in: [/investida/i]}}, {defense: {$not: {$lte: 49}}}]}
> db.pokemons.find(query).pretty()

// SUPONDO que fosse com o ataque Desvio...
> var query = {$and: [{moves: {$in: [/desvio/i]}}, {defense: {$not: {$lte: 49}}}]}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564291b535f1b5fe4ead7442"),
        "name" : "Pidgey",
        "description" : "Um pokémon de vento muito forte",
        "attack" : 30,
        "defense" : 50,
        "height" : 0.5,
        "moves" : [
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564a4bf5db4bef5e9999a550"),
        "description" : "Pokemon de teste",
        "name" : "Testemon",
        "attack" : 8000,
        "defense" : 8000,
        "moves" : [
                "Desvio"
        ]
}
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```js
// Campo type não foi adicionado... Por isso o não deletou o squirtle...
> var query = {$and: [{attack: {$lt: 50}}, {type: 'água'}]}
> db.pokemons.remove(query)
WriteResult({ "nRemoved" : 0 })
```

## Extra pra quem é malandrão
## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores `$ne` e `$not`.

O operador `$ne` se refere a uma condição que não é atendida. Por exemplo, eu poderia retornar da minha collection pokemons, todos os pokemons que não são do tipo elétrico... e por ai vai...

Já o operador `$not` tem a função de negar a condição, inclusive pode ser utilizada com o operador `$ne` pra fazer pegadinha do malandro. '-'
Se por acaso utilizarmos o operador `$not` no exemplo anterior, iriamos retornar todos os pokemons do tipo elétrico. :)