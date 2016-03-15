#MongoDB - Aula 04 - Exercício
autor: Anderson Machado Lemos

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander. ##
```
var query = {$or: [{name: /pikachu/i},{name: /squirtle/i},{name: /bulbassauro/i},{name: /charmander/i}]}
var attacks = ['ataque rápido', 'bola elétrica']
var mod = {$pushAll: {attacks : attacks }}
var opt = {multi: true}

db.pokemons.update(query, mod, opt)
```
## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
var query = {}
var mod = {$push: {moves:'desvio'}}
var options = {multi:true}
db.pokemons.update(query,mod,options)
```
## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = {name: /AindaNaoExisteMon/i}
var mod = {setOnInsert:
    {
        name:"AindaNaoExisteMon",
        attack: null,
        defense: null,
        type: null,
        height: null,
        description:"Sem maiores descrições"
    }
}
var options = {upsert:true}
db.pokemons.update(query, mod, options)
```
## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
var query = {moves:{$in:[/investida/i,/esfera elétrica/i]}}
db.pokemons.find(query)
```
## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
var query = {moves:{$in:[/desvio/i,/esfera elétrica/i]}}
db.pokemons.find(query)
```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
var query = {type:{$not:/elétrico/i}}
db.pokemons.find(query)
```
## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
var query = {$and:[{moves:{$in:[/investida/i]}},{attack:{$not:{$lte:49}}}]}
db.pokemons.find(query)
```
## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var query = {$and:[{type:/agua/i},{attack:{$lt:50}}]}
db.pokemons.remove(query)
```

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not. ##

**$ne**:  Retorna documentos onde o valor não seja igual. E não suporta REGEX.

**$not**: Retorna objetos que não satisfaçam a condição do campo (inclui a não existencia do campo). Suporta REGEX.



