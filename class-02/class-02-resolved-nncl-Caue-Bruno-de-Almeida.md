#MongoDB - Aula 02 - Exercício
Autor: Cauê Bruno de Almeida

## 1
`use be-mean-pokemons`

## 2
`show dbs`

## 3
`show collections`

## 4
```
var pokemon = {
    'name' : 'Charmilion',
    'description' : 'Foguinho',
    'type' : 'bird',
    'attack' : 35,
    'defense' : 20,
    'height' : 0.25
}

db.pokemons.insert(pokemon)
var pokemon = {
    'name' : 'Mew',
    'description' : 'hMMMMMMmmmm',
    'type' : 'null',
    'attack' : 10000,
    'defense' : 10000,
    'height' : 0.1
}

db.pokemons.insert(pokemon)

var pokemon = {
    'name' : 'Mew Two',
    'description' : 'Opa já era',
    'type' : 'null',
    'attack' : 40000,
    'defense' : 40000,
    'height' : 0.4
}

db.pokemons.insert(pokemon)

var pokemon = {
    'name' : 'Blastoise',
    'description' : 'O rei das água',
    'type' : 'turtle',
    'attack' : 50,
    'defense' : 30,
    'height' : 20
}

db.pokemons.insert(pokemon)

var pokemon = {
    'name' : 'Dog Pi',
    'description' : 'Psiquicão',
    'type' : 'ball',
    'attack' : 0.1,
    'defense' : 0.5,
    'height' : 0.01
}

db.pokemons.insert(pokemon)
```

### 5
`db.pokemons.find()`

### 6

```
var query = {name : 'Dog Pi'}
var poke = db.pokemons.findOne(query)
```

### 7

```
poke.description = 'Non ecxiste'
db.pokemons.save(poke)
```