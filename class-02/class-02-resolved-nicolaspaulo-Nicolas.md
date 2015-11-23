MongoDB - Aula 02 - Exercício
Autor: Nicolas de Paulo Rosa

Criando a database be-mean-pokemons(1)

```
mongo be-mean-pokemons
MongoDB shell version: 3.0.7
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.8
MEAN(mongod-3.0.7) be-mean-pokemons>
```

Listando quais databases possui no servidor(2)

```
MEAN(mongod-3.0.7) be-mean-pokemons> show dbs
local              0.078GB
be-mean-teste      0.078GB
be-mean-instagram  0.078GB
be-mean            0.078GB
```

Listando as coleções que possui nessa database(3)

```
MEAN(mongod-3.0.7) be-mean-pokemons> show collections
```

Inserindo os 5 pokemons(4)

```
MEAN(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Pikachu','description':'Pikachu é foda e fofo <3','type':'fogo','attack': 58,'height': 0.9}
MEAN(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 321ms
WriteResult({
  "nInserted": 1
})
MEAN(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Fire Blast','description':'Explosão de fogo','type':'fogo','attack': 23,'height': 0.2}
MEAN(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 0ms
WriteResult({
  "nInserted": 1
})
MEAN(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Aqua Tail','description':'Cauda de água','type':'água','attack': 65,'height': 1.9}
MEAN(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
MEAN(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Electro Ball','description':'Bola elétrica motherfucker','type':'elétrico','attack': 666,'height': 1.3}
MEAN(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
MEAN(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Confusion','description':'Psiquico das loucura','type':'psiquico','attack': 120,'height': 5.9}
MEAN(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

Listando os pokemons existentes em minha coleção(5)

```
MEAN(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564691ece5af3c3b5de963f1"),
  "name": "Pikachu",
  "description": "Pikachu é foda e fofo <3",
  "type": "fogo",
  "attack": 58,
  "height": 0.9
}
{
  "_id": ObjectId("5646920fe5af3c3b5de963f2"),
  "name": "Fire Blast",
  "description": "Explosão de fogo",
  "type": "fogo",
  "attack": 23,
  "height": 0.2
}
{
  "_id": ObjectId("56469229e5af3c3b5de963f3"),
  "name": "Aqua Tail",
  "description": "Cauda de água",
  "type": "água",
  "attack": 65,
  "height": 1.9
}
{
  "_id": ObjectId("5646923de5af3c3b5de963f4"),
  "name": "Electro Ball",
  "description": "Bola elétrica motherfucker",
  "type": "elétrico",
  "attack": 666,
  "height": 1.3
}
{
  "_id": ObjectId("5646924ce5af3c3b5de963f5"),
  "name": "Confusion",
  "description": "Psiquico das loucura",
  "type": "psiquico",
  "attack": 120,
  "height": 5.9
}
```

Buscando o pokemon pikachu armazenando ele em uma variável poke(6)

```
MEAN(mongod-3.0.7) be-mean-pokemons> var buscapokemon = {name: 'Pikachu'}
MEAN(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(buscapokemon)
MEAN(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("564691ece5af3c3b5de963f1"),
  "name": "Pikachu",
  "description": "Pikachu é foda e fofo <3",
  "type": "fogo",
  "attack": 58,
  "height": 0.9
}
```
Modificando sua descrição e salvando a modificação(7)

```
MEAN(mongod-3.0.7) be-mean-pokemons> poke.description = 'Pika-pika, pi-pika, chuuuuu!'
Pika-pika, pi-pika, chuuuuu!
MEAN(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
MEAN(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("564691ece5af3c3b5de963f1"),
  "name": "Pikachu",
  "description": "Pika-pika, pi-pika, chuuuuu!",
  "type": "fogo",
  "attack": 58,
  "height": 0.9
}
```
