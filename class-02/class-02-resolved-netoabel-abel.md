# MongoDB - Aula 02 - Exercício
Autor: Abel Neto

## Criando uma database chamada be-mean-pokemons

```
be-mean> use be-mean-pokemons
```

## Listando as databases

```
be-mean-pokemons> show dbs
```

## Listando as collections

```
be-mean-pokemons> show collections
```

## Inserindo cinco pokémons

```
be-mean-pokemons> var pokemon = { name: "Bulbassaur", description: "Um sapo com folhas", attack: 30, defense: 20, height: 0.7 }
be-mean-pokemons> pokemons.save(pokemon)

be-mean-pokemons> var pokemon = { name: "Ivysaur", description: "Um sapo com uma flor", attack: 30, defense: 30, height: 1 }
be-mean-pokemons> db.pokemons.save(pokemon)

be-mean-pokemons> var pokemon = { name: "Venusaur", description: "Um sapo com um coqueiro", attack: 40, defense: 40, height: 2 }
be-mean-pokemons> db.pokemons.save(pokemon)

be-mean-pokemons> var pokemon = { name: "Charmander", description: "Um filhote de dinossauro com o rabo pegando fogo", attack: 30, defense: 20, height: 0.6 }
be-mean-pokemons> db.pokemons.save(pokemon)

be-mean-pokemons> var pokemon = { name: "Charmeleon", description: "Um pterodáctilo sem asas com o rabo pegando fogo", attack: 30, defense: 30, height: 1 }
be-mean-pokemons> db.pokemons.save(pokemon)
```

## Listando os pokémons

```
be-mean-pokemons> var pokemons = db.pokemons.find()
be-mean-pokemons> while(pokemons.hasNext()) { print(tojson(pokemons.next())) }
```

## Buscando um pokémon pelo nome e atualizando a descrição dele

```
be-mean-pokemons> var poke = db.pokemons.findOne({name:'Ivysaur'})
be-mean-pokemons> poke.description = 'Um sapo com uma bromélia'
be-mean-pokemons> db.pokemons.save(poke)
```
