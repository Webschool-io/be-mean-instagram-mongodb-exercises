# MongoDB - Aula 04 / 05 - Exercício
autor: Sergio Kopplin

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Venusaur, Charizard, Nidoking e Nidoqueen.
```
var query = { name: { $in: [
	/venusaur/i,
	/charizard/i,
	/nidoking/i,
	/nidoqueen/i
] } } }
var mod = { $pushAll: { attacks: [ 'scrash', 'energy' ] } };
var options = { multi: true };

Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 1ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
var query = {}
var mod = { $pushAll: { moves: ['desvio'] } }
var options = { multi: true }
db.pokemons.update(query, mod, options)

Fetched 5 record(s) in 2ms
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = { name: /AindaNaoExisteMon/i }
var mod = {
	$set: { name: "AindaNaoExisteMon" },
	$setOnInsert: {
		type: null,
		attack: null,
		height: null,
		attacks: [],
		moves: [],
		description: "Sem maiores informações"
	}
}
var options = { upsert: true }
db.pokemons.update(query, mod, options)

Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("565b407177fb101da1e7282b")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
var query = { attacks: { $all: ['investida', 'energy'] } }
db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
var query = { attacks: { $all: ['scrash', 'energy'] }, name: /Venusaur/i }
db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que não são do tipo `Drill`.##
```
var query = { type: { $nin: ['Drill'] } }
db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
var query = {
	attacks: { $in: [/scrash/i] },
	attack: { $gte: 49 }
}
db.pokemons.find(query)
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var query = {
	type: /agua/i,
	attack: { $lt: 50 }
}
db.pokemons.remove(query)
```
