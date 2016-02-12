# MongoDB - Aula 04 - Exercício

autor: João Antonio Gardin Vieira

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = {name: /pikachu/i}
Tto(mongod-3.2.1) be-mean-pokemons> var attacks = ['thil whip', 'thunder shock']
Tto(mongod-3.2.1) be-mean-pokemons> var mod = {$set: {moves: attacks}}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Tto(mongod-3.2.1) be-mean-pokemons> var query = {name: /squirtle/i}
Tto(mongod-3.2.1) be-mean-pokemons> var attacks = ['water gun', 'withdraw']
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
Tto(mongod-3.2.1) be-mean-pokemons> var query = {name: /bulbassauro/i}
Tto(mongod-3.2.1) be-mean-pokemons> var attacks = ['leech seed', 'vine whip']
Tto(mongod-3.2.1) be-mean-pokemons> var mod = {$set: {moves: attacks, name: 'bulbasaur'}}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Tto(mongod-3.2.1) be-mean-pokemons> var query = {name: /charmander/i}
Tto(mongod-3.2.1) be-mean-pokemons> var attacks = ['ember', 'smokescreen']
Tto(mongod-3.2.1) be-mean-pokemons> var mod = {$set: {moves: attacks}}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
Tto(mongod-3.2.1) be-mean-pokemons> var query = {}
Tto(mongod-3.2.1) be-mean-pokemons> var mod = {$set: {moves: ['desvio']}}
Tto(mongod-3.2.1) be-mean-pokemons> var options = {multi: true}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 15 existing record(s) in 2ms
WriteResult({
  "nMatched": 15,
  "nUpserted": 0,
  "nModified": 14
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
Tto(mongod-3.2.1) be-mean-pokemons> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"}}
Tto(mongod-3.2.1) be-mean-pokemons> var options = {upsert: true}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 153ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56bae50cb45aafdd957c6476")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = {moves: { $in: [/investida/i, /roar/i]}}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56bae656b45aafdd957c648f"),
  "name": "vulpix",
  "description": "Na época de seu nascimento, Vulpix tem uma cauda branca.",
  "type": "fire",
  "attack": 40,
  "height": 0.6,
  "defese": 41,
  "moves": [
    "ember",
    "roar"
  ]
}
Fetched 1 record(s) in 3ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = {moves: { $in: [/desvio/i]}}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56bae656b45aafdd957c6487"),
  "name": "bulbasaur",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defese": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c6489"),
  "name": "pidgey",
  "description": "Pokemon voador com geolocalizador",
  "type": "flying",
  "attack": 45,
  "height": 0.3,
  "defese": 40,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c648a"),
  "name": "weedle",
  "description": "Este pokemon possui o poder de sexto sentido",
  "type": "bug",
  "attack": 35,
  "height": 0.3,
  "defese": 30,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c648b"),
  "name": "spearow",
  "description": "Spearow tem um grito muito alto que pode ser ouvido mais de meia milha de distância",
  "type": "flying",
  "attack": 60,
  "height": 0.3,
  "defese": 30,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c648c"),
  "name": "rattata",
  "description": "Pokemon comedor de queijo",
  "type": "normal",
  "attack": 56,
  "height": 0.3,
  "defese": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c648d"),
  "name": "caterpie",
  "description": "Larva lutadore",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defese": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c648e"),
  "name": "ekans",
  "description": "Ekans enrola-se em uma espiral enquanto descansa",
  "type": "snake",
  "attack": 60,
  "height": 2,
  "defese": 44,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c6490"),
  "name": "venonat",
  "description": "Venonat é dito ter evoluído com um casaco de cabelo fino",
  "type": "poison",
  "attack": 55,
  "height": 1,
  "defese": 50,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c6491"),
  "name": "meowth",
  "description": "este Pokémon ama moedas brilhantes que brilham com a luz.",
  "type": "normal",
  "attack": 45,
  "height": 0.4,
  "defese": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c6492"),
  "name": "mankey",
  "description": "Esse pokemon foi editado para sevir o exercicio",
  "type": "figthing",
  "attack": 80,
  "height": 0.5,
  "defese": 40,
  "moves": [
    "desvio"
  ]
}
Fetched 10 record(s) in 7ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = {$nor: [{type: /eletric/i}]}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56bae656b45aafdd957c6485"),
  "name": "squirtle",
  "description": "Ejeta água que passarinhoo não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "thil whip",
    "thunder shock"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c6487"),
  "name": "bulbasaur",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defese": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c6488"),
  "name": "charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defese": 40,
  "moves": [
    "ember",
    "smokescreen"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c6489"),
  "name": "pidgey",
  "description": "Pokemon voador com geolocalizador",
  "type": "flying",
  "attack": 45,
  "height": 0.3,
  "defese": 40,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c648a"),
  "name": "weedle",
  "description": "Este pokemon possui o poder de sexto sentido",
  "type": "bug",
  "attack": 35,
  "height": 0.3,
  "defese": 30,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c648b"),
  "name": "spearow",
  "description": "Spearow tem um grito muito alto que pode ser ouvido mais de meia milha de distância",
  "type": "flying",
  "attack": 60,
  "height": 0.3,
  "defese": 30,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c648c"),
  "name": "rattata",
  "description": "Pokemon comedor de queijo",
  "type": "normal",
  "attack": 56,
  "height": 0.3,
  "defese": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c648d"),
  "name": "caterpie",
  "description": "Larva lutadore",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defese": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c648e"),
  "name": "ekans",
  "description": "Ekans enrola-se em uma espiral enquanto descansa",
  "type": "snake",
  "attack": 60,
  "height": 2,
  "defese": 44,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c648f"),
  "name": "vulpix",
  "description": "Na época de seu nascimento, Vulpix tem uma cauda branca.",
  "type": "fire",
  "attack": 40,
  "height": 0.6,
  "defese": 41,
  "moves": [
    "ember",
    "roar"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c6490"),
  "name": "venonat",
  "description": "Venonat é dito ter evoluído com um casaco de cabelo fino",
  "type": "poison",
  "attack": 55,
  "height": 1,
  "defese": 50,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c6491"),
  "name": "meowth",
  "description": "este Pokémon ama moedas brilhantes que brilham com a luz.",
  "type": "normal",
  "attack": 45,
  "height": 0.4,
  "defese": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae656b45aafdd957c6492"),
  "name": "mankey",
  "description": "Esse pokemon foi editado para sevir o exercicio",
  "type": "figthing",
  "attack": 80,
  "height": 0.5,
  "defese": 40,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bae69ab45aafdd957c6493"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 14 record(s) in 10ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = { $and: [ {defese: { $gte: 49 } }, { moves: { $in: [/investida/i] } } ] }
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = { $and: [ {attack: { $lt: 50 } }, { type: /watter/i } ] }
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.remove( query )
Removed 0 record(s) in 2ms
WriteResult({
  "nRemoved": 0
})
```
