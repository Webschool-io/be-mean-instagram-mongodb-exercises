# MongoDB - Aula 04 - Exercício
Autor: Jackson de Fraga

## Exercício

1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Blastoise, Pikachu, Charmander e Mankey.
``` JavaScript
var query = { $or: [ { name: /blastoise/i}, {name: /pikachu/i}, {name: /charmander/i}, {name: /mankey/i} ]};
var mod = { $pushAll : { moves : ['soco','chute'] } };
var options= { multi : true };

db.pokemons.update(query, mod, options);
```

2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.
``` JavaScript

var query = {};
var mod = { $push : { moves : 'desvio' } };
var options= { multi : true };
db.pokemons.update(query, mod, options);

```

3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".
``` JavaScript

var query = { name : 'AindaNaoExisteMon' }
var mod = { 
    
    $set: {
        name: "AindaNaoExisteMon",
    },    
    $setOnInsert : {
        description: 'Sem maiores informações',
        type: null,
        attack: null,
        defense: null,
        height: null,
        moves: []
    }
}
var options = { upsert : true }
db.pokemons.update(query, mod, options)

```

4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.
``` JavaScript

var query = { moves : { $in : ['investida', 'soco'] } }
db.pokemons.find(query)

```

5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
``` JavaScript

var query = { moves : { $all : ['chute', 'soco'] } }
db.pokemons.find(query)

```

6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
``` JavaScript

var query = { type : { $ne : 'eletric' } };
db.pokemons.find(query)

```

7. Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.
``` JavaScript

var query = { 
    $and : [
        { moves : { $in : ['investida'] } },
        { defense : { $lte : 49 } }
    ] }
db.pokemons.find(query)

```

8. Remova **todos** os pokemons do tipo água e com attack menor que 50.
``` JavaScript
var query = { $and:[ { type: /water/i }, { attack: { $lt: 50 }} ]};
db.pokemons.remove(query);
```
