# MongoDb - Aula 03 - Exercício
autor Vinicius Mazzeo

## Listagem menor que 0.5(passo 1)

```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)

{ 
	"_id" : ObjectId("56aab60325214ae4c33db931"), 
	"name" : "Pikachu", 
	"description" : "Rato elétrico bem fofinho", 
	"type" : "eletric", 
	"attack" : 55, 
	"height" : 0.4 
}
{ 
	"_id" : ObjectId("56aab61325214ae4c33db932"), 
	"name" : "Bulbassauro", 
	"description" : "Chicote de trepadeira", 
	"type" : "grama", 
	"attack" : 49, 
	"height" : 0.4 
}
{ 
	"_id" : ObjectId("56aab62725214ae4c33db934"), 
	"name" : "Squirtle", 
	"description" : "Ejeta água que passarinho não bebe", 
	"type" : "água", 
	"attack" : 48, 
	"height" : 0.4 
}
{ 
	"_id" : ObjectId("56aabd5125214ae4c33db935"), 
	"name" : "Caterpie", 
	"description" : "Larva lutadora", 
	"type" : "inseto", 
	"attack" : 30, 
	"height" : 0.3, 
	"defense" : 35 
}
 

```
## Listagem maior ou igual que 0.5(passo 2)

```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ 
	"_id" : ObjectId("56aab61d25214ae4c33db933"), 
	"name" : "Charmander", 
	"description" : "Esse é o cão chupando manga de foquinho", 
	"type" : "fogo", 
	"attack" : 52, 
	"height" : 0.5 
}
{ 
	"_id" : ObjectId("56ae8248f04a3367ea761484"), 
	"name" : "Charizar", 
	"description" : "Charizard flies around the sky in search of powerful opponents.", 
	"type" : "Fogo", 
	"attack" : 70, 
	"height" : 1.7 
}
{
	"_id" : ObjectId("56ae8284f04a3367ea761485"), 
	"name" : "Blastoise", 
	"description" : "Blastoise has water spouts that protrude from its shell. ", 
	"type" : "Água", 
	"attack" : 68, 
	"defense" : 85, 
	"height" : 1.6 
}
{ 
	"_id" : ObjectId("56ae8290f04a3367ea761486"), 
	"name" : "Pidgeot", 
	"description" : "This Pokémon has a dazzling plumage of beautifully glossy feathers. ", 
	"type" : "Normal", 
	"attack" : 67, 
	"defense" : 69, 
	"height" : 1.5
}
{
	"_id" : ObjectId("56ae82a0f04a3367ea761487"), 
	"name" : "Golduck", 
	"description" : "The webbed flippers on its forelegs and hind legs and the streamlined body", 
	"type" : "Water", 
	"attack" : 76, 
	"defense" : 73, 
	"height" : 1.7 
}
{ 
	"_id" : ObjectId("56ae82acf04a3367ea761488"), 
	"name" : "Arcanine", 
	"description" : "Arcanine is known for its high speed. It is said to be capable of running", 
	"type" : "Fogo", 
	"attack" : 71, 
	"defense" : 82, 
	"height" : 1.9 
}

```
## Listagem menor ou igual que 0.5 E do type grama(passo 3)
```
> var query = {$and: [{height: {$lte: 0.5}}, {type: 'grama'}]}
> db.pokemons.find(query)
{ 
	"_id" : ObjectId("56aab61325214ae4c33db932"), 
	"name" : "Bulbassauro", 
	"description" : "Chicote de trepadeira", 
	"type" : "grama", 
	"attack" : 49, 
	"height" : 0.4 
}

```

## Listagem Pokemons name: Pikachu Ou Attack menor ou igual que 0.5(passo 4)

```

> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
> db.pokemons.find(query)
{ 
	"_id" : ObjectId("56aab60325214ae4c33db931"), 
	"name" : "Pikachu", 
	"description" : "Rato elétrico bem fofinho", 
	"type" : "eletric", 
	"attack" : 55, 
	"height" : 0.4 
}

```

## Listagem dos pokemons(passo 5)

```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
{ 
	"_id" : ObjectId("56aab60325214ae4c33db931"), 
	"name" : "Pikachu", 
	"description" : "Rato elétrico bem fofinho", 
	"type" : "eletric", 
	"attack" : 55, 
	"height" : 0.4 
}
{ 
	"_id" : ObjectId("56aab61325214ae4c33db932"), 
	"name" : "Bulbassauro", 
	"description" : "Chicote de trepadeira", 
	"type" : "grama", 
	"attack" : 49, 
	"height" : 0.4 
}
{ 
	"_id" : ObjectId("56aab61d25214ae4c33db933"), 
	"name" : "Charmander", 
	"description" : "Esse é o cão chupando manga de foquinho", 
	"type" : "fogo", 
	"attack" : 52, 
	"height" : 0.5 
}
{ 
	"_id" : ObjectId("56aab62725214ae4c33db934"), 
	"name" : "Squirtle", 
	"description" : "Ejeta água que passarinho não bebe", 
	"type" : "água", 
	"attack" : 48, 
	"height" : 0.4 
}



```
