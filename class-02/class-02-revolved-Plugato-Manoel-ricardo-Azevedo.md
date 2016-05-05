# MongoDb - Aula 02 - Exercício
autor Manoel Ricardo De Azevedo

## Crie uma database chamada be-mean-pokemons;

```
>use be-mean-pokemons
switched to db be-mean-pokemons
```
## Liste quais databases você possui nesse servidor;

```
> show dbs                
be-mean            0.004GB
be-mean-instagram  0.000GB
local              0.000GB
test               0.000GB
```
## Liste quais coleções você possui nessa database;
```
> show collections       

```

## Insira pelo menos 5 pokemons A SUA ESCOLHA;
```

> var pokemons = [
                   {'name':'Charizard','description':'Charizard flies around the sky in search of powerful opponents.','type':'Fogo', attack:70, height:1.7},
                   {'name':'Blastoise','description':'Blastoise has water spouts that protrude from its shell. ','type':'Água', attack:68, defense:85, height:1.6},
                   {'name':'Pidgeot','description':'This Pokémon has a dazzling plumage of beautifully glossy feathers. ','type':'Normal', attack:67, defense:69, height:1.5},
                   {'name':'Golduck','description':'The webbed flippers on its forelegs and hind legs and the streamlined body','type':'Water', attack:76, defense:73, height:1.7},
                   {'name':'Arcanine','description':'Arcanine is known for its high speed. It is said to be capable of running','type':'Fogo', attack:71, defense:82, height:1.9}
                 ]

> db.pokemons.insert(pokemons)
BulkWriteResult({ "writeErrors" : [ ],
                  "writeConcernErrors" : [ ],
                  "nInserted" : 5,
                  "nUpserted" : 0,
                  "nMatched" : 0,
                  "nModified" : 0,
                  "nRemoved" : 0,
                  "upserted" : [ ]      
})
```

## Liste os pokemons existentes na sua coleção;

```

> var list = db.pokemons.find()

> list
{
	"_id" : ObjectId("56bd201d831b7e2c1d226b6a"),
	"name" : "Charizard",
	"description" : "Charizard flies around the sky in search of powerful opponents.",
	"type" : "Fogo",
	"attack" : 70,
	"defense" : 79,
	"height" : 1.7
}
{
	"_id" : ObjectId("56bd201d831b7e2c1d226b6b"),
	"name" : "Blastoise",
	"description" : "Blastoise has water spouts that protrude from its shell. ",
	"type" : "Água",
	"attack" : 68,
	"defense" : 85,
	"height" : 1.6
}
{
	"_id" : ObjectId("56bd201d831b7e2c1d226b6c"),
	"name" : "Pidgeot",
	"description" : "This Pokémon has a dazzling plumage of beautifully glossy feathers. ",
	"type" : "Normal",
	"attack" : 67,
	"defense" : 69,
	"height" : 1.5
}
{
	"_id" : ObjectId("56bd201d831b7e2c1d226b6d"),
	"name" : "Golduck",
	"description" : "The webbed flippers on its forelegs and hind legs and the streamlined body",
	"type" : "Water",
	"attack" : 76,
	"defense" : 73,
	"height" : 1.7
}
{
	"_id" : ObjectId("56bd201d831b7e2c1d226b6e"),
	"name" : "Arcanine",
	"description" : "Arcanine is known for its high speed. It is said to be capable of running",
	"type" : "Fogo",
	"attack" : 71,
	"defense" : 82,
	"height" : 1.9
}

```

## Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;

```

> var poke = db.pokemons.findOne( {name: 'Blastoise'} )
> poke
{
        "_id" : ObjectId("56bd201d831b7e2c1d226b6b"),
        "name" : "Blastoise",
        "description" : "Blastoise has water spouts that protrude from its shell. ",
        "type" : "Água",
        "attack" : 68,
        "defense" : 85,
        "height" : 1.6
}

```

## Modifique sua `description` e salvê-o;

```
> poke.description = 'BLASTOISEEEEEEEE!!!!!!!!!!!!!!!!!!!!!!!!!'
BLASTOISEEEEEEEE!!!!!!!!!!!!!!!!!!!!!!!!!
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

> var poke = db.pokemons.findOne( {name: 'Blastoise'} )
> poke
{
        "_id" : ObjectId("56bd201d831b7e2c1d226b6b"),
        "name" : "Blastoise",
        "description" : "BLASTOISEEEEEEEE!!!!!!!!!!!!!!!!!!!!!!!!!",
        "type" : "Água",
        "attack" : 68,
        "defense" : 85,
        "height" : 1.6
}


```
