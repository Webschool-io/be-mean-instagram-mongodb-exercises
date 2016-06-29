# MongoDB - Aula 04 - Exercício
Autor: Caio Henrique Ribeiro Martins

## Exercício

1. **Adicionar** 
2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Charmander e Bulbassauro.

query = {$or:[{name:/pikachu/i},{name:/squirtle/i},{name:/charmander/i}]}
mod = {$pushAll:{moves:['ataque 1','ataque 2']}}
var option = {multi:true}
db.pokemons.update(query,mod,options)

2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.

query ={}
mod ={$push:{moves:'desvio'}}
options = {multi:true}

db.pokemons.update(query,mod,options)

3. **Adicionar** 
o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

query = {name:'AindaNaoExisteMon'}
mod = { $setOnInsert: {name: "NaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"} }
options ={upsert:true}

db.pokemons.update(query,mod,options)

4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

query = {moves:{$in:[/investida/i,/teste/i]}}
db.pokemons.find(query)

5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

var query = { moves : { $all : ['ataque 1','ataque 2'] } }
db.pokemons.find(query)

6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

var query = { type : { $ne : 'eletric' } };
db.pokemons.find(query)

7. Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

query = {$and:[{moves:{$in:['investida']}},{defense:{$lte:49}}]}
db.pokemons.find(query)

8. Remova **todos** os pokemons do tipo água e com attack menor que 50.

query = {$or:[{type:/agua/i},{attack:{$lt:50}}]}
db.pokemons.remove(query)




