### 1. Crie uma database chamada be-mean-pokemons;

```JS
leonardo(mongod-2.6.10) test> use be-mean-pokemons
switched to db be-mean-pokemons
```

### 2. Liste quais databases você possui nesse servidor;

```JS
leonardo(mongod-2.6.10) be-mean-pokemons> show dbs
local                    0.078GB
multivision              0.078GB
be-mean-teste            0.078GB
be-mean                  0.078GB
denguereport             0.078GB
globo-newsource-v2-test  0.078GB
globo-newsource-v2       0.078GB
denguereport_test        0.078GB
be-mean-pokemons         0.078GB
admin                    (empty)
```

### 3. Liste quais coleções você possui nessa database;

```JS
leonardo(mongod-2.6.10) be-mean-pokemons> show collections
pokemons        0.001MB / 0.008MB
system.indexes  0.000MB / 0.008MB
```

4. Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;

```JS

var Charizard = {
  'name':'Charizard',
  'description':'Dragão feroz',
  'type': 'Flame', 
  'attack': '40', 
  'height': '1.7m' 
};

db.pokemons.save(Charizard);

var Pidgeot = {
  'name':'Pidgeot',
  'description':'This Pokémon has a dazzling plumage of beautifully glossy feathers',
  'type': 'Bird', 
  'attack': '40', 
  'height': '1.5m' 
};

db.pokemons.save(Pidgeot);

var Raichu = {
  'name':'Raichu',
  'description':'If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.',
  'type': 'Mouse', 
  'attack': '50', 
  'height': '0.8m' 
};

db.pokemons.save(Raichu);

var Arcanine = {
  'name':'Arcanine',
  'description':'Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night. ',
  'type': 'Legendary', 
  'attack': '60', 
  'height': '1.9m' 
};

db.pokemons.save(Arcanine);

var Blastoise = {
  'name':'Blastoise',
  'description':'Blastoise has water spouts that protrude from its shell',
  'type': 'Shellfish', 
  'attack': '40', 
  'height': '1.6m' 
};

db.pokemons.save(Blastoise);

```

### 5. Liste os pokemons existentes na sua coleção;
```JS
leonardo(mongod-2.6.10) be-mean-pokemons> show collections
pokemons        0.001MB / 0.008MB
system.indexes  0.000MB / 0.008MB
```

### 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;
```JS

> var query = {'name':'Pidgeot'};

> var poke = db.pokemons.findOne(query)

> poke

``` 

### 7. Modifique sua `description` e salvê-o

```JS

leonardo(mongod-2.6.10) be-mean-pokemons> poke.description = 'This Pokémon is beatiful'
This Pokémon is beatiful

leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(poke);

Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

``` 
