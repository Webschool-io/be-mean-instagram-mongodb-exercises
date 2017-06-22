# MongoDB - Aula 03 - Exercício
autor: Kayo glauco

## Pokemons com altura menor que 0.5

```sh
> var qry = {height: {$lt: 0.5}}
> db.pokemons.find(qry)

{
  "_id": ObjectId("56f08be2732a2b6d85865d31"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56f08d921f8af4bc23be8770"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56f0903e1f8af4bc23be8773"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
```

## Pokemons com altura maior ou igual 0.5
```
> var qry = {height: {$gte: 0.5}}
> db.pokemons.find(qry)
{
  "_id": ObjectId("56f08da81f8af4bc23be8771"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56f08e251f8af4bc23be8772"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56f6a155ec09b890ae15305b"),
  "name": "Hoothoot",
  "description": "Coruja da hora",
  "attack": 20,
  "defense": 20,
  "height": 0.7
}
{
  "_id": ObjectId("56f6a17cec09b890ae15305c"),
  "name": "Hoothoot",
  "description": "Coruja da hora",
  "attack": 20,
  "defense": 20,
  "height": 0.7
}
{
  "_id": ObjectId("56f6a186ec09b890ae15305d"),
  "name": "Ledyba",
  "description": "Joaninha ruim de briga",
  "attack": 10,
  "defense": 20,
  "height": 1
}
{
  "_id": ObjectId("56f6a190ec09b890ae15305e"),
  "name": "Ledian",
  "description": "Abelha mascarada",
  "attack": 20,
  "defense": 20,
  "height": 1.4
}
{
  "_id": ObjectId("56f6a198ec09b890ae15305f"),
  "name": "Spinarak",
  "description": "Spider terror",
  "attack": 30,
  "defense": 20,
  "height": 0.5
}
{
  "_id": ObjectId("56f6a1a2ec09b890ae153060"),
  "name": "Crobat",
  "description": "Mascote do batman",
  "attack": 50,
  "defense": 40,
  "height": 1.8
}
```

## Pokemons com altura altura menor ou igual a 0.5 e do tipo grama
```
> var qry = {height: {$lte: 0.5}, $and: [{type: 'grama'}]}
> db.pokemons.find(qry)
{
  "_id": ObjectId("56f08d921f8af4bc23be8770"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
```

## Pokemons com o nome Pikachu ou com ataque menor ou igual que 0.5
```
> var qry = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
> db.pokemons.find(qry)
{
  "_id": ObjectId("56f08be2732a2b6d85865d31"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
```

## Pokemons com o ataque maior ou igual que 48 e com altura menor ou igual que 0.5
```
> var qry = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(qry)
{
  "_id": ObjectId("56f08be2732a2b6d85865d31"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56f08d921f8af4bc23be8770"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56f08e251f8af4bc23be8772"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
```
