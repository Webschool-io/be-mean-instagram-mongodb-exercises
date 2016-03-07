###MongoDB - Aula 04 - Exercício
Autor: Thiago de Carvalho

##1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = {
  "$or": [
    {
      "name": /pikachu/i
    },
    {
      "name": /squirtle/i
    },
    {
      "name": /bulbassauro/i
    },
    {
      "name": /charmander/i
    }
  ]
}

megazord(mongod-3.2.3) be-mean-pokemon> var mod = {
  "$pushAll": {
    "moves": [
      "Superman Punch",
      "Kimura"
    ]
  }
}

megazord(mongod-3.2.3) be-mean-pokemon> var options = {
  multi: true
}

megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.update(query, mod, options)

Updated 4 existing record(s) in 4ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```
##2. Adicionar 1 movimento em todos os pokemons: desvio.
```

megazord(mongod-3.2.3) be-mean-pokemon> var query = {}

megazord(mongod-3.2.3) be-mean-pokemon> var mod = {
  "$push": {
    "moves": "Desvio"
  }
}

megazord(mongod-3.2.3) be-mean-pokemon> var options = {
  multi: true
}

megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.update(query, mod, options)
Updated 12 existing record(s) in 6ms
WriteResult({
  "nMatched": 12,
  "nUpserted": 0,
  "nModified": 12
})


```
##3. Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = {name: /AindaNaoExisteMon/i}

megazord(mongod-3.2.3) be-mean-pokemon> var mod = {
  $setOnInsert: {
    "name": "AindaNaoExisteMon",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "height": null,
    "moves": null
  }
}

megazord(mongod-3.2.3) be-mean-pokemon> var options = {
  upsert: true
}

megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 4ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "id": ObjectId("56d9ff0852163b03af90eba6")
})

```
##4. Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = {
  "moves": {
    "$all": [
      /investida/i,
      /desvio/i
    ]
  }
}

megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.find(query)

```
##5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = {
  "moves": {
    "$all": [
      /Superman Punch/i,
      /Kimura/i
    ]
  }
}

megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.find(query)

```
##6. Pesquisar todos os pokemons que não são do tipo elétrico.
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = {
  "type": {
    "$ne": "elétrico"
  }
}

megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.find(query)

```
##7. Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = {
  "$and": [
    {
      "moves": "investida"
    },
    {
      "defense": {
        "$gt": 49
      }
    }
  ]
}

megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.find(query);
```
##8. Remova todos os pokemons do tipo água e com attack menor que 50.
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = {
  "$and": [
    {
      "type": "água"
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}

megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.remove(query);

```
