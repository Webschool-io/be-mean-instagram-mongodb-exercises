# MongoDB - Aula 03 - Exercício
	autor: Sérgio Kopplin

## 0.

```
Sergios-MacBook-Pro(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons

# Database utilizada
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("565509aa8567adc6cced29bd"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back",
  "type": "Seed",
  "attack": 40,
  "height": 2
}
{
  "_id": ObjectId("565509ab8567adc6cced29be"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents",
  "type": "Flame",
  "attack": 40,
  "height": 1.7
}
{
  "_id": ObjectId("565509af8567adc6cced29c0"),
  "name": "Nidoking",
  "description": "Nidoking's thick tail packs enormously destructive power",
  "type": "Drill",
  "attack": 50,
  "height": 1.4
}
{
  "_id": ObjectId("565509b08567adc6cced29c1"),
  "name": "Nidoqueen",
  "description": "Nidoqueen's body is encased in extremely hard scales",
  "type": "Drill",
  "attack": 50,
  "height": 1.3
}
{
  "_id": ObjectId("565509ad8567adc6cced29bf"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "type": "Shellfish",
  "attack": 40,
  "height": 1.6
}
Fetched 5 record(s) in 3ms
```

## 1. Listagem de todos os Pokemons com a altura menor que 0.5

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = { height: { $lt: 0.5 } }
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 0ms
```

## 2. Listagem de todos os Pokemons com a altura maior ou igual que 0.5

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = { height: { $gte: 0.5 } }
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("565509aa8567adc6cced29bd"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back",
  "type": "Seed",
  "attack": 40,
  "height": 2
}
{
  "_id": ObjectId("565509ab8567adc6cced29be"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents",
  "type": "Flame",
  "attack": 40,
  "height": 1.7
}
{
  "_id": ObjectId("565509af8567adc6cced29c0"),
  "name": "Nidoking",
  "description": "Nidoking's thick tail packs enormously destructive power",
  "type": "Drill",
  "attack": 50,
  "height": 1.4
}
{
  "_id": ObjectId("565509b08567adc6cced29c1"),
  "name": "Nidoqueen",
  "description": "Nidoqueen's body is encased in extremely hard scales",
  "type": "Drill",
  "attack": 50,
  "height": 1.3
}
{
  "_id": ObjectId("565509ad8567adc6cced29bf"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "type": "Shellfish",
  "attack": 40,
  "height": 1.6
}
Fetched 5 record(s) in 3ms
```

## 3. Listagem de todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ { height: { $gte: 0.5 } }, { type: "grass" } ] }
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 0ms
```

## 4. Listagem de todos os Pokemons com o nome Pikachu ou com attack menor ou igual que 0.5

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = { $or: [ { name: "Pikachu" }, { attack: { $lte: 0.5 } } ]  }
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 1ms
```

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menos ou igual 0.5

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = { $or: [{attack:{$gte:48}}, {height: { $lte: 0.5 } } ] }
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("565509af8567adc6cced29c0"),
  "name": "Nidoking",
  "description": "Nidoking's thick tail packs enormously destructive power",
  "type": "Drill",
  "attack": 50,
  "height": 1.4
}
{
  "_id": ObjectId("565509b08567adc6cced29c1"),
  "name": "Nidoqueen",
  "description": "Nidoqueen's body is encased in extremely hard scales",
  "type": "Drill",
  "attack": 50,
  "height": 1.3
}
Fetched 2 record(s) in 1ms
```
