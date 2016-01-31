# MongoDb - Aula 02 - Exercício
autor Vinicius Mazzeo

## Importando os restaurantes

```
>use be-mean-pokemons
switched to db be-mean-pokemons
```
## Listagem das databases(passo 2)

```
> show dbs
be-mean            0.004GB
be-mean-instagram  0.000GB
be-mean-teste      0.000GB
local              0.000GB
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

## Cadastro dos pokemons(passo 4)

```

> var pokemon ={'name':'Charizar','description':'Charizard flies around the sky in search of powerful opponents.','type':'Fogo', attack:70, height:1.7}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

> var pokemon ={'name':'Blastoise','description':'Blastoise has water spouts that protrude from its shell. ','type':'Água', attack:68, defense:85, height:1.6}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

> var pokemon ={'name':'Pidgeot','description':'This Pokémon has a dazzling plumage of beautifully glossy feathers. ','type':'Normal', attack:67, defense:69, height:1.5}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

> var pokemon ={'name':'Golduck','description':'The webbed flippers on its forelegs and hind legs and the streamlined body','type':'Water', attack:76, defense:73, height:1.7}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

> var pokemon ={'name':'Arcanine','description':'Arcanine is known for its high speed. It is said to be capable of running','type':'Fogo', attack:71, defense:82, height:1.9}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

```

## Listagem dos pokemons(passo 5)

```

> var lista = db.pokemons.find()

> lista
{ 
	"_id" : ObjectId("56aacb0bafa8cba6ffd83971"), 
	"name" : "Charizar", 
	"description" : "Charizard flies around the sky in search of powerful opponents.", 
	"type" : "Fogo", 
	"attack" : 70, 
	"defense" : 79,
	"height" : 1.7 
}
{ 
	"_id" : ObjectId("56aacb88afa8cba6ffd83972"), 
	"name" : "Blastoise", 
	"description" : "Blastoise has water spouts that protrude from its shell. ", 
	"type" : "Água", 
	"attack" : 68, 
	"defense" : 85, 
	"height" : 1.6 
}
{ 
	"_id" : ObjectId("56aacd2dafa8cba6ffd83973"), 
	"name" : "Pidgeot", 
	"description" : "This Pokémon has a dazzling plumage of beautifully glossy feathers. ", 
	"type" : "Normal", 
	"attack" : 67, 
	"defense" : 69, 
	"height" : 1.5 
}
{ 
	"_id" : ObjectId("56aacdadafa8cba6ffd83974"), 
	"name" : "Golduck", 
	"description" : "The webbed flippers on its forelegs and hind legs and the streamlined body", 
	"type" : "Water", 
	"attack" : 76, 
	"defense" : 73, 
	"height" : 1.7 
}
{ 
	"_id" : ObjectId("56aace1fafa8cba6ffd83975"), 
	"name" : "Arcanine", 
	"description" : "Arcanine is known for its high speed. It is said to be capable of running", 
	"type" : "Fogo", 
	"attack" : 71, 
	"defense" : 82, 
	"height" : 1.9 
}

```

## pokemons(passo 6)

```

> var updatepoke = {name: 'Charizar'}
> var poke = db.pokemons.findOne(updatepoke)
> poke
{
	"_id" : ObjectId("56aacb0bafa8cba6ffd83971"),
	"name" : "Charizar",
	"description" : "Charizard flies around the sky in search of powerful opponents.",
	"type" : "Fogo",
	"attack" : 70,
	"height" : 1.7,
	"defense" : 79
}

```

## Atualização de Pokemon (passo 7)

```

> poke.description = 'Dragãozinho do capiroto'
Dragãozinho do capiroto
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })


> var lista = db.pokemons.find()
> lista

{ 
	"_id" : ObjectId("56aacb0bafa8cba6ffd83971"), 
	"name" : "Charizar", 
	"description" : "Dragãozinho do capiroto", 
	"type" : "Fogo", 
	"attack" : 70, 
	"defense" : 79,
	"height" : 1.7 
}
{ 
	"_id" : ObjectId("56aacb88afa8cba6ffd83972"), 
	"name" : "Blastoise", 
	"description" : "Blastoise has water spouts that protrude from its shell. ", 
	"type" : "Água", 
	"attack" : 68, 
	"defense" : 85, 
	"height" : 1.6 
}
{ 
	"_id" : ObjectId("56aacd2dafa8cba6ffd83973"), 
	"name" : "Pidgeot", 
	"description" : "This Pokémon has a dazzling plumage of beautifully glossy feathers. ", 
	"type" : "Normal", 
	"attack" : 67, 
	"defense" : 69, 
	"height" : 1.5 
}
{ 
	"_id" : ObjectId("56aacdadafa8cba6ffd83974"), 
	"name" : "Golduck", 
	"description" : "The webbed flippers on its forelegs and hind legs and the streamlined body", 
	"type" : "Water", 
	"attack" : 76, 
	"defense" : 73, 
	"height" : 1.7 
}
{ 
	"_id" : ObjectId("56aace1fafa8cba6ffd83975"), 
	"name" : "Arcanine", 
	"description" : "Arcanine is known for its high speed. It is said to be capable of running", 
	"type" : "Fogo", 
	"attack" : 71, 
	"defense" : 82, 
	"height" : 1.9 
}


```

