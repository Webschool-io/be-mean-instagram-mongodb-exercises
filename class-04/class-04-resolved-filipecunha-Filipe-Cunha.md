1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
> query = {name: {$in:[/pikachu/i,/squirtle/i,/charmander/i, /bulbassauro/i]}}
> mod = {$pushAll:{moves:["ataque 1", "ataque 2"]}}
> options = {multi: true}
> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 16ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})



2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.
> query = {}
> mod = {$push:{moves:'desvio'}}
> db.pokemons.update(query, mod, options)
Updated 12 existing record(s) in 3ms
WriteResult({
  "nMatched": 12,
  "nUpserted": 0,
  "nModified": 12
})



3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".
> query = {name: /AindaNaoExisteMon/i}
> mod = {
  $set: {active: true},
  $setOnInsert: {
    name: "NaoExisteMon", 
    attack: null, 
    defense: null, 
    height: null, 
    description: "Sem maiores informações"
  }
}
> options = {upsert: true}
> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 4ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5657aa1db4b768d0fa329dc8")
})



4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.
> query = {moves:{$all:[/investida/i, /ataque 1/i]}}
> db.pokemons.find(query)
{
  "_id": ObjectId("5657a62a5df346e9f346ad33"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 100,
  "height": 0.4,
  "active": false,
  "moves": [
    "choque do trovão",
    "investida",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}



5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
> query = {moves:{$all:[/ataque 1/i, /ataque 2/i]}}
> db.pokemons.find(query)
{
  "_id": ObjectId("5657a62a5df346e9f346ad29"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2a"),
  "name": "Charmander",
  "description": "Esse é o cão chipando manga de fofinho",
  "type": "fogo",
  "attack": 53,
  "height": 0.6,
  "active": false,
  "moves": [
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2b"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad33"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 100,
  "height": 0.4,
  "active": false,
  "moves": [
    "choque do trovão",
    "investida",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
Fetched 4 record(s) in 8ms


6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
> query = {type: {$ne:"eletric"}}
> db.pokemons.find(query)
{
  "_id": ObjectId("5657a62a5df346e9f346ad29"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2a"),
  "name": "Charmander",
  "description": "Esse é o cão chipando manga de fofinho",
  "type": "fogo",
  "attack": 53,
  "height": 0.6,
  "active": false,
  "moves": [
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2b"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2c"),
  "name": "Cartepie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "defense": 35,
  "height": 0.3,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2d"),
  "name": "Suissamon",
  "description": "Pokemon hacker",
  "type": "hacker",
  "attack": 8001,
  "defense": 8000,
  "height": 1.69,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2e"),
  "name": "Dilmamon",
  "description": "Pokemon presidANTA",
  "type": "besta",
  "attack": 1,
  "defense": 1,
  "height": 1.6,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2f"),
  "name": "Cunhamon",
  "description": "Filho da puta",
  "type": "besta",
  "attack": 9990,
  "defense": 9999,
  "height": 1.8,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad30"),
  "name": "Calheirosmon",
  "description": "Irmão do filho da PUTA",
  "type": "besta",
  "attack": 8500,
  "defense": 9999,
  "height": 1.79,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad31"),
  "name": "FeliciANUS",
  "description": "Pastor BAITOLA E FILHO DA PUTA",
  "type": "besta",
  "attack": 666,
  "defense": 666,
  "height": 1.7,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad32"),
  "name": "Testemin",
  "description": "Pokemon de teste",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657aa1db4b768d0fa329dc8"),
  "active": true,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 11 record(s) in 8ms



7. Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.
> query = {defense:{$gt:49}}
> db.pokemons.find(query)
{
  "_id": ObjectId("5657a62a5df346e9f346ad2d"),
  "name": "Suissamon",
  "description": "Pokemon hacker",
  "type": "hacker",
  "attack": 8001,
  "defense": 8000,
  "height": 1.69,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2f"),
  "name": "Cunhamon",
  "description": "Filho da puta",
  "type": "besta",
  "attack": 9990,
  "defense": 9999,
  "height": 1.8,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad30"),
  "name": "Calheirosmon",
  "description": "Irmão do filho da PUTA",
  "type": "besta",
  "attack": 8500,
  "defense": 9999,
  "height": 1.79,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad31"),
  "name": "FeliciANUS",
  "description": "Pastor BAITOLA E FILHO DA PUTA",
  "type": "besta",
  "attack": 666,
  "defense": 666,
  "height": 1.7,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad32"),
  "name": "Testemin",
  "description": "Pokemon de teste",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "desvio"
  ]
}
Fetched 5 record(s) in 5ms



8. Remova **todos** os pokemons do tipo água e com attack menor que 50.
> query = {defense:{$lt:50}}
> db.pokemons.remove(query)
Removed 2 record(s) in 1ms
WriteResult({
  "nRemoved": 2
})
> db.pokemons.find()
{
  "_id": ObjectId("5657a62a5df346e9f346ad29"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2a"),
  "name": "Charmander",
  "description": "Esse é o cão chipando manga de fofinho",
  "type": "fogo",
  "attack": 53,
  "height": 0.6,
  "active": false,
  "moves": [
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2b"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2d"),
  "name": "Suissamon",
  "description": "Pokemon hacker",
  "type": "hacker",
  "attack": 8001,
  "defense": 8000,
  "height": 1.69,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad2f"),
  "name": "Cunhamon",
  "description": "Filho da puta",
  "type": "besta",
  "attack": 9990,
  "defense": 9999,
  "height": 1.8,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad30"),
  "name": "Calheirosmon",
  "description": "Irmão do filho da PUTA",
  "type": "besta",
  "attack": 8500,
  "defense": 9999,
  "height": 1.79,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad31"),
  "name": "FeliciANUS",
  "description": "Pastor BAITOLA E FILHO DA PUTA",
  "type": "besta",
  "attack": 666,
  "defense": 666,
  "height": 1.7,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad32"),
  "name": "Testemin",
  "description": "Pokemon de teste",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5657a62a5df346e9f346ad33"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 100,
  "height": 0.4,
  "active": false,
  "moves": [
    "choque do trovão",
    "investida",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5657aa1db4b768d0fa329dc8"),
  "active": true,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 10 record(s) in 2ms