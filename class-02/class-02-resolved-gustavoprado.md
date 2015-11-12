#MongoDB - Aula 02 - Exercício
autor: Gustavo Prado

## Crie uma database chamada be-mean-pokemons

```
gustavo-Inspiron-3442(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemons> 

```
## Liste as databases existentes no servidor

```
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemons> show dbs
local             → 0.078GB
be-mean           → 0.078GB
be-mean-instagram → 0.078GB

```

## Liste as coleções que existe na database selecionada

```

gustavo-Inspiron-3442(mongod-3.0.7) be-mean-instagram> show collections
pokemons       → 0.001MB / 0.008MB
system.indexes → 0.000MB / 0.008MB
teste          → 0.000MB / 0.008MB

```

## Insira pelo menos 5 pokémons a sua escolha utilizando o mesmo padrão de campos utilizados: name, description, attack, defense e height

```
var pokemon = [
{
	'name' : 'Charmander',
	'description' : 'Charmander is a Fire-type Pokémon.',
	'attack' : '52',
	'defense' : '43',
	'height' : '0.6m'
},
{
	'name' : 'Squirtle',
	'description' : 'Squirtle is a Water-type Pokémon.',
	'attack' : '48',
	'defense' : '65',
	'height' : '0.5m'
},
{
	'name' : 'Pikachu',
	'description' : 'Pikachu is an Eletric-type Pokémon.',
	'attack' : '55',
	'defense' : '30',
	'height' : '0.4m'
},
{
	'name' : 'Bulbasaur',
	'description' : 'Bulbasaur is a dual-type Grass/Poison Pokémon.',
	'attack' : '49',
	'defense' : '49',
	'height' : '0.7m'
},
{
	'name' : 'Meowth',
	'description' : 'Meowth is a Normal-type Pokémon',
	'attack' : '45',
	'defense' : '35',
	'height' : '0.4'
}];

be-mean-pokemon> db.pokemons.insert(pokemon)

```

## Liste os pokemons existentes na sua coleção

```
db.pokemons.find()

```

## Busque um pokemon e armazene-o em uma variavel chamada 'poke'

```

gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemon> var poke = {name: 'Pikachu'}
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemon> var p = db.pokemons.findOne(poke)
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemon> poke
{
  "name": "Pikachu"
}

```

## Modifique sua description e salve

```

gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemon> p.description
pokemon eletrico
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemon> p.description = 'pokemon eletrico alterado'
pokemon eletrico alterado
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemon> p.description
pokemon eletrico alterado

gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemon> db.pokemons.save(p)
Updated 1 existing record(s) in 7ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```