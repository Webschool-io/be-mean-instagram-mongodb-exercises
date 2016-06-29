# MongoDB - Aula 04 - Exercício
autor: Lucas Duarte Anício

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
> var query = 
{
  "name": {
    "$in": [
      "Pikachu",
      "Squirtle",
      "Bulbasauro",
      "Charmander"
    ]
  }
}

> var mod = 
{
  "$pushAll": {
    "moves": [
      "Cortar",
      "Picar"
    ]
  }
}

> var options = 
{
  "multi": true
}


> db.pokemons.update(query, mod, options)
Updated 3 existing record(s) in 1ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
> var mod = 
{
  "$push": {
    "moves": "Desvio"
  }
}

> var options = 
{
  "multi": true
}

> db.pokemons.update({},mod,options)
Updated 5 existing record(s) in 1ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
> var pokemon =
{
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}

> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
> var query = 
{
  "moves": {
    "$in": [
      /investida/i,
      /desvio/i
    ]
  }
}

> db.pokemons.find(query)
Fetched 5 record(s) in 1ms

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
> var query = {moves: {$in: [/desvio/i, /esquivar/i, /cortar/i]}}
> db.pokemons.find(query)

Fetched 3 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
> var query = 
{
  "type": "electric"
}

> db.pokemons.find(query)
{
  "_id": ObjectId("56ac9a4353d26711909f147b"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "Cortar",
    "Picar",
  ]
}

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
> var query = {
  $and: [
    {
      moves: {$in: ['investida']}
    },
    {
      defense: {$not: {$lte: 49}}
    }
  ]
}

> db.pokemons.find(query)
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
> var query = {
  $and: [
    {types: {$in:['water']}},
    {attack: {$lt: 50}}
  ]
}

> db.pokemons.remove(query)
```

