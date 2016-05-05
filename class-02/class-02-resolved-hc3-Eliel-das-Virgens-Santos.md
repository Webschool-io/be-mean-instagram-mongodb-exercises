MongoDb - Aula 02 - Exercício

Autor : Eliel das Virgens


# Cria database be-mean-pokemons

```
darkSide(mongod-2.6.3) be-mean-restaurantes> use be-mean-pokemons
switched to db be-mean-pokemons
```

# Listagem das databases(passo 2)

```
darkSide(mongod-2.6.3) be-mean-pokemons> show dbs
admin                → (empty)
be-mean-instagram    → 0.078GB
be-mean-pokemons     → (empty)
be-mean-restaurantes → 0.078GB
be-mean-teste        → 0.078GB
local                → 0.078GB
```

# Listagem de coleções (passo 3)

```
darkSide(mongod-2.6.3) be-mean-pokemons> show collections
```

# Inserindo pelo menos 5 pokemons na base (passo 4)

```
darkSide(mongod-2.6.3) be-mean-pokemons> var pokemon1 = {'name':'Black Alien Mon' , 'description':'Pokemon da Rima' , 'attack':'250' , 'defense':'300' , 'height':1.3}
darkSide(mongod-2.6.3) be-mean-pokemons> ls
function ls() { [native code] }
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.insert(pokemon1)
Inserted 1 record(s) in 104ms
WriteResult({
  "nInserted": 1
})
darkSide(mongod-2.6.3) be-mean-pokemons> var pokemon2 = {'name':'Bnegao' , 'description':'Pokemon pensador' , 'attack':'150' , 'defense':'400' , 'height':1.1}
darkSide(mongod-2.6.3) be-mean-pokemons> var pokemon3 = {'name':'Marcelo D2' , 'description':'Pokemon Smoke Hard' , 'attack':'350' , 'defense':'500' , 'height':1.0}
darkSide(mongod-2.6.3) be-mean-pokemons> var pokemon4 = {'name':'Formiga' , 'description':'Pokemon do Baixo' , 'attack':'50' , 'defense':'200' , 'height':1.4}
darkSide(mongod-2.6.3) be-mean-pokemons> var pokemon5 = {'name':'Pedrinho' , 'description':'Pokemon da Batera' , 'attack':'80' , 'defense':'220' , 'height':1.2}
darkSide(mongod-2.6.3) be-mean-pokemons> var pokemon6 = {'name':'Speed Freaks' , 'description':'Pokemon Flow ou Levada' , 'attack':'500' , 'defense':9220' , 'height':1.2}
2016-02-07T10:36:43.100-0300 SyntaxError: Unexpected string
darkSide(mongod-2.6.3) be-mean-pokemons> var pokemon6 = {'name':'Speed Freaks' , 'description':'Pokemon Flow ou Levada' , 'attack':'500' , 'defense':900 , 'height':1.2}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.insert(pokemon2)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.insert(pokemon3)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.insert(pokemon4)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.insert(pokemon5)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.insert(pokemon6)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```

# Listar os pokemons existentes(passo 5)

```
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56b7478eb4620a5d4ec2cb52"),
  "name": "Black Alien Mon",
  "description": "Pokemon da Rima",
  "attack": "250",
  "defense": "300",
  "height": 1.3
}
{
  "_id": ObjectId("56b74890b4620a5d4ec2cb53"),
  "name": "Bnegao",
  "description": "Pokemon pensador",
  "attack": "150",
  "defense": "400",
  "height": 1.1
}
{
  "_id": ObjectId("56b74894b4620a5d4ec2cb54"),
  "name": "Marcelo D2",
  "description": "Pokemon Smoke Hard",
  "attack": "350",
  "defense": "500",
  "height": 1
}
{
  "_id": ObjectId("56b74897b4620a5d4ec2cb55"),
  "name": "Formiga",
  "description": "Pokemon do Baixo",
  "attack": "50",
  "defense": "200",
  "height": 1.4
}
{
  "_id": ObjectId("56b74899b4620a5d4ec2cb56"),
  "name": "Pedrinho",
  "description": "Pokemon da Batera",
  "attack": "80",
  "defense": "220",
  "height": 1.2
}
{
  "_id": ObjectId("56b7489bb4620a5d4ec2cb57"),
  "name": "Speed Freaks",
  "description": "Pokemon Flow ou Levada",
  "attack": "500",
  "defense": 900,
  "height": 1.2
}
Fetched 6 record(s) in 2ms
```
# Busque pokemons pelo nome e armazene em uma variável(passo 5)

```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {"name":"Pedrinho"}
darkSide(mongod-2.6.3) be-mean-pokemons> var poke = db.pokemons.findOne(query)
darkSide(mongod-2.6.3) be-mean-pokemons> poke
{
  "_id": ObjectId("56b74899b4620a5d4ec2cb56"),
  "name": "Pedrinho",
  "description": "Pokemon da Batera",
  "attack": "80",
  "defense": "220",
  "height": 1.2
}
```


# Alteração da descrição do Pokemon(passo 6)
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {"nome":"Pedrinho"}
darkSide(mongod-2.6.3) be-mean-pokemons> var poke = db.pokemons.findOne(poke)
darkSide(mongod-2.6.3) be-mean-pokemons> poke
{
  "_id": ObjectId("56b74899b4620a5d4ec2cb56"),
  "name": "Pedrinho",
  "description": "mudei",
  "attack": "80",
  "defense": "220",
  "height": 1.2
}
darkSide(mongod-2.6.3) be-mean-pokemons> poke.description = "Bateria psichodelica"
Bateria psichodelica
darkSide(mongod-2.6.3) be-mean-pokemons> poke
{
  "_id": ObjectId("56b74899b4620a5d4ec2cb56"),
  "name": "Pedrinho",
  "description": "Bateria psichodelica",
  "attack": "80",
  "defense": "220",
  "height": 1.2
}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.sabe(poke)
2016-02-07T12:37:27.554-0300 TypeError: Property 'sabe' of object be-mean-pokemons.pokemons is not a function
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
darkSide(mongod-2.6.3) be-mean-pokemons> poke
{
  "_id": ObjectId("56b74899b4620a5d4ec2cb56"),
  "name": "Pedrinho",
  "description": "Bateria psichodelica",
  "attack": "80",
  "defense": "220",
  "height": 1.2
}
darkSide(mongod-2.6.3) be-mean-pokemons> 
```
