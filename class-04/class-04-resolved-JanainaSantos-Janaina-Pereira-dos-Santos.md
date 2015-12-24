# MongoDB - Aula 04 - Exercício
autor: Janaína P. dos Santos

## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: 
	Pikachu, Squirtle, Bulbassauro e Charmander.
```
> var query = {name: /Pikachu/i}
> var mod = {$pushAll:{moves:['esfera eletrica', ' investida do trovão']}};
> db.pokemons.update(query, mod)

> var query = { name: /Squirtle/i}
> var mod = {$pushAll:{moves:['raio', 'giro']}}
> db.pokemons.update(query, mod)

> var query = {name: /Bulbassauro/i}
> var mod = {$pushAll:{moves:['raio', 'teste']}}
> db.pokemons.update(query, mod)

> var query = {name: /Charmander/i}
> var mod = {$pushAll:{moves:['brasas',  'encarar']}}
> db.pokemons.update(query, mod)
```

## 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
> var query = {}
> var mod = {$push:{moves:"desvio"}}
> var options = {multi:true}
> db.pokemons.update(query, mod, options)
```

## 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
> var query = {name: /AindaNaoExisteMon/i}
> var mod = {setOnInsert:
	{
		name:"AindaNaoExisteMon",
		attack: null,
		defense: null,
		type: null,
		height: null,
		description:"Sem maiores descrições"
	}
}
> var options = {upsert:true}
> db.pokemons.update(query, mod, options)
```

## 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
> var query = {moves:{$in:[/investida/i, /brasas/i]}}
> db.pokemons.find(query);	
```

## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
``` 
> var query = {moves:{$all:[/desvio/i, /brasas/i]}}
> db.pokemons.find(query);	
```

## 6. Pesquisar **todos** que não são do tipo 'elétrico'.##
``` 
> var query = {type:{$not:/eletric/i}}
> db.pokemons.find(query)
```

## 7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
``` 
> var query = {$and:[{moves:{$in:['investida']}},{defense:{$not:{$lte:49}}]}
> db.pokemons.find(query)
```

## 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.##
``` 
> var query = {$and:[{type:/agua/i},{attack:{$lt:50}}]}
> db.pokemons.remove(query)
```

## 9. Diferença entre operadores '$ne' e '$not'.##

O operador $ne busca os documentos que não é igual ao valor especificado. Não aceita regex.
O operador $not busca os documentos que é o oposto do filtro.

	

 
 


