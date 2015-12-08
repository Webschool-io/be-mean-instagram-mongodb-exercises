```md
# MongoDB - Aula 02 - Exercício
```
autor: JOSÉ CARLOS DA SILVA DE CARVALHO	
```
## Listagem das databases (passo 2)
```
carlos-pc(mongod-2.4.9) be-mean-pokemons> show dbs
be-mean-pokemons   0.203GB
local              0.078GB
be-mean-instagram  0.203GB
database           0.203GB
bemean             0.203GB
```
## Listagem das coleções (passo 3)
```
carlos-pc(mongod-2.4.9) be-mean-pokemons> show collections
pokemons        0.000MB / 0.012MB
system.indexes  0.000MB / 0.008MB
```
## Cadastro dos pokemons (passo 4)
```
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert({name: 'Hitmonlee', description: "Lutador com chute potente", attack: 120, defence: 80, height: 1.5})
Inserted 1 record(s) in 1ms
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert({name: "Raichu", description: "Rato gigante, a evolução do pickachu", attack: 90, defence: 50, height: 0.8})
Inserted 1 record(s) in 1ms
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert({name: "Sandshrew", description: "Parece um tatu e sobrevive no deserto", attack: 60, defence: 80, height: 0.6})
Inserted 1 record(s) in 1ms
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert({name: "Sandshrew", description: "Rato grande azul e com orelhas gigantes", attack: 30, defence: 20, height: 0.4})
Inserted 1 record(s) in 1ms
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert({name: "Voltorb", description: "Se parece com uma pokebola e pode explodir", attack: 20, defence: 20, height: 0.5})
Inserted 1 record(s) in 1ms
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert({name: "Exeggcute", description: "Esse é muito estranho, parece um monte de ovos", attack: 20, defence: 40, height: 0.4})
Inserted 1 record(s) in 1ms
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert({name: "Cubone", description: "Bixinho de pelúcia com uma caveira na cabeça", attack: 30, defence: 40, height: 0.4})
Inserted 1 record(s) in 1ms
```

## Lista dos pokemons (passo 5)
```
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.find()
'{
  "_id": ObjectId("565fb437096fb0ddd2aaac99"),
  "name": "Hitmonlee",
  "description": "Lutador com chute potente",
  "attack": 120,
  "defence": 80,
  "height": 1.5
}'
...outros 6 aqui
Fetched 7 record(s) in 4ms
```

## Sandshrew (passo 6)
```
carlos-pc(mongod-2.4.9) be-mean-pokemons> var poke = db.pokemons.findOne({name: "Sandshrew"})


## Atualização do Sandshrew (passo 7	)
carlos-pc(mongod-2.4.9) be-mean-pokemons> poke.description = "Uma nova descrição para o pokemon"
Estava com nome duplicado, então:
carlos-pc(mongod-2.4.9) be-mean-pokemons> poke.name = "Magna"
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 0ms

```
