# MongoDB - Aula 02 - Exercício
autor: Ivan Diniz

## Listagem das databases (passo 2)

```
$ show dbs
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
local             → 0.000GB

```

## Listagem das coleções (passo 3)
```
$ show collections
```
## Cadastro dos pokemons (passo 4)

```
$ var pokes = [
	{name: "Psyduck", description: "Muito misterioso por isso é bastante interessante", type:"Water",attack: 0.3, defense: 0.2, height: 0.7},
	{name: "Persian", description: "Só mais um gato grande e fofo", type:"Normal", attack: 0.3, defense: 0.2, height: 0.3},
	{name: "Alakazam", description: "Um psicopota psicólogo", type:"Psychic", attack: 0.3, defense: 20, height: 1},
	{name: "Mewtwo", description: "O magneto dos pokemons", type:"Psychic", attack: 0.6, defense: 0.4, height: 0.7},
	{name: "Scyther", description: "O traficante, corta planta como ninguém", type:"Bug", attack: 0.6, defense: 0.4, height: 1}
]

$ db.pokemons.save(pokes);
```

## Lista dos pokemons (passo 5)

```
$ db.pokemons.find();

{
  "_id": ObjectId("56781208ee41b458a6f2eacc"),
  "name": "Psyduck",
  "description": "Muito misterioso por isso é bastante interessante",
  "type": "Water",
  "attack": 0.3,
  "defense": 0.2,
  "height": 0.7
}
{
  "_id": ObjectId("56781208ee41b458a6f2eacd"),
  "name": "Persian",
  "description": "Só mais um gato grande e fofo",
  "type": "Normal",
  "attack": 0.3,
  "defense": 0.2,
  "height": 0.3
}
{
  "_id": ObjectId("56781208ee41b458a6f2eace"),
  "name": "Alakazam",
  "description": "Um psicopota psicólogo",
  "type": "Psychic",
  "attack": 0.3,
  "defense": 20,
  "height": 1
}
{
  "_id": ObjectId("56781208ee41b458a6f2eacf"),
  "name": "Mewtwo",
  "description": "O magneto dos pokemons",
  "type": "Psychic",
  "attack": 0.6,
  "defense": 0.4,
  "height": 0.7
}
{
  "_id": ObjectId("56781208ee41b458a6f2ead0"),
  "name": "Scyther",
  "description": "O traficante, corta planta como ninguém",
  "type": "Bug",
  "attack": 0.6,
  "defense": 0.4,
  "height": 1
}

```

## Persian (passo 6)

```
$ var poke = db.pokemons.findOne({name: "Persian"});
```

## Atualização do Persian (passo 6)

```
$ poke.description = "Só mais um gato grande, fofo e amarelo";
$ db.pokemons.save(poke);
```