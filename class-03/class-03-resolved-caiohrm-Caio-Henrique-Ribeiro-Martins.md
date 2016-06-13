# MongoDB - Aula 03 - Exercício
autor: Caio Henrique Ribeiro Martins

## Listando Pokemons com altura menor que 0.5 (Passo 1)

caio-pc(mongod-3.2.7) be-mean-instagram> query = {height: {$lt:0.5}}
{
  "height": {
    "$lt": 0.5
  }
}
caio-pc(mongod-3.2.7) be-mean-instagram> db.pokemons.find(query)

## Listando Pokemons com altura maior ou igual que 0.5 (Passo 2)

caio-pc(mongod-3.2.7) be-mean-instagram> query = {height: {$gte:0.5}}
{
  "height": {
    "$gte": 0.5
  }
}
caio-pc(mongod-3.2.7) be-mean-instagram> db.pokemons.find(query)



## Listando Pokemons com altura menor ou igual que 0.5 E do tipo grama (Passo 3)

caio-pc(mongod-3.2.7) be-mean-instagram> query = {$or:[{height:{$lte:0.5}},{type:'grama'}]}
{
  "$or": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": "grama"
    }
  ]
}

caio-pc(mongod-3.2.7) be-mean-instagram> db.pokemons.find(query)



## Listando Pokemons com o name 'Pìkachu' OU com attack menor ou igual que 0.5 (Passo 4)

caio-pc(mongod-3.2.7) be-mean-instagram> query = {$or:[{name:/pikachu/i},{attack:{$lte:0.5}}]}
{
  "$or": [
    {
      "name": /pikachu/i
    },
    {
      "attack": {
        "$lte": 0.5
      }
    }
  ]
}




## Listando Pokemons com attack maior ou igual que 48 E com altura menor ou igual que 0.5 (Passo 5)


caio-pc(mongod-3.2.7) be-mean-instagram> query = {$and:[{height:{$lte:0.5}},{attack:{$gte:48}}]}
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "attack": {
        "$gte": 48
      }
    }
  ]
}





