# MongoDB - Aula 02 - Exercício
autor: Leonardo Colodette

## Listagem das databases (passo 2)
```
> show dbs
admin              (empty)
be-mean            0.078GB
be-mean-instagram  0.078GB
local              0.078GB
```

## Listagem das coleções (passo 3)

```
> show collections
>
```

## Cadastro dos pokemons (passo 4)
```
> var pokemonss = [
{name:"Porygon",description:"Porygon is capable of reverting itself entirely back to program data and entering cyberspace. This Pokémon is copy protected so it cannot be duplicated by copying",attack: 60,defense: 70,height: 8},
{name:"Jigglypuff",description: "Jigglypuff's vocal cords can freely adjust the wavelength of its voice. This Pokémon uses this ability to sing at precisely the right wavelength to make its foes most drowsy",attack: 2,defense: 1,height: 0.5},
{name:"Pikachu",description:"Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge",attack:55,defense: 30,height:4},
{name:"Serperior",description: "It only gives its all against strong opponents who are not fazed by the glare from Serperior's noble eyes",attack: 40,defense: 40,heigth: 3.30},
{name:"Metapod",description: "The shell covering this Pokémon's body is as hard as an iron slab. Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell",attack: 20, defense: 55 ,height : 0.7},
{name:"Lickitung",description: "Whenever Lickitung comes across something new, it will unfailingly give it a lick. It does so because it memorizes things by texture and by taste. It is somewhat put off by sour things",attack: 30,defense: 30,height: 1.2}
];

> db.pokemons.insert(pokemonss);
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

## Lista dos pokemons (passo 5)
```
> db.pokemons.find().pretty()
{
	"_id" : ObjectId("568f109f27ec7cce40760674"),
	"name" : "Porygon",
	"description" : "Porygon is capable of reverting itself entirely back to program data and entering cyberspace. This Pokémon is copy protected so it cannot be duplicated by copying",
	"attack" : 60,
	"defense" : 70,
	"height" : 8
}
{
	"_id" : ObjectId("568f109f27ec7cce40760675"),
	"name" : "Jigglypuff",
	"description" : "Jigglypuff's vocal cords can freely adjust the wavelength of its voice. This Pokémon uses this ability to sing at precisely the right wavelength to make its foes most drowsy",
	"attack" : 2,
	"defense" : 1,
	"height" : 0.5
}
{
	"_id" : ObjectId("568f109f27ec7cce40760676"),
	"name" : "Pikachu",
	"description" : "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge",
	"attack" : 55,
	"defense" : 30,
	"height" : 4
}
{
	"_id" : ObjectId("568f109f27ec7cce40760677"),
	"name" : "Serperior",
	"description" : "It only gives its all against strong opponents who are not fazed by the glare from Serperior's noble eyes",
	"attack" : 40,
	"defense" : 40,
	"heigth" : 3.3
}
{
	"_id" : ObjectId("568f109f27ec7cce40760678"),
	"name" : "Metapod",
	"description" : "The shell covering this Pokémon's body is as hard as an iron slab. Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell",
	"attack" : 20,
	"defense" : 55,
	"height" : 0.7
}
{
	"_id" : ObjectId("568f109f27ec7cce40760679"),
	"name" : "Lickitung",
	"description" : "Whenever Lickitung comes across something new, it will unfailingly give it a lick. It does so because it memorizes things by texture and by taste. It is somewhat put off by sour things",
	"attack" : 30,
	"defense" : 30,
	"height" : 1.2
}
```
## Pikachu (passo 6)
```
> var query = {name:"Pikachu"};
> db.pokemons.findOne(query);
{
	"_id" : ObjectId("568f109f27ec7cce40760676"),
	"name" : "Pikachu",
	"description" : "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge",
	"attack" : 55,
	"defense" : 30,
	"height" : 4
}

```

## Atualização do Pikachu (passo 6)

```
var pikachu = db.pokemons.findOne(query);

> pikachu.attack = 70;
70

> db.pokemons.save(pikachu);
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

> db.pokemons.findOne(query);
{
	"_id" : ObjectId("568f109f27ec7cce40760676"),
	"name" : "Pikachu",
	"description" : "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge",
	"attack" : 70,
	"defense" : 30,
	"height" : 4
}

```
