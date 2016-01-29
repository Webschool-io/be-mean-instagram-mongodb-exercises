# MongoDb - Aula 04 - Exercício

1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.
3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".
4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.
5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.
8. Remova **todos** os pokemons do tipo água e com attack menor que 50.
9. Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores `$ne` e `$not`.


## Estrutura

```md
# MongoDB - Aula 02 - Exercício
autor: CAMILO CAMPOS

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

var query ={name: /pikachu/i}
var mod = {$pushAll: {moves: ['esfera elétrica', 'investida trovão']}}
db.pokemon.update(query,mod)

var query ={name: /squirtle/i}
var mod = {$pushAll: {moves: ['jato de agua', 'retirada']}}
db.pokemon.update(query,mod)

var query ={name: /bulbassauro/i}
var mod = {$pushAll: {moves: ['folha navalha', 'semente']}}
db.pokemon.update(query,mod)

var query ={name: /charmander/i}
var mod = {$pushAll: {moves: ['brasas', 'encarar']}}
db.pokemon.update(query,mod)

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

var query = {}
var mod = {$push: {moves: 'desvio'}}
var options = {multi: true}
db.pokemon.update(query, mod, options)

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

var query = {name: /aindaNaoExisteMon/i}
var mod = {$setOnInsert:
	{
	name: 'aindaNaoExisteMon',
	type: null,
	attack: null,
	defense: null,
	height: null,
	description: 'Sem maiores informações'
	}
}

var options = {upsert: true}
db.pokemon.update(query,mod, options)


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

var query = {moves: {$in [/investida/i, /brasas/i]}}
db.pokemon.find(query)

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

var query = {moves: {$all : [/desvio/i, /brasas/i]}}
db.pokemon.find(query)

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
var query = {type: {$not: /eletrico/i}}
db.pokemon.find(query)

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

var query = {$and: [ {moves: {$in: ['investida']}}, {defense: {$not: {$lte: 49}} }]} 
db.pokemon.find(query)



## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```

var query = {$and: [ {type: /agua/i}, {attack: {lt:50}}]}
db.pokemon.remove(query)


## Envio

[Veja na nossa Wiki](https://github.com/Webschool-io/be-mean-instagram/wiki/Exerc%C3%ADcios)

1. Crie o repositório específico do módulo. Ex.: be-mean-instagram-mongodb
2. Crie a solução do exercício localmente nesse repositório, usando sempre o padrão `class-04-resolved-suissa-Jean-Nascimento.md`
3. Dê um `fork` no repositório oficial https://github.com/Webschool-io/be-mean-instagram-mongodb-excercises
4. Vá até a pasta do módulo desejado e **COLE** seu arquivo na pasta `exercises`
5. Crie um **Pull Request** enviando **APENAS** o seu arquivo sem modificar mais nada.
6. Na mensagem do commit/pull request favor seguir o padrão: Jean Nascimento - MongoDB - Exercicio 02 resolvido
7. Levante as mão para o céu e agradeça se acaso tiver ... #brinks
