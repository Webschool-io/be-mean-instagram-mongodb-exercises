# MongoDB - Aula 02 - Exercício
autor: Guilherme Felipe de Sousa

## Criando Database

```
> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases

```
> show dbs
be-mean       → 0.078GB
be-mean-teste → 0.078GB
local         → 0.078GB
```

## Listagem das coleções da DB

```
> show collections
>
```

## Inserindo os Pokemons

```
> function Pokemon(name, description, attack, defense, height)
  {this.name = name; 
   this.description = description;
   this.attack = attack;
   this.defense = defense;
   this.height = height; 
  };

> var p = new Pokemon('Charmander', 'Tem um rabo quente', 30, 20, 8.5)
> db.pokemons.insert(p);
> var p = new Pokemon('Vileplume', 'Cogumelo azul do ventania', 40,40, 18.6)
> db.pokemons.insert(p);
> var p = new Pokemon('Raticate', 'Tem presas grandes e elas crescem de forma constatante, ele mastiga até paredes', 40, 30,18.5)
> db.pokemons.insert(p);
> var p = new Pokemon('Spearow', 'Galisé minuscula que machuca', 30, 20, 2.0)
> db.pokemons.insert(p);
> var p = new Pokemon('Sandshrew', 'Tatu bolinha manso', 40,40,12.0)
> db.pokemons.insert(p);
> var p = new Pokemon('Ekans','A famosa cascavel (sogra)', 30,20,6.9)
> db.pokemons.insert(p);
> var p = new Pokemon('Vileplume', 'Cogumelo azul do ventania', 40,40, 18.6)
> db.pokemons.insert(p);
```

## Lista dos pokemons

```
> db.pokemons.find()
{
  "_id": ObjectId("56ad056653448d2fab7f1dfd"),
  "name": "Charmander",
  "description": "Tem uma chama na ponta da calda, a chama queima mais forte quando ele fica furioso",
  "attack": 30,
  "defense": 20,
  "height": 8.5
}
{
  "_id": ObjectId("56ad06b64484bcd68498514e"),
  "name": "Raticate",
  "description": "Tem presas grandes e elas crescem de forma constatante, ele mastiga até paredes",
  "attack": 40,
  "defense": 30,
  "height": 18.5
}
{
  "_id": ObjectId("56ad072b4484bcd68498514f"),
  "name": "Spearow",
  "description": "Galisé minuscula que machuca",
  "attack": 30,
  "defense": 20,
  "height": 2
}
{
  "_id": ObjectId("56ad07954484bcd684985150"),
  "name": "Ekans",
  "description": "A famosa cascavel (sogra)",
  "attack": 30,
  "defense": 20,
  "height": 6.9
}
{
  "_id": ObjectId("56ad07d54484bcd684985151"),
  "name": "Sandshrew",
  "description": "Tatu bolinha manso",
  "attack": 40,
  "defense": 40,
  "height": 12
}
{
  "_id": ObjectId("56ad0a1740706acf8c2cc9c1"),
  "name": "Vileplume",
  "description": "Cogumelo azul do ventania",
  "attack": 40,
  "defense": 40,
  "height": 18.6
}
Fetched 6 record(s) in 1ms
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56ad056653448d2fab7f1dfd"),
  "name": "Charmander",
  "description": "Tem uma chama na ponta da calda, a chama queima mais forte quando ele fica furioso",
  "attack": 30,
  "defense": 20,
  "height": 8.5
}
{
  "_id": ObjectId("56ad06b64484bcd68498514e"),
  "name": "Raticate",
  "description": "Tem presas grandes e elas crescem de forma constatante, ele mastiga até paredes",
  "attack": 40,
  "defense": 30,
  "height": 18.5
}
{
  "_id": ObjectId("56ad072b4484bcd68498514f"),
  "name": "Spearow",
  "description": "Galisé minuscula que machuca",
  "attack": 30,
  "defense": 20,
  "height": 2
}
{
  "_id": ObjectId("56ad07954484bcd684985150"),
  "name": "Ekans",
  "description": "A famosa cascavel (sogra)",
  "attack": 30,
  "defense": 20,
  "height": 6.9
}
{
  "_id": ObjectId("56ad07d54484bcd684985151"),
  "name": "Sandshrew",
  "description": "Tatu bolinha manso",
  "attack": 40,
  "defense": 40,
  "height": 12
}
{
  "_id": ObjectId("56ad0a1740706acf8c2cc9c1"),
  "name": "Vileplume",
  "description": "Cogumelo azul do ventania",
  "attack": 40,
  "defense": 40,
  "height": 18.6
}
Fetched 6 record(s) in 1ms
```

## Query de busca do Pokemon

```
> var query = { name: 'Ekans' }
> var p = db.pokemons.findOne(query)
```

## Atualização do Pokemon

```
> p.description = 'A famosa sogra!!! (cascavel)'
> db.pokemons.save(p)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```