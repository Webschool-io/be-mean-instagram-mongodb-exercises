# MongoDB - Aula 04 - Exercício
autor: Davidson da Silva Nascimento
## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbasaur e Charmander.
```js
> var query = {name: /pikachu/i}
> var mod = {$pushAll: {moves: ["investida rapidamente rapida", "choque lerolero"]}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
>

> var query = {name: /bulbasaur/i}
> var mod = {$pushAll: {moves: ["cospe erva", "genki dama tipo goku"]}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 0, "nUpserted" : 0, "nModified" : 0 })
>

> var query = {name: /squirtle/i}
> var mod = {$pushAll: {moves: ["bolhas matadoras", "jato forte de água"]}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
>

> var query = {name: /charmander/i}
> var mod = {$pushAll: {moves: ["investida ardente", "cospe fogo quente pelano"]}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
>
```
## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```js
> var query = {}
> var mod = {$push: {moves: "desvio"}}
> var options = {multi: 1}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 11, "nUpserted" : 0, "nModified" : 11 })
>
```
## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```js
> var query = {name: /AindaNaoExisteMon/i}
> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", type: null, attack: null, defense: null, height: null, description: "Sem maiores informações"}}
> var options = {upsert: 1}
> db.pokemons.update(query, mod, options)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("5658575991a7a2e6968ab81b")
})
>
```
## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```js
> var query = {moves: {$in: [/investida/i, /genki dama/i]}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("5652f5aae73644cad08260c8"),
        "name" : "Pikachu",
        "attack" : 55,
        "defense" : 40,
        "height" : 0.4,
        "type" : "Elétrico",
        "moves" : [
                "investida rapidamente rapida",
                "choque lerolero",
                "desvio"
        ]
}
{
        "_id" : ObjectId("5658510e1c51afdabac469ff"),
        "name" : "Charmander",
        "attack" : 52,
        "defense" : 43,
        "height" : 0.6,
        "type" : "Fogo",
        "description" : "Obviamente prefere lugares quentes. Quando chove, a vapor é dito bico a partir da ponta da cauda.",
        "moves" : [
                "investida ardente",
                "cospe fogo quente pelano",
                "desvio"
        ]
}
{
        "_id" : ObjectId("565850d01c51afdabac469fd"),
        "name" : "Bulbasaur",
        "attack" : 49,
        "defense" : 49,
        "height" : 0.7,
        "type" : "Grama",
        "description" : "A semente em sua parte traseira está cheio de nutrientes.",
        "moves" : [
                "cospe erva",
                "genki dama tipo goku",
                "desvio"
        ]
}
>
```
## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```js
> var query = {moves: {$all: [/cospe erva/i, /genki dama tipo goku/i]}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("565850d01c51afdabac469fd"),
        "name" : "Bulbasaur",
        "attack" : 49,
        "defense" : 49,
        "height" : 0.7,
        "type" : "Grama",
        "description" : "A semente em sua parte traseira está cheio de nutrientes.",
        "moves" : [
                "cospe erva",
                "genki dama tipo goku",
                "desvio"
        ]
}
>
```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```js
> var query = {type: {$not: /elétrico/i}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("565222b99a8f50a878c10890"),
        "name" : "Mewtwo",
        "description" : "Pokemon sangue nu ZÓI",
        "attack" : 110,
        "defense" : 90,
        "height" : 2,
        "type" : "Psíquico",
        "moves" : [
                "desvio"
        ]
}
{
        "_id" : ObjectId("565222b99a8f50a878c10894"),
        "name" : "Zoroark",
        "description" : "Eles protegem seu covil com cenário ilusório.",
        "attack" : 105,
        "defense" : 60,
        "height" : 1.6,
        "type" : "Negro",
        "moves" : [
                "desvio"
        ]
}
{
        "_id" : ObjectId("565222b99a8f50a878c10895"),
        "name" : "Zubat",
        "description" : "Quando ela cresce, ela lança a pele, cobre-se com seda, e torna-se um casulo.",
        "attack" : 45,
        "defense" : 35,
        "height" : 0.8,
        "type" : "Voador",
        "moves" : [
                "desvio"
        ]
}
{
        "_id" : ObjectId("565222b99a8f50a878c10891"),
        "name" : "Charizard",
        "description" : "Cospe fogo que é quente o suficiente para derreter rochas. Conhecido por causar incêndios florestais sem querer.",
        "attack" : 84,
        "defense" : 78,
        "height" : 1.7,
        "type" : "Fogo",
        "moves" : [
                "desvio"
        ]
}
{
        "_id" : ObjectId("565222b99a8f50a878c10892"),
        "name" : "Yveltal",
        "description" : "Quando sua vida chega ao fim, ele absorve a energia da vida de todos os seres vivos e se transforma em um casulo mais uma vez.",
        "attack" : 131,
        "defense" : 95,
        "height" : 5.8,
        "type" : "Voador",
        "moves" : [
                "desvio"
        ]
}
{
        "_id" : ObjectId("56585aa21c51afdabac46a00"),
        "name" : "Bulbasaur",
        "attack" : 49,
        "defense" : 49,
        "height" : 0.7,
        "type" : "Grama",
        "description" : "A semente em sua parte traseira está cheio de nutrientes.",
        "moves" : [
                "cospe erva",
                "genki dama tipo goku",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56585aa41c51afdabac46a02"),
        "name" : "Charmander",
        "attack" : 52,
        "defense" : 43,
        "height" : 0.6,
        "type" : "Fogo",
        "description" : "Obviamente prefere lugares quentes. Quando chove, a vapor é dito bico a partir da ponta da cauda.",
        "moves" : [
                "investida ardente",
                "cospe fogo quente pelano",
                "desvio"
        ]
}
{
        "_id" : ObjectId("565222b99a8f50a878c10893"),
        "name" : "Alakazam",
        "description" : "Um aroma sedutor exala de sua flor. A fragrância deixa calmo seus oponentes em uma batalha.",
        "attack" : 50,
        "defense" : 45,
        "height" : 1.5,
        "type" : "Psíquico",
        "moves" : [
                "desvio"
        ]
}
{
        "_id" : ObjectId("565222b99a8f50a878c10896"),
        "name" : "Aggron",
        "description" : "Suas balas de água pode pregar precisamente latas de uma distância de mais de 160 pés.",
        "attack" : 110,
        "defense" : 180,
        "height" : 2.1,
        "type" : "Pedra",
        "moves" : [
                "desvio"
        ]
}
{
        "_id" : ObjectId("56585aa21c51afdabac46a01"),
        "name" : "Squirtle",
        "attack" : 48,
        "defense" : 65,
        "height" : 0.5,
        "type" : "Água",
        "description" : "Poderosamente sprays de espuma de sua boca.",
        "moves" : [
                "bolhas matadoras",
                "jato forte de água",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56585b4891a7a2e6968ab81c"),
        "name" : "AindaNaoExisteMon",
        "type" : null,
        "attack" : null,
        "defense" : null,
        "height" : null,
        "description" : "Sem maiores informações"
}
>
```
## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
#### Se você não tiver Pokemons com valores de defense então faça a query para o campo attack, como feito abaixo:
```js
> var query = {$and: [{moves: {$in: [/investida/i]}}, {attack: {$not: {$lte: 49}
}}]}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("5652f5aae73644cad08260c8"),
        "name" : "Pikachu",
        "attack" : 55,
        "defense" : 40,
        "height" : 0.4,
        "type" : "Elétrico",
        "moves" : [
                "investida rapidamente rapida",
                "choque lerolero",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56585aa41c51afdabac46a02"),
        "name" : "Charmander",
        "attack" : 52,
        "defense" : 43,
        "height" : 0.6,
        "type" : "Fogo",
        "description" : "Obviamente prefere lugares quentes. Quando chove, a vapor é dito bico a partir da ponta da cauda.",
        "moves" : [
                "investida ardente",
                "cospe fogo quente pelano",
                "desvio"
        ]
}
>
```
## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```js
> var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}
> db.pokemons.remove(query)
WriteResult({ "nRemoved" : 1 })
>
```
## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores `$ne` e `$not`.
### $ne
Seleciona os documentos onde o valor do campo `não` é igual ao valor especificado ou que `não` possuem o campo informado, ou seja, testa diretamente o conteúdo dos campos. Não suporta operações utilizando **REGEX**, para isto recomenda-se utilizar o `$not`.

**Sintaxe:**  
`{ campo: { $ne: valor } }`

**Exemplo:**

`db.pokemons.find({type: {$ne: "Grama"}})`
* irá selecionar todos os documentos da coleção `pokemons` cujo valor do campo `type` seja igual a **Grama** ou
* o campo não existe

### $not
Seleciona os documentos que `não` correspondem a expressão informada ou que `não` possuem o campo informado.

**Só afeta outros operadores e não pode verificar campos e documentos de forma independente.**

**Sintaxe:**  
`{ campo: { $not: {expressão} } }`

**Exemplo:**

`db.pokemons.find({attack: {$not: {$lt: 50}}})`
* o valor do campo `type` é maior ou igual a **50** ou
* o campo não existe

`db.pokemons.find({moves: {$not: /desvio/i}})`
* o valor de nenhuma posição do campo `moves` **(que é do tipo array)** deverá possuir a descrição **"desvio"** ou
* o campo não existe