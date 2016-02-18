# MongoDB - Aula 04 - Exercício
autor: Felipe José Lopes Rita

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro, Charmander
StarKiller(mongod-3.2.0) be-mean-instagram> query = { $or:[ {name: /pikachu/i}, {name:/squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ] }
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
StarKiller(mongod-3.2.0) be-mean-instagram> mod = { $pushAll: { moves:[ 'Investida', 'Multiplicar' ] } }
{
  "$pushAll": {
    "moves": [
      "Investida",
      "Multiplicar"
    ]
  }
}

StarKiller(mongod-3.2.0) be-mean-instagram> options = {multi: true}
{
  "multi": true
}
StarKiller(mongod-3.2.0) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
StarKiller(mongod-3.2.0) be-mean-instagram> var mod = { $push:{ moves:'desvio' } }
StarKiller(mongod-3.2.0) be-mean-instagram> var options = {multi: true}
StarKiller(mongod-3.2.0) be-mean-instagram> db.pokemons.update({}, mod, options)
Updated 9 existing record(s) in 4ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})



## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
StarKiller(mongod-3.2.0) be-mean-instagram> mod = { $setOnInsert: { name: 'AindaNaoExisteMon', description: 'Sem maiores informações', type: null, attack: null, height:null, moves: null } }
{
  "$setOnInsert": {
    "name": "AindaNaoExisteMon",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "height": null,
    "moves": null
  }
}
StarKiller(mongod-3.2.0) be-mean-instagram> var options = {upsert: true}
StarKiller(mongod-3.2.0) be-mean-instagram> var query = {name: 'AindaNaoExisteMon'}
StarKiller(mongod-3.2.0) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56bb5169a654f3d15d16ef85")
})

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
StarKiller(mongod-3.2.0) be-mean-instagram> var query = { moves: { $all:['Investida', 'Choque do Trovão'] } }
StarKiller(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56bb4baa43e8eae26e3d71ca"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "Multiplicar",
    "desvio",
    "Choque do Trovão"
  ]
}
Fetched 1 record(s) in 3ms

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
StarKiller(mongod-3.2.0) be-mean-instagram> var query = { moves: { $in: ['Choque do Trovão'] } }
StarKiller(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56bb4baa43e8eae26e3d71ca"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "Multiplicar",
    "desvio",
    "Choque do Trovão"
  ]
}
Fetched 1 record(s) in 2ms

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
StarKiller(mongod-3.2.0) be-mean-instagram> var query = { type: { $not: /elétrico/i } }
StarKiller(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56b4237765cd05bf6bff3322"),
  "name": "Cyndaquil",
  "description": "Tem fogo nas costas e é fofo pra caralho",
  "attack": 52,
  "defense": 43,
  "height": 0.5,
  "descricao": "Sempre escolhia ele quando jogava pokemon Gold & Silver",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b4237765cd05bf6bff3324"),
  "name": "Charizard",
  "description": "Pokemon mais pica das galáxias",
  "attack": 84,
  "defense": 78,
  "height": 1.7,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b4237765cd05bf6bff3325"),
  "name": "Pidgey",
  "description": "Pomba comum de Sampa, só que não caga em você (acho)",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b4237765cd05bf6bff3326"),
  "name": "Zorua",
  "description": "Raposa preta (deve ser do capeta) foda e fofa",
  "attack": 65,
  "defense": 40,
  "height": 0.7,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56bb4baa43e8eae26e3d71cb"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "Investida",
    "Multiplicar",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bb4baa43e8eae26e3d71cc"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Investida",
    "Multiplicar",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bb4baa43e8eae26e3d71cd"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "Investida",
    "Multiplicar",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bb5169a654f3d15d16ef85"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "moves": null
}
Fetched 8 record(s) in 9ms

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
var query = {
	$and: [
		{ moves: { $in: ['Investida'] } },
		{ defense: { $not: { $lte: 49 } } }
	]
}
StarKiller(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56b4237765cd05bf6bff3323"),
  "name": "Minun",
  "description": "Coelho elétrico que parece mas não tem nada a ver com o pikachu",
  "attack": 40,
  "defense": 50,
  "height": 0.4,
  "moves": [
    "desvio",
    "Investida"
  ],
  "type": [
    "Elétrico"
  ]
}
{
  "_id": ObjectId("56b4237765cd05bf6bff3324"),
  "name": "Charizard",
  "description": "Pokemon mais pica das galáxias",
  "attack": 84,
  "defense": 78,
  "height": 1.7,
  "moves": [
    "desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("56bb4baa43e8eae26e3d71cd"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "Investida",
    "Multiplicar",
    "desvio"
  ],
  "defense": 65
}
Fetched 3 record(s) in 4ms

## Remova **todos** os pokemons do tipo água e com attack menor que 50
var query = {
	$and: [
		{ type: 'água' },
		{ attack: { $lt: 50 } }
	]
}
StarKiller(mongod-3.2.0) be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 4ms
WriteResult({
  "nRemoved": 1
})
