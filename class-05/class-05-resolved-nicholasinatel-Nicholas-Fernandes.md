# MongoDB - Aula 05 - Exercício

User: [nicholasinatel](https://github.com/nicholasinatel)

Autor: Nicholas Fernandes de Almeida Paolillo

# Importar as collections `restaurantes` e `pokemons`.

```

mongoimport --host 127.0.0.1 --db pokeagenda --collection pokemons --drop --file /Users/Nicholas/Downloads/pokemon-seed/pokemons.json

mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file /Users/Nicholas/Downloads/restaurantes.json

```

# Distinct por `cuisine` na restaurantes.

```

db.restaurantes.distinct(`cuisine`)


```

# Distinct por `types` na pokemons.

```

db.pokemons.distinct(`types`)

```
# As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5).

```

db.pokemons.find({},{name: 1, _id: 0 }).limit(5).skip(5 * 5)


```


# Group ou Aggregate contando a quantidade de pokemons de cada tipo.

```

db.pokemons.group({
    initial: {total: 0},                 
    reduce: function(curr, result) {    
        curr.types.forEach(function(type) {
        if(result[type]) {
            result[type]++;    
        } else {
            result[type] = 1;    
        }  
        result.total++;
    });                                    
    }
});


```
# Realizar 3 counts na pokemons.

```

db.pokemons.count()

db.pokemons.count( {attack : { $gt: 40 }})

db.pokemons.count({ types: ["normal","flying"]})


```
