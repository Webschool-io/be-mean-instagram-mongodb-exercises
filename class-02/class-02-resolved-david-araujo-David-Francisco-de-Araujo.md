# MongoDB - Aula 02 - Exercício

autor: David Araujo

## 1. Crie uma database chamada be-mean-pokemons;
```
>use be-mean-pokemons
switched to db be-mean-pokemons
```
## 2. Liste quais databases você possui nesse servidor;

```
>show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
local              0.078GB
test               0.078GB
```

## 3. Liste quais coleções você possui nessa database;

```
>show collections
>
```
## 4. Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;

```
> pokemons
[
	{
		"name" : "Bulbasaur",
		"description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
		"attack" : "49",
		"defense" : "49",
		"height" : "0.7"
	},
	{
		"name" : "Ivysaur",
		"description" : "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
		"attack" : "62",
		"defense" : "63",
		"height" : "1"
	},
	{
		"name" : "Venusaur",
		"description" : "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
		"attack" : "82",
		"defense" : "83",
		"height" : "2"
	},
	{
		"name" : "Charmander",
		"description" : "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
		"attack" : "52",
		"defense" : "43",
		"height" : "0.6"
	},
	{
		"name" : "Charmeleon",
		"description" : "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.",
		"attack" : "64",
		"defense" : "58",
		"height" : "1.1"
	},
	{
		"name" : "Charizard",
		"description" : "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
		"attack" : "84",
		"defense" : "78",
		"height" : "1.7"
	}
]

> db.pokemons.insert(pokemons)
BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 6,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]
})
```

## 5. Liste os pokemons existentes na sua coleção;

```
> db.pokemons.find().pretty()
{
	"_id" : ObjectId("5722ad9bdaee77205cdb3e8f"),
	"name" : "Bulbasaur",
	"description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
	"attack" : "49",
	"defense" : "49",
	"height" : "0.7"
}
{
	"_id" : ObjectId("5722ad9bdaee77205cdb3e90"),
	"name" : "Ivysaur",
	"description" : "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
	"attack" : "62",
	"defense" : "63",
	"height" : "1"
}
{
	"_id" : ObjectId("5722ad9bdaee77205cdb3e91"),
	"name" : "Venusaur",
	"description" : "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
	"attack" : "82",
	"defense" : "83",
	"height" : "2"
}
{
	"_id" : ObjectId("5722ad9bdaee77205cdb3e92"),
	"name" : "Charmander",
	"description" : "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
	"attack" : "52",
	"defense" : "43",
	"height" : "0.6"
}
{
	"_id" : ObjectId("5722ad9bdaee77205cdb3e93"),
	"name" : "Charmeleon",
	"description" : "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.",
	"attack" : "64",
	"defense" : "58",
	"height" : "1.1"
}
{
	"_id" : ObjectId("5722ad9bdaee77205cdb3e94"),
	"name" : "Charizard",
	"description" : "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
	"attack" : "84",
	"defense" : "78",
	"height" : "1.7"
}
```

## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada 'poke';

```
> var poke = db.pokemons.findOne({"name" : "Charizard"})
> poke
{
	"_id" : ObjectId("5722ad093572045c6629f9ce"),
	"name" : "Charizard",
	"description" : "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
	"attack" : "84",
	"defense" : "78",
	"height" : "1.7"
}
```

## 7. Modifique sua 'description' e salvê-o

```
> poke.description = "Pokemon FOOOODA!!!"
Pokemon FOOOODA!!!
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

> db.pokemons.find({name:"Charizard"}).pretty()
{
	"_id" : ObjectId("5722ad093572045c6629f9ce"),
	"name" : "Charizard",
	"description" : "Pokemon FOOOODA!!!",
	"attack" : "84",
	"defense" : "78",
	"height" : "1.7"
}
```
