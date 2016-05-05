# MongoDB - Aula 04 - Exercício

autor: William Bewzenko de Jesus

1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
2. Adicionar 1 movimento em todos os pokemons: 'desvio'
3. Adicionar o pokemons 'AindaNãoExisteMon' caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"
4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.
5. Pesquisar todos os pokemons que possuam ataques que você adicionou, escolha seu pokemon favorito.
6. Pesquisar todos que não são do tipo 'elétrico'
7. Pesquisar todos pokemons que tenham ataque 'investida' e tenham a defesa não menor ou igual a 49
8. Remova todos os pokemons do tipo água e com attack menor que 50.


1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander

```
> query
{
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
> mod
{
  "$pushAll": {
    "moves": [
      "cabeçada",
      "fugir"
    ]
  }
}
> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
> db.pokemons.find(query)
{
  "_id": ObjectId("568af9afe5c2ef5322619bac"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovao",
    "cabeçada",
    "fugir"
  ],
  "active": false
}
{
  "_id": ObjectId("568afb7de5c2ef5322619bad"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha"
  ]
}
{
  "_id": ObjectId("568afb7de5c2ef5322619bae"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas"
  ]
}
{
  "_id": ObjectId("568afb7de5c2ef5322619baf"),
  "name": "Squirtle",
  "description": "Ejeta àgua que passarinho não bebe",
  "type": "àgua",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba"
  ]
}
Fetched 4 record(s) in 3ms

```

2. Adicionar 1 movimento em todos os pokemons: 'desvio'

```
	> query
	{
	  
	}
	> mod
	{
	  "$push": {
	    "moves": "desvio"
	  }
	}
	> options
	{
	  "multi": true
	}
	> db.pokemons.update(query, mod, options)
	Updated 6 existing record(s) in 5ms
	WriteResult({
	  "nMatched": 6,
	  "nUpserted": 0,
	  "nModified": 6
	})
	> db.pokemons.find(query)
	{
	  "_id": ObjectId("568af9afe5c2ef5322619bac"),
	  "name": "Pikachu",
	  "description": "Rato elétrico bem fofinho",
	  "type": "electric",
	  "attack": 55,
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "choque do trovao",
	    "cabeçada",
	    "fugir",
	    "desvio"
	  ],
	  "active": false
	}
	{
	  "_id": ObjectId("568afb7de5c2ef5322619bad"),
	  "name": "Bulbassauro",
	  "description": "Chicote de trepadeira",
	  "type": "grama",
	  "attack": 49,
	  "height": 0.4,
	  "active": false,
	  "moves": [
	    "investida",
	    "folha navalha",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("568afb7de5c2ef5322619bae"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga de fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "lança-chamas",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("568afb7de5c2ef5322619baf"),
	  "name": "Squirtle",
	  "description": "Ejeta àgua que passarinho não bebe",
	  "type": "àgua",
	  "attack": 48,
	  "height": 0.5,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("568afc51e5c2ef5322619bb0"),
	  "name": "Caterpie",
	  "description": "Larva lutadora",
	  "type": "inseto",
	  "attack": 30,
	  "height": 0.3,
	  "defense": 35,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5692d63a612241b9f91d6736"),
	  "name": "Elizanamon",
	  "attack": 8000,
	  "defense": 9000,
	  "description": "Pokemon Brabo...",
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	Fetched 6 record(s) in 4ms

```

3. Adicionar o pokemons 'AindaNãoExisteMon' caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"

```
	
	> query
	{
	  "name": /AindaNãoExisteMon/i
	}
	> mod
	{
	  "$setOnInsert": {
	    "name": "AindaNãoExisteMon",
	    "attack": null,
	    "defense": null,
	    "height": null,
	    "description": "Sem maiores informações"
	  }
	}
	> options
	{
	  "upsert": true
	}
	> db.pokemons.update(query, mod, options)
	Updated 1 new record(s) in 39ms
	WriteResult({
	  "nMatched": 0,
	  "nUpserted": 1,
	  "nModified": 0,
	  "_id": ObjectId("5693828e2301b3a3b496d3ca")
	})
	> db.pokemons.find(query)
	{
	  "_id": ObjectId("5693828e2301b3a3b496d3ca"),
	  "name": "AindaNãoExisteMon",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem maiores informações"
	}
	Fetched 1 record(s) in 3ms

```

4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.

```
> query
{
  "moves": {
    "$in": [
      "investida",
      "desvio"
    ]
  }
}
> db.pokemons.find(query)
{
  "_id": ObjectId("568af9afe5c2ef5322619bac"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovao",
    "cabeçada",
    "fugir",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("568afb7de5c2ef5322619bad"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
{
  "_id": ObjectId("568afb7de5c2ef5322619bae"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("568afb7de5c2ef5322619baf"),
  "name": "Squirtle",
  "description": "Ejeta àgua que passarinho não bebe",
  "type": "àgua",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ]
}
{
  "_id": ObjectId("568afc51e5c2ef5322619bb0"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5692d63a612241b9f91d6736"),
  "name": "Elizanamon",
  "attack": 8000,
  "defense": 9000,
  "description": "Pokemon Brabo...",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 6 record(s) in 5ms

```

5. Pesquisar todos os pokemons que possuam ataques que você adicionou, escolha seu pokemon favorito.

```
> var query = {moves: {$in: ['cabeçada']}}
> db.pokemons.find(query)
{
  "_id": ObjectId("568af9afe5c2ef5322619bac"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovao",
    "cabeçada",
    "fugir",
    "desvio"
  ],
  "active": false
}
Fetched 1 record(s) in 2ms

```

6. Pesquisar todos que não são do tipo 'elétrico'

```
> var query = {$nor: [{type: 'electric'}]}
> db.pokemons.find(query)
{
  "_id": ObjectId("568afb7de5c2ef5322619bad"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
{
  "_id": ObjectId("568afb7de5c2ef5322619bae"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("568afb7de5c2ef5322619baf"),
  "name": "Squirtle",
  "description": "Ejeta àgua que passarinho não bebe",
  "type": "àgua",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ]
}
{
  "_id": ObjectId("568afc51e5c2ef5322619bb0"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5692d63a612241b9f91d6736"),
  "name": "Elizanamon",
  "attack": 8000,
  "defense": 9000,
  "description": "Pokemon Brabo...",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5693828e2301b3a3b496d3ca"),
  "name": "AindaNãoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 6 record(s) in 5ms
```

7. Pesquisar todos pokemons que tenham ataque 'investida' e tenham a defesa não menor ou igual a 49

```
> query
{
  "$and": [
    {
      "moves": {
        "$in": [
          "investida"
        ]
      }
    },
    {
      "defense": {
        "$lte": 49
      }
    }
  ]
}
> db.pokemons.find(query)
{
  "_id": ObjectId("568afc51e5c2ef5322619bb0"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms
	
```

8. Remova todos os pokemons do tipo água e com attack menor que 50.

```
> query
{
  "$and": [
    {
      "type": "grama"
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}
> db.pokemons.remove(query)
Removed 1 record(s) in 19ms
WriteResult({
  "nRemoved": 1
})

```
