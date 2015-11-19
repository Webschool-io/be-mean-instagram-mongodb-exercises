#MongoDB - Aula02 - Exercicio
autor: Raphael De Pieri

##Criando database be-mean-pokemon
localhost(mongod-2.6.11) test> use be-mean-pokemon
switched to db be-mean-pokemon

##Listar database no servidor
localhost(mongod-2.6.11) be-mean-pokemon> show dbs
be-mean-instagram  0.078GB
be-mean-teste      0.078GB
local              0.078GB
be-mean            0.078GB
be-mean-pokemon    0.078GB
admin              (empty)


##Adicionando pokemons
localhost(mongod-2.6.11) be-mean-pokemon> var pokemon = {'name': 'Blastoise', 'descripton': 'Dino de agua', 'type': 'agua', 'attack':83, height:1.6}
localhost(mongod-2.6.11) be-mean-pokemon> db.pokemon.save(pokemon)
Inserted 1 record(s) in 5ms
WriteResult({
  "nInserted": 1
})
localhost(mongod-2.6.11) be-mean-pokemon> var pokemon = {'name': 'Raichu', 'descripton': 'Dispara raios', 'type': 'eletrico', 'attack':90, height:0.73}
localhost(mongod-2.6.11) be-mean-pokemon> db.pokemon.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
var pokemon = {'name': 'Mew', 'descripton': 'Ele é foda', 'type': 'foda', 'attack':100, height:0.41}
localhost(mongod-2.6.11) be-mean-pokemon> db.pokemon.save(pokemon)
Inserted 1 record(s) in 5ms
WriteResult({
  "nInserted": 1
})
var pokemon = {'name': 'Lugia', 'descripton': 'Passarinho', 'type': 'psychic', 'attack':90, height:5.21}
localhost(mongod-2.6.11) be-mean-pokemon> db.pokemon.save(pokemon)
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})
localhost(mongod-2.6.11) be-mean-pokemon> var pokemon = {'name': 'Entei', 'descripton': 'Cachorrinho', 'type': 'fire', 'attack':115, height:2.11}
localhost(mongod-2.6.11) be-mean-pokemon> db.pokemon.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

##Listar os pokemons salvos
localhost(mongod-2.6.11) be-mean-pokemon> db.pokemon.find()
{
  "_id": ObjectId("564bf12b86c921063a253dab"),
  "name": "Charmander",
  "descripton": "Dino de fogo",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564bf1c274c2b60515ab703a"),
  "name": "Blastoise",
  "descripton": "Dino de agua",
  "type": "agua",
  "attack": 83,
  "height": 1.6
}
{
  "_id": ObjectId("564bf20a74c2b60515ab703b"),
  "name": "Raichu",
  "descripton": "Dispara raios",
  "type": "eletrico",
  "attack": 90,
  "height": 0.73
}
{
  "_id": ObjectId("564bf2b984278e06c3a97639"),
  "name": "Mew",
  "descripton": "Ele é foda",
  "type": "foda",
  "attack": 100,
  "height": 0.41
}
{
  "_id": ObjectId("564bf33a4e1bb2c3dd915d40"),
  "name": "Lugia",
  "descripton": "Passarinho",
  "type": "psychic",
  "attack": 90,
  "height": 5.21
}
{
  "_id": ObjectId("564bf38f4e1bb2c3dd915d41"),
  "name": "Entei",
  "descripton": "Cachorrinho",
  "type": "fire",
  "attack": 115,
  "height": 2.11
}
Fetched 6 record(s) in 2ms

##Buscando pokemon pelo nome
var query = {name: 'Lugia'}
localhost(mongod-2.6.11) be-mean-pokemon> var poke = db.pokemon.findOne(query)
localhost(mongod-2.6.11) be-mean-pokemon> poke
{
  "_id": ObjectId("564bf33a4e1bb2c3dd915d40"),
  "name": "Lugia",
  "descripton": "Passarinho",
  "type": "psychic",
  "attack": 90,
  "height": 5.21
}

##Alterando um valor e salvando
localhost(mongod-2.6.11) be-mean-pokemon> var poke = db.pokemon.findOne(query)
localhost(mongod-2.6.11) be-mean-pokemon> poke
{
  "_id": ObjectId("564bf33a4e1bb2c3dd915d40"),
  "name": "Lugia",
  "descripton": "Passarinho",
  "type": "psychic",
  "attack": 90,
  "height": 5.21
}
localhost(mongod-2.6.11) be-mean-pokemon> poke.descripton = "Passarinho muito grande"
Passarinho muito grande
localhost(mongod-2.6.11) be-mean-pokemon> poke
{
  "_id": ObjectId("564bf33a4e1bb2c3dd915d40"),
  "name": "Lugia",
  "descripton": "Passarinho muito grande",
  "type": "psychic",
  "attack": 90,
  "height": 5.21
}
ocalhost(mongod-2.6.11) be-mean-pokemon> db.pokemon.save(poke)
Updated 1 existing record(s) in 5ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
localhost(mongod-2.6.11) be-mean-pokemon> db.pokemon.find()
{
  "_id": ObjectId("564bf12b86c921063a253dab"),
  "name": "Charmander",
  "descripton": "Dino de fogo",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564bf1c274c2b60515ab703a"),
  "name": "Blastoise",
  "descripton": "Dino de agua",
  "type": "agua",
  "attack": 83,
  "height": 1.6
}
{
  "_id": ObjectId("564bf20a74c2b60515ab703b"),
  "name": "Raichu",
  "descripton": "Dispara raios",
  "type": "eletrico",
  "attack": 90,
  "height": 0.73
}
{
  "_id": ObjectId("564bf2b984278e06c3a97639"),
  "name": "Mew",
  "descripton": "Ele é foda",
  "type": "foda",
  "attack": 100,
  "height": 0.41
}
{
  "_id": ObjectId("564bf33a4e1bb2c3dd915d40"),
  "name": "Lugia",
  "descripton": "Passarinho muito grande",
  "type": "psychic",
  "attack": 90,
  "height": 5.21
}
{
  "_id": ObjectId("564bf38f4e1bb2c3dd915d41"),
  "name": "Entei",
  "descripton": "Cachorrinho",
  "type": "fire",
  "attack": 115,
  "height": 2.11
}
Fetched 6 record(s) in 2ms




##Contando os restaurantes

db.restaurantes.find({}).count()
25359
