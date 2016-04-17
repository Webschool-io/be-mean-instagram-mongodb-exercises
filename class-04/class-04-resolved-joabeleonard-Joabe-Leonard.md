# MongoDB - Aula 04 - Exercício
autor: Joabe Leonard Feitosa

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
> var query = {name: {$in:['Pikachu', 'Squirtle','Bulbassauro','Charmander']}}
> var mod = {$set : {moves:['Investida','Agilidade extrema']}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
  WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
> var query = {}
> var mod = {$set: {moves:['desvio']}}
> var options = {multi :true}
> db.pokemons.update(query, mod, options)
  WriteResult({ "nMatched" : 7, "nUpserted" : 0, "nModified" : 7 })

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```> var query = {name: /AindaNaoExisteMon/i}
> var mod = {$setOnInsert:{nome : 'AindaNaoExisteMon', type:null, attack: null, defense:null, height:null, description:'Sem maiores informações'}}
> var options = {upsert:true}
> db.pokemons.update(query, mod, options)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("57139e9b2dfe6393eb3b04a6")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
	> var query = {moves:{$in:[/investida/i, /desvio/i]}}
	> db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```js
var query = {moves: {

    $all: [/Pancada de Raio/i, /Descarga/i]

    }
}
db.pokemons.find(query)

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
	> var query = {type: {$not: /electric/i}}
	> db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
	> var query = {$and: [ {moves: {$in: ['investida']}}, {attack: {$gt: 49}} ]}
	> db.pokemons.find(query)
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
	> var query = {$and: [ {type: /água/i}, {attack: {$lt: 50}} ]}
	> db.pokemons.remove(query)
WriteResult({ "nRemoved" : 0 })
```