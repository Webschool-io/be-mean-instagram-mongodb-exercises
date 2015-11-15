# MongoDB - Aula 02 - Exercício
autor: Robson Luiz Valim de Bittencourt

## Listagem das databases (passo 2)
```

vostro(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
local              0.078GB

```

## Listagem das coleções (passo 3)

```

vostro(mongod-3.0.7) be-mean-pokemons> show collections
vostro(mongod-3.0.7) be-mean-pokemons> 

```


## Cadastro dos pokemons (passo 4)

```

vostro(mongod-3.0.7) be-mean-pokemons> var poke = {
	name: 'Mewtwo',
	description: 'Because its battle abilities were raised to the ultimate level, it thinks only of de feating its foes.',
	attack: 110,
	defense: 90,
	height: 20,
}

vostro(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Inserted 1 record(s) in 300ms
WriteResult({
  "nInserted": 1
})

vostro(mongod-3.0.7) be-mean-pokemons> var poke = {
	name: 'Mew',
	description: 'So rare that it is still said to be a mirage by many experts. Only a few people have seen it worldwide.',
	attack: 100,
	defense: 100,
	height: 4,
}

vostro(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

vostro(mongod-3.0.7) be-mean-pokemons> var poke = {
	name: 'Bibarel',
	description: 'A river dammed by Bibarel will never overflow its banks, which is appreciated by people nearby.',
	attack: 85,
	defense: 60,
	height: 10,
}

vostro(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

vostro(mongod-3.0.7) be-mean-pokemons> var poke = {
	name: 'Feebas',
	description: 'It is the shabbiest Pokmon of all. It forms in schools and lives at the bottom of rivers.',
	attack: 15,
	defense: 20,
	height: 6,
}

vostro(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

vostro(mongod-3.0.7) be-mean-pokemons> var poke = {
	name: 'Lugia',
	description: 'It sleeps in a deep-sea trench. If it flaps its wings, it is said to cause a 40-day storm.',
	attack: 90,
	defense: 130,
	height: 52,
}

vostro(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})


```

## Lista dos pokemons (passo 5)

```

vostro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5648c5d2e509dc2b3e263851"),
  "name": "Mewtwo",
  "description": "Because its battle abilities were raised to the ultimate level, it thinks only of de feating its foes.",
  "attack": 110,
  "defense": 90,
  "height": 20
}
{
  "_id": ObjectId("5648c5e1e509dc2b3e263852"),
  "name": "Mew",
  "description": "So rare that it is still said to be a mirage by many experts. Only a few people have seen it worldwide.",
  "attack": 100,
  "defense": 100,
  "height": 4
}
{
  "_id": ObjectId("5648c5efe509dc2b3e263853"),
  "name": "Bibarel",
  "description": "A river dammed by Bibarel will never overflow its banks, which is appreciated by people nearby.",
  "attack": 85,
  "defense": 60,
  "height": 10
}
{
  "_id": ObjectId("5648c5f9e509dc2b3e263854"),
  "name": "Feebas",
  "description": "It is the shabbiest Pokmon of all. It forms in schools and lives at the bottom of rivers.",
  "attack": 15,
  "defense": 20,
  "height": 6
}
{
  "_id": ObjectId("5648c603e509dc2b3e263855"),
  "name": "Lugia",
  "description": "It sleeps in a deep-sea trench. If it flaps its wings, it is said to cause a 40-day storm.",
  "attack": 90,
  "defense": 130,
  "height": 52
}
Fetched 5 record(s) in 4ms


```


## Pikachu (passo 6)

```

vostro(mongod-3.0.7) be-mean-pokemons> var query = {name: 'Lugia'}
vostro(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)


```

## Atualização do Pikachu (passo 6)

```

vostro(mongod-3.0.7) be-mean-pokemons> poke.description = 'O rei dos mares'
O rei dos mares
vostro(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 15ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```