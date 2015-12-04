# MongoDB - Aula 02 - Exercício
autor: Arthur Nascimento Assuncao

## Crie uma database chamada be-mean-pokemons
```
arthur@assuncao ~/cursos/be-mean/be-mean-instagram-mongodb-excercises $ mongo be-mean-pokemons
MongoDB shell version: 3.0.7
connecting to: be-mean-pokemons
Server has startup warnings: 
2015-11-15T13:05:44.300-0200 I CONTROL  [initandlisten] 
2015-11-15T13:05:44.300-0200 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.
2015-11-15T13:05:44.300-0200 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2015-11-15T13:05:44.300-0200 I CONTROL  [initandlisten] 
2015-11-15T13:05:44.301-0200 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/defrag is 'always'.
2015-11-15T13:05:44.301-0200 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2015-11-15T13:05:44.301-0200 I CONTROL  [initandlisten] 
> db
be-mean-pokemons
> 
```

## Liste quais databases você possui nesse servidor
```
> show dbs
be-mean    0.078GB
entregadb  0.203GB
local      0.078GB
>
```

## Liste quais coleções você possui nessa database
```
> show collections
> 
```

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height
```
> db.pokemons.insert([{
...     "name": "Bulbasaur",
...     "attack": 49,
...     "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
...     "defense": 49,
...     "height": "7"
... },
... {
...     "attack": 62,
... "defense": 63,
... "height": "10",
... "name": "Ivysaur",
... "description": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon."
... },
... {
...     "name": "Venusaur",
...     "attack": 82,
... "defense": 83,
... "height": "20",
... "description": "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people."
... },
... {
...     "name": "Charmander",
...     "attack": 52,
... "defense": 43,
... "height": "6",
...     "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely."
... },
... {
...     "name": "Charmeleon",
...     "attack": 64,
... "defense": 58,
... "height": "11",
...     "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color."
... }])
BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 5,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]
})
> 
```

## Liste os pokemons existentes na sua coleção
```
> db.pokemons.find({})
{ "_id" : ObjectId("564bd85b4a7aaa28e49ebdaf"), "name" : "Bulbasaur", "attack" : 49, "description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", "defense" : 49, "height" : "7" }
{ "_id" : ObjectId("564bd85b4a7aaa28e49ebdb0"), "attack" : 62, "defense" : 63, "height" : "10", "name" : "Ivysaur", "description" : "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon." }
{ "_id" : ObjectId("564bd85b4a7aaa28e49ebdb1"), "name" : "Venusaur", "attack" : 82, "defense" : 83, "height" : "20", "description" : "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people." }
{ "_id" : ObjectId("564bd85b4a7aaa28e49ebdb2"), "name" : "Charmander", "attack" : 52, "defense" : 43, "height" : "6", "description" : "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely." }
{ "_id" : ObjectId("564bd85b4a7aaa28e49ebdb3"), "name" : "Charmeleon", "attack" : 64, "defense" : 58, "height" : "11", "description" : "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color." }
```

## Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`
```
> var poke = db.pokemons.findOne({name: "Bulbasaur"})
> poke
{
	"_id" : ObjectId("564bd85b4a7aaa28e49ebdaf"),
	"name" : "Bulbasaur",
	"attack" : 49,
	"description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
	"defense" : 49,
	"height" : "7"
}
> 
```

## Modifique sua `description` e salvê-o
```
> poke.description = "Bulbasaur eh o primeiro pokemon"
Bulbasaur eh o primeiro pokemon
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find({name: "Bulbasaur"})
{ "_id" : ObjectId("564bd85b4a7aaa28e49ebdaf"), "name" : "Bulbasaur", "attack" : 49, "description" : "Bulbasaur eh o primeiro pokemon", "defense" : 49, "height" : "7" }
> 
```