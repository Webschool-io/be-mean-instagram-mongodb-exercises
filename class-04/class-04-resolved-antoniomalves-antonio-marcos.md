# MongoDB - Aula 04 - Exercicio
autor: Antonio Marcos Alves

## Adicionar 2 ataques dois atques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander - passo 01

'''
var query = {name: /Charmander/i}
var mod   = {$pushAll: {moves: ['cospe fogo', 'brilha no escuro']}}
db.pokemons.update(query, mod)

var query = {name: /Squirtle/i}
var mod   = {$pushAll: {moves: ['olho de gelo', 'congela inimigos']}}
db.pokemons.update(query, mod)

var query = {name: /Pikachu/i}
var mod   = {$pushAll: {moves: ['giro do trovão', 'arrasta pedras']}}
db.pokemons.update(query, mod)

var query = {name: /Bulbassauro/i}
var mod   = {$pushAll: {moves: ['couro resistente', 'aguenta muita porrada']}}
db.pokemons.update(query, mod)
'''

## Adicionar 1 movimento em todos os pokemons: 'desvio' - passo 02

'''
var query   = {}
var mod     = {$push: {moves: 'desvio'}}
var options = {multi: true} 
db.pokemons.update(query, mod, options)
'''

## Adicionar o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição: "Sem maiores informações" - passo 03

'''
var query   = {name: /AindaNaoExisteMon/i}
var mod     = {$setOnInsert:{name: 'AindaNaoExisteMon', description: 'Sem maiores informações', type: null, attack: null, height: null, active: null, moves: null}}
var options = {upsert:1}
db.pokemons.update(query, mod, options)
'''

## Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito - passo 04

'''
var query = {moves: {$in: [/investida/i, /cospe fogo/i]}}
db.pokemons.find(query)
'''

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito - passo 05

'''
var query = {moves: {$all:[/olho de gelo/i, /congela inimigos/i]}}
db.pokemons.find(query)
'''

## Pesquisar todos que não são do tipo elétrico. - passo 06

'''
var query = {type: {$not: /elétrico/i}}
db.pokemons.find(query)
'''


## Pesquisar todos os pokemons que tenham o ataque 'investida' E tenham a defesa não menor ou igual a 49. - passo 07

'''
var query = {$and: [{moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}}]}
db.pokemons.find(query)
'''

## Remova todos os pokemons do tipo agua e com attack menor que 50.

'''
var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}
db.pokemons.remove(query)
'''
