# MongoDB - Aula 04 - Exercício
autor: Vander Amorin

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
<pre><code>
var query = {
	
	$or: [

		{ name: /pikachu/i },
		{ name: /squirtle/i },
		{ name: /bulbassauro/i },
		{ name: /charmander/i }
	]

}


var mod = {
	
	$push: {

		moves: ['raio gurmetizador', 'raio dollinizador']
	}
}


var options = { multi: true }

be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
</code></pre>

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
<pre><code>
var query = {}

var mod = {
	
	$push: {

		moves: 'desvio'
	}
}

var options = { multi: true }

be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 13 existing record(s) in 2ms
WriteResult({
  "nMatched": 13,
  "nUpserted": 0,
  "nModified": 13
})
</code></pre>


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
<pre><code>
var query = {
	name: /AindaNaoExisteMon/i
}

var mod = {
	
	$setOnInsert: {

		name: "AindaNaoExisteMon",
		type: null,
		attack: null,
		height: null,
		active: null,
		moves: null,
		description: "Sem maiores informações"
	}
}

var options = { upsert: true }

be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564c91f7e7e93712b21f5a3e")
})
</code></pre>


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
<pre><code>
var query = {

	moves: {
		$all: ['investida', 'choque do trovão']
	}
}

be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564294113a1ae06e90375de3"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 0.8,
  "height": 0.4,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("564296b83a1ae06e90375de5"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 0,
  "height": 0.6,
  "active": false,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ]
}
{
  "_id": ObjectId("5642982e3a1ae06e90375de6"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 0.7,
  "height": 0.5,
  "active": false,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ]
}
{
  "_id": ObjectId("564294f43a1ae06e90375de4"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 0.8,
  "height": 0.4,
  "active": false,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ]
}
Fetched 4 record(s) in 5ms

</code></pre>


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
<pre><code>
var query = {

	moves: {

		$all: ['raio dollinizador', 'raio gurmetizador']
	}
}

be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564294113a1ae06e90375de3"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 0.8,
  "height": 0.4,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("564296b83a1ae06e90375de5"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 0,
  "height": 0.6,
  "active": false,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ]
}
{
  "_id": ObjectId("5642982e3a1ae06e90375de6"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 0.7,
  "height": 0.5,
  "active": false,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ]
}
{
  "_id": ObjectId("564294f43a1ae06e90375de4"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 0.8,
  "height": 0.4,
  "active": false,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ]
}
Fetched 4 record(s) in 1ms
</code></pre>


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
<pre><code>
var query = {
	type: {

		$ne: "electric"
	}
}
	
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5642993e3a1ae06e90375de7"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642a2a57a0d8f07689b8256"),
  "name": "Sandslash",
  "description": "Rato espinhoso",
  "type": "Rato",
  "attack": 50,
  "height": 1,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642a3218752932d9235dbe4"),
  "name": "Weedle",
  "description": "Minhoca de chifre",
  "type": "terra",
  "attack": 20,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642a3568752932d9235dbe5"),
  "name": "Spearow",
  "description": "Pássaro chorão",
  "type": "Aves",
  "attack": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642a37c8752932d9235dbe6"),
  "name": "Clefairy",
  "description": "Bicho Rosa inútil",
  "type": "fada",
  "attack": 0,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642a3968752932d9235dbe7"),
  "name": "Vulpix",
  "description": "Raposa fofinha",
  "type": "Raposa",
  "attack": 20,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564a78f3d504bf81bd7718c2"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564bde8f000b77b8851fdd01"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642982e3a1ae06e90375de6"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 0.7,
  "height": 0.5,
  "active": false,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ]
}
{
  "_id": ObjectId("564294f43a1ae06e90375de4"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 0.8,
  "height": 0.4,
  "active": false,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ]
}
{
  "_id": ObjectId("564c91f7e7e93712b21f5a3e"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "active": null,
  "moves": [ ],
  "description": "Sem maiores informações"
}
{
  "_id": ObjectId("5642a2e88752932d9235dbe3"),
  "name": "Blastoise",
  "description": "Pokemon tartaruga com canhões nas costas",
  "type": "Água",
  "attack": 40,
  "height": 1.6,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
Fetched 12 record(s) in 5ms
</code></pre>


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

<pre><code>
var query = {
	
	$and: [
		{ moves: { $in: ['investida'] } },

		{
			defense: {
				$ne: {$lte: 49}
			}
		}
	]
}

be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5642993e3a1ae06e90375de7"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642a2a57a0d8f07689b8256"),
  "name": "Sandslash",
  "description": "Rato espinhoso",
  "type": "Rato",
  "attack": 50,
  "height": 1,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642a3218752932d9235dbe4"),
  "name": "Weedle",
  "description": "Minhoca de chifre",
  "type": "terra",
  "attack": 20,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642a3568752932d9235dbe5"),
  "name": "Spearow",
  "description": "Pássaro chorão",
  "type": "Aves",
  "attack": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642a37c8752932d9235dbe6"),
  "name": "Clefairy",
  "description": "Bicho Rosa inútil",
  "type": "fada",
  "attack": 0,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5642a3968752932d9235dbe7"),
  "name": "Vulpix",
  "description": "Raposa fofinha",
  "type": "Raposa",
  "attack": 20,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564a78f3d504bf81bd7718c2"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564294113a1ae06e90375de3"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 0.8,
  "height": 0.4,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("564bde8f000b77b8851fdd01"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564296b83a1ae06e90375de5"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 0,
  "height": 0.6,
  "active": false,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ]
}
{
  "_id": ObjectId("5642982e3a1ae06e90375de6"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 0.7,
  "height": 0.5,
  "active": false,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ]
}
{
  "_id": ObjectId("564294f43a1ae06e90375de4"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 0.8,
  "height": 0.4,
  "active": false,
  "moves": [
    "raio gurmetizador",
    "raio dollinizador",
    "investida"
  ]
}
{
  "_id": ObjectId("5642a2e88752932d9235dbe3"),
  "name": "Blastoise",
  "description": "Pokemon tartaruga com canhões nas costas",
  "type": "Água",
  "attack": 40,
  "height": 1.6,
  "active": false,
  "moves": [
    "investida",
    "desvio",
    "investida"
  ]
}
Fetched 13 record(s) in 3ms
</code></pre>

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
<pre><code>
var query = {
	
	$and: [
		{ type: "água" },
		{ attack: { $lt: 50 } }
	]
}

be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
</code></pre>