# MongoDB - Aula 02 - Exercício
Autor: Juliano Padilha

## Criar uma database chamada de be-mean-pokemons

```
use be-mean-pokemons
switched to db be-mean-pokemons
```

## Liste quais database você possui neste servidor

```
show dbs
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
local             → 0.000GB
```

## Liste quais coleções você possui nessa database

```
show collections
> 
```

## Insira pelo menos 5 Pokemons a sua escolha

```
var pokemon1 = {name: "Bugossauro", description: "Buga seu código sem você perceber", attack: 60, defense: 45, height: 0.9}
db.pokemons.insert(pokemon1)
var pokemon2 = {name: "Javascripto", description: "Seu melhor companheiro de aventura", attack: 80, defense: 60, height: 0.5}
db.pokemons.insert(pokemon2)
var pokemon3 = {name: "Maczin", description: "Ataque de Maça", attack: 50, defense: 30, height: 0.6}
db.pokemons.insert(pokemon3)
var pokemon4 = {name: "Freelagem", description: "Faz tudo para sobreviver", attack: 45, defense: 70, height: 0.8}
db.pokemons.insert(pokemon4)
var pokemon5 = {name: "Gitus", description: "Sempre a sua melhor versão", attack: 70, defense: 50, height: 0.2}
db.pokemons.insert(pokemon5)
```

## Liste os Pokemons existentes na sua coleção

```
db.pokemons.find()
```

## Busque o Pokemon a sua escolha e armazene-o em uma variável chamda "poke"

```
var poke = {name: 'Gitus'}
poke = db.pokemons.findOne(poke)
```

## Modifique sua description e salvê-o

```
poke.description = "Faz push e faz pull"
db.pokemons.save(poke)
```