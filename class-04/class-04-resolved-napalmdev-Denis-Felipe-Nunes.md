# MongoDB - Aula 04 - Exercício
autor: Dênis Nunes

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```js
    var ataques = ['Chute na Bunda', 'Chute na Cara'];
    var query = {name:{$in: ['Pikachu', 'Squirtle', 'Bulbasaur', 'Charmander']}};
    var mod = {$pushAll: {moves: ataques}};
    db.pokedex.update(query, mod, {multi: true});
```


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```js
    var mod = {$push: {moves: 'desvio'}};
    db.pokedex.update({}, mod, {multi: true});
```


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```js
var query = {name:/NaoExisteMon/i};
var options = {upsert: true};
var mod = {
        $set: {
            active: true
        }, 
        $setOnInsert: { 
            name: "NaoExisteMon", 
            attack: null, 
            defense: null, 
            height: null, 
            description: "Sem maiores informações"
        }
    };

db.pokedex.update(query, mod, options);
```


## Pesquisar todos os pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```js
    db.pokedex.find({moves: {$all: ['investida', /bomba dagua/i]}});
```


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```js
    db.pokedex.find({moves: {$all: [/chute na bunda/i, /chute na cara/i]}});
```


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```js
    db.pokedex.find({types: {$ne: 'electric'}});
```


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```js
    db.pokedex.find({$and: [{moves: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}}]});
```


## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```js
    db.pokedex.remove({$and: [{types: {$in: ['water']}}, {attack: {$lt: 50}}]});
```
