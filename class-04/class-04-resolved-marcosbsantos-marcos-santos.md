##MongoDB -Aula04- Exercícios
##autor: MARCOS SANTOS

##1 - Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander:

var query = {name:/pikachu/i}
var attacks = ['raio da morte','electro']
var mod = {$pushAll:{moves:attacks}}
db.pokemons.update(query,mod)

var query = {name:/squirtle/i}
var attacks = ['tromba dagua','onda maritima']
var mod = {$pushAll:{moves:attacks}}
db.pokemons.update(query,mod)

var query = {name:/bulbassauro/i}
var attacks = ['lapada de cipo','vagem cortante']
var mod = {$pushAll:{moves:attacks}}
db.pokemons.update(query,mod)

var query = {name:/charmander/i}
var attacks = ['fagulha comsumiveis','fogo nuclear']
var mod = {$pushAll:{moves:attacks}}
db.pokemons.update(query,mod)

##2 - Adicionar 1 movimento em todos os pokemons: desvio:

var query = {}
var mod = {$push:{moves:desvio}}
var option = {multi:true}
db.pokemons.update(query,mod,option)

##3 - Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações":

var query = {name: /AindaNaoExisteMon/i}
var mod = {$setOnInsert:
	{
	  "name": "AindaNaoExisteMon",
	  "description": "Sem maiores informações",
	  "type": null,
	  "attack": null,
	  "height": null,
	  "defense": null
	}
}
var options = {upsert: true}
db.pokemons.update(query,mod,options)

##4 - Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito:

var query = {moves:{$in:['investida','fogo nuclear']}}

db.pokemons.find(query)
{
  "_id": ObjectId("5643c54172550cdcbbddbaa7"),
  "name": "Chamander",
  "description": "Esse e o cao chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "fagulha comsumiveis",
    "fogo nuclear",
    "desvio",
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms


##5 - Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito:

var query = {moves:{$all: ['lapada de cipo','vagem cortante']}}type

db.pokemons.find(query)
{
  "_id": ObjectId("5643c4d272550cdcbbddbaa6"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "lapada de cipo",
    "vagem cortante",
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms

##6 - Pesquisar todos os pokemons que não são do tipo elétrico:

var query = {type:{$ne:'eletric'}}

db.pokemons.find(query)
{
  "_id": ObjectId("56490978055d13b8416e9c63"),
  "name": "Magcargo",
  "description": "Este Pokémon retorna ao seu tamanho original mergulhando-se no magma.",
  "attack": 30,
  "defense": 50,
  "height": 0.8,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56490a26055d13b8416e9c64"),
  "name": "Remoraid",
  "description": " Quando a evolução se aproxima, este Pokémon viaja a jusante dos rios.",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56490a30055d13b8416e9c65"),
  "name": "Corsola",
  "description": "Se qualquer ramo quebra, este Pokémon cresce de volta em apenas uma noite..",
  "attack": 30,
  "defense": 40,
  "height": 0.6,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56490a38055d13b8416e9c66"),
  "name": "Piloswine",
  "description": "Possui cabelo bem curto por conta do calor do NE do Brasil",
  "attack": 50,
  "defense": 40,
  "height": 1.1,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56490a49055d13b8416e9c67"),
  "name": "Swinub",
  "description": "Sua comida favorita é um cogumelo que cresce sob a cobertura de grama morta.",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643c4d272550cdcbbddbaa6"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "lapada de cipo",
    "vagem cortante",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643c54172550cdcbbddbaa7"),
  "name": "Chamander",
  "description": "Esse e o cao chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "fagulha comsumiveis",
    "fogo nuclear",
    "desvio",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643c5a672550cdcbbddbaa8"),
  "name": "Squirtle",
  "description": "Ejeta agua que passarinho nao bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "tromba dagua",
    "onda maritima",
    "desvio"
  ]
}
{
  "_id": ObjectId("565f7388e68620800d8fc340"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null
}
Fetched 9 record(s) in 36ms


##7 - Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49:

var query = {$and:[{moves: {$in: ['desvio']}}, {attack: {$not: {$lte: 49}}} ]}
db.pokemons.find(query)
{
  "_id": ObjectId("56490a38055d13b8416e9c66"),
  "name": "Piloswine",
  "description": "Possui cabelo bem curto por conta do calor do NE do Brasil",
  "attack": 50,
  "defense": 40,
  "height": 1.1,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643c45472550cdcbbddbaa5"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "raio da morte",
    "electro",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643c54172550cdcbbddbaa7"),
  "name": "Chamander",
  "description": "Esse e o cao chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "fagulha comsumiveis",
    "fogo nuclear",
    "desvio",
    "desvio"
  ]
}
Fetched 3 record(s) in 7ms

##8 - Remova todos os pokemons do tipo água E com attack menor que 50:

var query = {$and:[{type: /agua/i}, {attack: {$lt: 50}} ]}

db.pokemons.remove(query)
Removed 1 record(s) in 3ms
WriteResult({
  "nRemoved": 1
})


