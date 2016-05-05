
# MongoDB - Aula 02 - Exercício
autor: Felipe Leão

## Crie uma database chamada be-mean-pokemons

```
> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Liste quais databases você possui nesse servidor

```
> show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
be-mean-pokemons   0.078GB
local              0.078GB
```

## Liste quais coleções você possui nessa database

```
> show collections
pokemons
system.indexes
```

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height

```
> var pokemon = {name: 'Weezing', description: 'Bacana demais', attack: 90, defense: 120, height: 12}
> db.pokemons.save(pokemon)
...

```

## Liste os pokemons existentes na sua coleção

```
> var pokemon = db.pokemons.find()
> while (pokemon.hasNext()) { print(tojson(pokemon.next()))  }
{
	"_id" : ObjectId("5647aab44d79adb38b688cdc"),
	"name" : "Voltorb",
	"description" : "Pokemon sinistro.",
	"attack" : 30,
	"defense" : 50,
	"height" : 5
}
{
	"_id" : ObjectId("5647ab884d79adb38b688cdd"),
	"name" : "Weezing",
	"description" : "Bacana demais",
	"attack" : 90,
	"defense" : 120,
	"height" : 12
}
{
	"_id" : ObjectId("5647abe44d79adb38b688cde"),
	"name" : "Butterfree",
	"description" : "Voa e tudo mais",
	"attack" : 45,
	"defense" : 50,
	"height" : 11
}
{
	"_id" : ObjectId("5647ac314d79adb38b688cdf"),
	"name" : "Pidgey",
	"description" : "Pássaro cabuloso",
	"attack" : 45,
	"defense" : 40,
	"height" : 3
}
{
	"_id" : ObjectId("5647ac894d79adb38b688ce0"),
	"name" : "Ekans",
	"description" : "Cobra",
	"attack" : 60,
	"defense" : 44,
	"height" : 20
}
```

## Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada poke

```
> var poke = db.pokemons.findOne({name: 'Pidgey'})
```

## Modifique sua description e salvê-o

```
> poke.description = 'Parece um pardal'
Parece um pardal
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```