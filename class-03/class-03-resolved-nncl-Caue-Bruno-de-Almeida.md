#MongoDB - Aula 03 - Exercício
Autor: Cauê Bruno de Almeida

# 1. Liste todos os pokemons com a altura meno que 0.5
```
be-mean-pokemons> var query = { height: {$lt: 0.5} }
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645223f141cff9e62ddfbe7"),
  "name": "Charmilion",
  "description": "Foguinho",
  "type": "bird",
  "attack": 35,
  "defense": 20,
  "height": 0.25
}
{
  "_id": ObjectId("56452240141cff9e62ddfbe8"),
  "name": "Mew",
  "description": "hMMMMMMmmmm",
  "type": "null",
  "attack": 10000,
  "defense": 10000,
  "height": 0.1
}
{
  "_id": ObjectId("56452240141cff9e62ddfbe9"),
  "name": "Mew Two",
  "description": "Opa já era",
  "type": "null",
  "attack": 40000,
  "defense": 40000,
  "height": 0.4
}
{
  "_id": ObjectId("56452240141cff9e62ddfbeb"),
  "name": "Dog Pi",
  "description": "Non ecxiste",
  "type": "ball",
  "attack": 0.1,
  "defense": 0.5,
  "height": 0.01
}
{
  "_id": ObjectId("5645233d141cff9e62ddfbec"),
  "name": "pickachu",
  "description": "Non ecxiste",
  "type": "electric",
  "attack": 0.1,
  "defense": 0.5,
  "height": 0.01
}
Fetched 5 record(s) in 2ms
```

# 2. Liste todos os pokemons com a altura maior ou igualque 0.5
```
be-mean-pokemons> var query = { height: { $gte: 0.5 } }
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56452240141cff9e62ddfbea"),
  "name": "Blastoise",
  "description": "O rei das água",
  "type": "turtle",
  "attack": 50,
  "defense": 30,
  "height": 20
}
Fetched 1 record(s) in 1ms
```

# 3. Liste todos os pokemons com a altura menor ou igual que 0.5 E do tipo grama

```
be-mean-pokemons> var query = { height: {$lte: 0.5}, $and: [{type: 'grama'}] }
be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

# 4. Liste todos os pokemons com o nome Pikachu OU com o ataque MENOR OU IGUAL QUE 0.5

```
be-mean-pokemons> var query = { name: 'pickachu', $or: [{ attack: {$lte: 0.5} }] }
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645233d141cff9e62ddfbec"),
  "name": "pickachu",
  "description": "Non ecxiste",
  "type": "electric",
  "attack": 0.1,
  "defense": 0.5,
  "height": 0.01
}
Fetched 1 record(s) in 1ms
```

# 5. Liste todos os pokemons com o attack MAIOR OU IGUAL A 48 E com height MENOR OU IGUAL A 0.5

```
be-mean-pokemons> var query = { attack: {$gte: 48}, $and: [ { height: {$lte: 0.5} } ] }
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56452240141cff9e62ddfbe8"),
  "name": "Mew",
  "description": "hMMMMMMmmmm",
  "type": "null",
  "attack": 10000,
  "defense": 10000,
  "height": 0.1
}
{
  "_id": ObjectId("56452240141cff9e62ddfbe9"),
  "name": "Mew Two",
  "description": "Opa já era",
  "type": "null",
  "attack": 40000,
  "defense": 40000,
  "height": 0.4
}
Fetched 2 record(s) in 1ms
```
