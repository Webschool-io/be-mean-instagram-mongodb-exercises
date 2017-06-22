##MongoDB -Aula03- Exercícios
##autor: MARCOS SANTOS

##1 - Liste todos Pokemons com a altura menor que 0.5:
be-mean-pokemons> db.pokemons.find({'height':{$lt:0.5}})
{
  "_id": ObjectId("56490a49055d13b8416e9c67"),
  "name": "Swinub",
  "description": "Sua comida favorita é um cogumelo que cresce sob a cobertura de grama morta.",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

##2 - Liste todos Pokemons com a altura maior ou igual que 0.5:
be-mean-pokemons> db.pokemons.find({'height':{$gte:0.5}})
{
  "_id": ObjectId("56490978055d13b8416e9c63"),
  "name": "Magcargo",
  "description": "Este Pokémon retorna ao seu tamanho original mergulhando-se no magma.",
  "attack": 30,
  "defense": 50,
  "height": 0.8
}
{
  "_id": ObjectId("56490a26055d13b8416e9c64"),
  "name": "Remoraid",
  "description": " Quando a evolução se aproxima, este Pokémon viaja a jusante dos rios.",
  "attack": 30,
  "defense": 20,
  "height": 0.6
}
{
  "_id": ObjectId("56490a30055d13b8416e9c65"),
  "name": "Corsola",
  "description": "Se qualquer ramo quebra, este Pokémon cresce de volta em apenas uma noite..",
  "attack": 30,
  "defense": 40,
  "height": 0.6
}
{
  "_id": ObjectId("56490a38055d13b8416e9c66"),
  "name": "Piloswine",
  "description": "Possui cabelo bem curto por conta do calor do NE do Brasil",
  "attack": 50,
  "defense": 40,
  "height": 1.1
}
Fetched 4 record(s) in 6ms

##3 - Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama:
be-mean-pokemons> db.pokemons.find({$and:[{'type':'grama'},{'height':{$lte:0.5}}]})
{
  "_id": ObjectId("56490a49055d13b8416e9c67"),
  "name": "Swinub",
  "description": "Sua comida favorita é um cogumelo que cresce sob a cobertura de grama morta.",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "grama"
}
Fetched 1 record(s) in 2ms

##4 - Liste todos Pokemons com o name 'Pikachu' OU com attack menor ou igual que 0.5:
be-mean-pokemons> db.pokemons.find({$or:[{'name':'Pikachu'},{'height':{$lte:0.5}}]})
{
  "_id": ObjectId("56490a49055d13b8416e9c67"),
  "name": "Swinub",
  "description": "Sua comida favorita é um cogumelo que cresce sob a cobertura de grama morta.",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "grama"
}
Fetched 1 record(s) in 7ms

##5 - Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5:
 be-mean-pokemons> db.pokemons.find({$or:[{'height':{$lte:0.5}},{'attack':{$gte:48}}]})
{
  "_id": ObjectId("56490a38055d13b8416e9c66"),
  "name": "Piloswine",
  "description": "Possui cabelo bem curto por conta do calor do NE do Brasil",
  "attack": 50,
  "defense": 40,
  "height": 1.1
}
{
  "_id": ObjectId("56490a49055d13b8416e9c67"),
  "name": "Swinub",
  "description": "Sua comida favorita é um cogumelo que cresce sob a cobertura de grama morta.",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "grama"
}
Fetched 2 record(s) in 1ms
