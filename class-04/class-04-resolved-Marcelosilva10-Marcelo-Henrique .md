#MongoDB - Aula 04 - Exercício

autor: Marcelo Henrique

##Adcionar 2 ataques para o seguintes pokemóns ao mesmo tempo: Pikachu, Squirtle, Bulbasauro e Charmander

MarceloLocal(mongod-2.4.9) be-mean-instagram> var query = {
... $or: [
	 {name: 'Pikachu'},
...	 {name: 'Squirtle'},
...  {name: 'Bulbassauro'},
...  {name: 'Charmander'}
... ]
}
MarceloLocal(mongod-2.4.9) be-mean-instagram> var mod = {$set: {
... moves: ['Recuar', 'Pular']
... }}
MarceloLocal(mongod-2.4.9) be-mean-instagram> var options = {
... multi: true
... }
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 7 existing record(s) in 247ms

##Adcionar 1 movimentos em todos os pokemóns

MarceloLocal(mongod-2.4.9) be-mean-instagram> var mod = {$push: {
... moves: 'desvio'
... }}
MarceloLocal(mongod-2.4.9) be-mean-instagram> var options = { upsert: true, multi: true }
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.update({}, mod, options)
Updated 12 existing record(s) in 42ms

##Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"

MarceloLocal(mongod-2.4.9) be-mean-instagram> var query = {name: 'AindaNaoExisteMon'}
MarceloLocal(mongod-2.4.9) be-mean-instagram> var mod = {$setOnInsert: {
... name: 'AindaNaoExisteMon',
... attack: null,
... defense: null,
... heigth: null,
... hp: null,
... speed: null,
... types: null,
... description: 'Sem maiores informações'
... }}
MarceloLocal(mongod-2.4.9) be-mean-instagram> var opt = {
... upsert: true}
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 83ms
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56645e738b78884c47f18f70"),
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "heigth": null,
  "hp": null,
  "name": "AindaNaoExisteMon",
  "speed": null,
  "types": null
}
Fetched 1 record(s) in 1ms

##Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
Charmander
MarceloLocal(mongod-2.4.9) be-mean-instagram> var query = { moves: {$in: ['investida']} }
MarceloLocal(mongod-2.4.9) be-mean-instagram> var poke = {
... name: 'Charmander',
... moves: ['investida']
... }
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.insert(poke)
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564e121cf80adb57fcfaffc5"),
  "active": false,
  "attack": 30,
  "defense": 35,
  "description": "Lavra lutadora",
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Caterpie",
  "type": "inseto"
}
{
  "_id": ObjectId("564e125ef80adb57fcfaffc8"),
  "active": false,
  "attack": 33,
  "description": "Parente proximo do hantaro",
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Rattata",
  "type": "normal"
}
{
  "_id": ObjectId("564e1334f80adb57fcfaffc9"),
  "active": false,
  "attack": 30,
  "description": "Lavra lutadora",
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Caterpie",
  "type": "inseto"
}
{
  "_id": ObjectId("565881d8e6b840c1819c8330"),
  "active": false,
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Testemon"
}
{
  "_id": ObjectId("565ddf8fa6b8f4f45b25074d"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": /PokemonInexistente/i
}
{
  "_id": ObjectId("56646181cf62d197d9fce763"),
  "name": "Charmander",
  "moves": [
    "investida"
  ]
}
Fetched 6 record(s) in 7ms

##Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

MarceloLocal(mongod-2.4.9) be-mean-instagram> var query = {moves: {$in: ['desvio', 'Recuar', 'Pular']}}
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564e1250f80adb57fcfaffc6"),
  "active": false,
  "attack": 52,
  "description": "Esse é o cão chupando manga de fofinho",
  "height": 0.6,
  "moves": [
    "Recuar",
    "Pular",
    "desvio"
  ],
  "name": "Charmander",
  "type": "fogo"
}
{
  "_id": ObjectId("564e125af80adb57fcfaffc7"),
  "active": false,
  "attack": 48,
  "description": "Ejeta água que passarinho não bebe",
  "height": 0.5,
  "moves": [
    "Recuar",
    "Pular",
    "desvio"
  ],
  "name": "Squirtle",
  "type": "água"
}
{
  "_id": ObjectId("564e1389f80adb57fcfaffca"),
  "active": false,
  "attack": 49,
  "description": "Chicote de trepadeira",
  "height": 0.4,
  "moves": [
    "Recuar",
    "Pular",
    "desvio"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("56577998e1bc5add00ad15eb"),
  "active": false,
  "attack": 55,
  "description": "Rato elétrico bem fofinho",
  "height": 0.4,
  "moves": [
    "Recuar",
    "Pular",
    "desvio"
  ],
  "name": "Pikachu",
  "type": "electric"
}
{
  "_id": ObjectId("564e121cf80adb57fcfaffc5"),
  "active": false,
  "attack": 30,
  "defense": 35,
  "description": "Lavra lutadora",
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Caterpie",
  "type": "inseto"
}
{
  "_id": ObjectId("564e125ef80adb57fcfaffc8"),
  "active": false,
  "attack": 33,
  "description": "Parente proximo do hantaro",
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Rattata",
  "type": "normal"
}
{
  "_id": ObjectId("564e1334f80adb57fcfaffc9"),
  "active": false,
  "attack": 30,
  "description": "Lavra lutadora",
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Caterpie",
  "type": "inseto"
}
{
  "_id": ObjectId("564e1395f80adb57fcfaffcb"),
  "active": false,
  "attack": 52,
  "description": "Esse é o cão chupando manga de fofinho",
  "height": 0.6,
  "moves": [
    "Recuar",
    "Pular",
    "desvio"
  ],
  "name": "Charmander",
  "type": "fogo"
}
{
  "_id": ObjectId("564e139ff80adb57fcfaffcc"),
  "active": false,
  "attack": 48,
  "description": "Ejeta água que passarinho não bebe",
  "height": 0.5,
  "moves": [
    "Recuar",
    "Pular",
    "desvio"
  ],
  "name": "Squirtle",
  "type": "água"
}
{
  "_id": ObjectId("56577949e1bc5add00ad15ea"),
  "active": false,
  "attack": 49,
  "description": "Chicote de trepadeira",
  "height": 0.4,
  "moves": [
    "Recuar",
    "Pular",
    "desvio"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("565881d8e6b840c1819c8330"),
  "active": false,
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Testemon"
}
{
  "_id": ObjectId("565ddf8fa6b8f4f45b25074d"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": /PokemonInexistente/i
}
Fetched 12 record(s) in 9ms

##Pesquisar todos os pokemons que são do tipo elétrico.

MarceloLocal(mongod-2.4.9) be-mean-instagram> var query = {type: {$in: ['electric']}}
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56577998e1bc5add00ad15eb"),
  "active": false,
  "attack": 55,
  "description": "Rato elétrico bem fofinho",
  "height": 0.4,
  "moves": [
    "Recuar",
    "Pular",
    "desvio"
  ],
  "name": "Pikachu",
  "type": "electric"
}
Fetched 1 record(s) in 3ms

##Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

MarceloLocal(mongod-2.4.9) be-mean-instagram> var query = {
	$and: [
		{
		moves: {$in: ['investida']}
		},
		{
			defense: {$not: {$lte: 49}}
		}
	]
}
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564e125ef80adb57fcfaffc8"),
  "active": false,
  "attack": 33,
  "description": "Parente proximo do hantaro",
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Rattata",
  "type": "normal"
}
{
  "_id": ObjectId("564e1334f80adb57fcfaffc9"),
  "active": false,
  "attack": 30,
  "description": "Lavra lutadora",
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Caterpie",
  "type": "inseto"
}
{
  "_id": ObjectId("565881d8e6b840c1819c8330"),
  "active": false,
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Testemon"
}
{
  "_id": ObjectId("565ddf8fa6b8f4f45b25074d"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": /PokemonInexistente/i
}
{
  "_id": ObjectId("56646181cf62d197d9fce763"),
  "name": "Charmander",
  "moves": [
    "investida"
  ]
}
Fetched 5 record(s) in 3ms

##Remova todos os pokemons do tipo água e com attack menor que 50.

MarceloLocal(mongod-2.4.9) be-mean-instagram> var query = { $and: [ {type: {$in:['água']}}, {attack: {$lt: 50}} ] }
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.remove(query)
Removed 2 record(s) in 1ms