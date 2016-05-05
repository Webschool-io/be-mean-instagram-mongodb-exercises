# MongoDB - Aula 04 - Exercício
autor: LUAN RAFAEL CASTOR PINHEIRO


## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> var names = [/pikachu/i, /squirtle/i, /bulbassauro/i,/charmander/i]
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {name: {$in: names}}
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
	{
	  "_id": ObjectId("56474c58295d0c12b162b7a7"),
	  "name": "Pikachu",
	  "description": "Rato elétrico bem fofinho",
	  "type": "eletric",
	  "attack": 55,
	  "height": 0.4,
	  "active": false,
	  "moves": [
	    "investida",
	    "choque do trovão"
	  ]
	}
	{
	  "_id": ObjectId("56474e88ee09ff771271032c"),
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
	  "_id": ObjectId("56474e9fee09ff771271032d"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga defofinho",
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
	  "_id": ObjectId("56474ee0ee09ff771271032e"),
	  "name": "Squirtle",
	  "description": "Ejeta água que passarinho não bebe",
	  "type": "água",
	  "attack": 48,
	  "height": 0.5,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba"
	  ]
	}
	Fetched 4 record(s) in 6ms

	ubuntu-luan(mongod-3.0.7) be-mean-instagram> var names = [/pikachu/i, /squirtle/i, /bulbassauro/i,/charmander/i]
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {name: {$in: names}}
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> var mod = {$pushAll: {moves: ['ataque be-mean','kame hame haaaa']}}
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> var options = {multi: true}
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod,options)
	Updated 4 existing record(s) in 1ms
	WriteResult({
	  "nMatched": 4,
	  "nUpserted": 0,
	  "nModified": 4
	})
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
	{
	  "_id": ObjectId("56474c58295d0c12b162b7a7"),
	  "name": "Pikachu",
	  "description": "Rato elétrico bem fofinho",
	  "type": "eletric",
	  "attack": 55,
	  "height": 0.4,
	  "active": false,
	  "moves": [
	    "ataque rapido",
	    "investida",
	    "ataque be-mean",
	    "kame hame haaaa"
	  ]
	}
	{
	  "_id": ObjectId("56474e88ee09ff771271032c"),
	  "name": "Bulbassauro",
	  "description": "Chicote de trepadeira",
	  "type": "grama",
	  "attack": 49,
	  "height": 0.4,
	  "active": false,
	  "moves": [
	    "ataque rapido",
	    "investida",
	    "ataque be-mean",
	    "kame hame haaaa"
	  ]
	}
	{
	  "_id": ObjectId("56474e9fee09ff771271032d"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga defofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "ataque rapido",
	    "investida",
	    "ataque be-mean",
	    "kame hame haaaa"
	  ]
	}
	{
	  "_id": ObjectId("56474ee0ee09ff771271032e"),
	  "name": "Squirtle",
	  "description": "Ejeta água que passarinho não bebe",
	  "type": "água",
	  "attack": 48,
	  "height": 0.5,
	  "active": false,
	  "moves": [
	    "ataque rapido",
	    "investida",
	    "ataque be-mean",
	    "kame hame haaaa"
	  ]
	}
	Fetched 4 record(s) in 2ms


```

## 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {}
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> var mod = {$push: {moves: 'desvio'}}
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> var options = {multi: true}
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod,options)
	Updated 6 existing record(s) in 1ms
	WriteResult({
	  "nMatched": 6,
	  "nUpserted": 0,
	  "nModified": 6
	})
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
	{
	  "_id": ObjectId("56474f8fee09ff771271032f"),
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
	  "_id": ObjectId("5651e885569bcc4e10ade88c"),
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("56474c58295d0c12b162b7a7"),
	  "name": "Pikachu",
	  "description": "Rato elétrico bem fofinho",
	  "type": "eletric",
	  "attack": 55,
	  "height": 0.4,
	  "active": false,
	  "moves": [
	    "ataque rapido",
	    "investida",
	    "ataque be-mean",
	    "kame hame haaaa",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("56474e88ee09ff771271032c"),
	  "name": "Bulbassauro",
	  "description": "Chicote de trepadeira",
	  "type": "grama",
	  "attack": 49,
	  "height": 0.4,
	  "active": false,
	  "moves": [
	    "ataque rapido",
	    "investida",
	    "ataque be-mean",
	    "kame hame haaaa",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("56474e9fee09ff771271032d"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga defofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "ataque rapido",
	    "investida",
	    "ataque be-mean",
	    "kame hame haaaa",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("56474ee0ee09ff771271032e"),
	  "name": "Squirtle",
	  "description": "Ejeta água que passarinho não bebe",
	  "type": "água",
	  "attack": 48,
	  "height": 0.5,
	  "active": false,
	  "moves": [
	    "ataque rapido",
	    "investida",
	    "ataque be-mean",
	    "kame hame haaaa",
	    "desvio"
	  ]
	}
	Fetched 6 record(s) in 2ms

```

## 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```
ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {name:/NaoExisteMon/i}
ubuntu-luan(mongod-3.0.7) be-mean-instagram> var mod = {$set: {description: "Sem maiores informações"}, $setOnInsert: {name: "NãoExisteMon", attack: null, defense: null, height: null}}
ubuntu-luan(mongod-3.0.7) be-mean-instagram> var options = {upsert: true}
ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query,mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5651fb8f569bcc4e10ade88e")
})


ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {"_id": ObjectId("5651fb8f569bcc4e10ade88e")}
ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5651fb8f569bcc4e10ade88e"),
  "description": "Sem maiores informações",
  "name": "NãoExisteMon",
  "attack": null,
  "defense": null,
  "height": null
}
Fetched 1 record(s) in 3ms


```

## 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```

ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {moves : {$all : ['investida','kame hame haaaa']}}
ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56474c58295d0c12b162b7a7"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "ataque rapido",
    "investida",
    "ataque be-mean",
    "kame hame haaaa",
    "desvio"
  ]
}
{
  "_id": ObjectId("56474e88ee09ff771271032c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "ataque rapido",
    "investida",
    "ataque be-mean",
    "kame hame haaaa",
    "desvio"
  ]
}
{
  "_id": ObjectId("56474e9fee09ff771271032d"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga defofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "ataque rapido",
    "investida",
    "ataque be-mean",
    "kame hame haaaa",
    "desvio"
  ]
}
{
  "_id": ObjectId("56474ee0ee09ff771271032e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "ataque rapido",
    "investida",
    "ataque be-mean",
    "kame hame haaaa",
    "desvio"
  ]
}
Fetched 4 record(s) in 5ms


```

## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {moves : {$all : ['ataque be-mean','kame hame haaaa']}}
ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56474c58295d0c12b162b7a7"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "ataque rapido",
    "investida",
    "ataque be-mean",
    "kame hame haaaa",
    "desvio"
  ]
}
{
  "_id": ObjectId("56474e88ee09ff771271032c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "ataque rapido",
    "investida",
    "ataque be-mean",
    "kame hame haaaa",
    "desvio"
  ]
}
{
  "_id": ObjectId("56474e9fee09ff771271032d"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga defofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "ataque rapido",
    "investida",
    "ataque be-mean",
    "kame hame haaaa",
    "desvio"
  ]
}
{
  "_id": ObjectId("56474ee0ee09ff771271032e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "ataque rapido",
    "investida",
    "ataque be-mean",
    "kame hame haaaa",
    "desvio"
  ]
}
Fetched 4 record(s) in 1ms

```

## 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```
ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {type: {$ne: 'eletric'}}
ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56474f8fee09ff771271032f"),
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
  "_id": ObjectId("5651e885569bcc4e10ade88c"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56474e88ee09ff771271032c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "ataque rapido",
    "investida",
    "ataque be-mean",
    "kame hame haaaa",
    "desvio"
  ]
}
{
  "_id": ObjectId("56474e9fee09ff771271032d"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga defofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "ataque rapido",
    "investida",
    "ataque be-mean",
    "kame hame haaaa",
    "desvio"
  ]
}
{
  "_id": ObjectId("56474ee0ee09ff771271032e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "ataque rapido",
    "investida",
    "ataque be-mean",
    "kame hame haaaa",
    "desvio"
  ]
}
{
  "_id": ObjectId("5651fb8f569bcc4e10ade88e"),
  "description": "Sem maiores informações",
  "name": "NãoExisteMon",
  "attack": null,
  "defense": null,
  "height": null
}
Fetched 6 record(s) in 2ms

```

## 7. Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```
ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {$and: [{moves: {$in: ['investida']}},{defense: {$lte: 48}}]}
ubuntu-luan(mongod-3.0.7) be-mean-instagram> query
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
        "$lte": 48
      }
    }
  ]
}
ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56474f8fee09ff771271032f"),
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
Fetched 1 record(s) in 1ms


```

## 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {$and: [{type: 'água'},{attack: {$lt: 50}}]}
ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56474ee0ee09ff771271032e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "ataque rapido",
    "investida",
    "ataque be-mean",
    "kame hame haaaa",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms
ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```