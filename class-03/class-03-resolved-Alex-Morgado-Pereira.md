# MongoDB - Aula 03 - Exercício
autor: Alex Morgado Pereira

## Pokemons com altura menor que 0.5

```
alex-morgado(mongod-3.2.6) be-mean-pokemons> var query = {height: {$lt: 0.5}}
alex-morgado(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
	"_id": ObjectId("57a54f5f1f8da2cc48912f26"),
	"name": "Arcanine",
	"tipo": "fogo",
	"hp": 90,
	"ataque": 110,
	"defesa": 80,
	"ataqueEspecial": 100,
	"defesaEspecial": 80,
	"velocidade": 95,
	"total": 555,
	"height": 0.4
}
{
	"_id": ObjectId("57a54fee1f8da2cc48912f27"),
	"name": "Archeops",
	"tipo": "Rocha / Voador",
	"hp": 75,
	"ataque": 140,
	"defesa": 65,
	"ataqueEspecial": 112,
	"defesaEspecial": 65,
	"velocidade": 110,
	"total": 567,
	"height": 0.3
}
{
	"_id": ObjectId("57a550c61f8da2cc48912f2a"),
	"name": "Garchomp",
	"tipo": "Dragão/Terra",
	"hp": 108,
	"ataque": 170,
	"defesa": 115,
	"ataqueEspecial": 120,
	"defesaEspecial": 95,
	"velocidade": 92,
	"total": 700,
	"descricao": "Ele voa com uma velocidade igual a de um jato. Ele nunca permite que sua presa escape.",
	"height": 0.2
}
Fetched 3 record(s) in 4ms

```
## Listar Pokemons maior ou igual a 0.5

```
alex-morgado(mongod-3.2.6) be-mean-pokemons> var query = {height: {$gte: 0.5}}
alex-morgado(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
	"_id": ObjectId("57a550301f8da2cc48912f28"),
	"name": "Goodra",
	"tipo": "Dragão",
	"hp": 90,
	"ataque": 100,
	"defesa": 70,
	"ataqueEspecial": 110,
	"defesaEspecial": 150,
	"velocidade": 80,
	"total": 600,
	"height": 0.6
}
{
	"_id": ObjectId("57a550771f8da2cc48912f29"),
	"name": "Hydreigon",
	"tipo": "Noturno/Dragão",
	"hp": 92,
	"ataque": 105,
	"defesa": 90,
	"ataqueEspecial": 125,
	"defesaEspecial": 90,
	"velocidade": 98,
	"total": 600,
	"height": 1
}
Fetched 2 record(s) in 2ms
```
## Listar Pokemons menor ou igual que 0.5 E do tipo Grama

```
alex-morgado(mongod-3.2.6) be-mean-pokemons> var query = {$and:[{height: {$lte: 0.5}},{tipo: "grama"}]}
alex-morgado(mongod-3.2.6) be-mean-pokemons> query
{
	"$and": [
	{
	"height": {
	"$lte": 0.5
}
},
{
	"tipo": "grama"
}
]
}
alex-morgado(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
	"_id": ObjectId("57aca7da2db883de63fc4720"),
	"name": "Venusaur",
	"tipo": "grama",
	"hp": 78,
	"ataque": 90,
	"defesa": 90,
	"ataqueEspecial": 100,
	"defesaEspecial": 90,
	"velocidade": 90,
	"height": 0.5,
	"total": 450
}
Fetched 1 record(s) in 1ms

```
## Liste todos os Pokemons com o nome "Pikachu" OU com ataque menor ou igual que 0.5

```
alex-morgado(mongod-3.2.6) be-mean-pokemons> var query = {$or: [{name: "Pikachu"},{ataque: {$lte: "0.5"}}]}
alex-morgado(mongod-3.2.6) be-mean-pokemons> query
{
	"$or": [
	{
	"name": "Pikachu"
},
{
	"ataque": {
	"$lte": "0.5"
}
}
]
}
alex-morgado(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 3ms

```
## Listagem de todos os Pokemons com o attack maior ou igual que 48 E com height menor ou igual que 0.5

```
alex-morgado(mongod-3.2.6) be-mean-pokemons> var query = {$and: [{ataque:{$gte: 48}},{height: {$lte: 0.5}}]}
alex-morgado(mongod-3.2.6) be-mean-pokemons> query
{
	"$and": [
	{
	"ataque": {
	"$gte": 48
}
},
{
	"height": {
	"$lte": 0.5
}
}
]
}
alex-morgado(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
	"_id": ObjectId("57a54f5f1f8da2cc48912f26"),
	"name": "Arcanine",
	"tipo": "fogo",
	"hp": 90,
	"ataque": 110,
	"defesa": 80,
	"ataqueEspecial": 100,
	"defesaEspecial": 80,
	"velocidade": 95,
	"total": 555,
	"height": 0.4
}
{
	"_id": ObjectId("57a54fee1f8da2cc48912f27"),
	"name": "Archeops",
	"tipo": "Rocha / Voador",
	"hp": 75,
	"ataque": 140,
	"defesa": 65,
	"ataqueEspecial": 112,
	"defesaEspecial": 65,
	"velocidade": 110,
	"total": 567,
	"height": 0.3
}
{
	"_id": ObjectId("57a550c61f8da2cc48912f2a"),
	"name": "Garchomp",
	"tipo": "Dragão/Terra",
	"hp": 108,
	"ataque": 170,
	"defesa": 115,
	"ataqueEspecial": 120,
	"defesaEspecial": 95,
	"velocidade": 92,
	"total": 700,
	"descricao": "Ele voa com uma velocidade igual a de um jato. Ele nunca permite que sua presa escape.",
	"height": 0.2
}
{
	"_id": ObjectId("57aca7da2db883de63fc4720"),
	"name": "Venusaur",
	"tipo": "grama",
	"hp": 78,
	"ataque": 90,
	"defesa": 90,
	"ataqueEspecial": 100,
	"defesaEspecial": 90,
	"velocidade": 90,
	"height": 0.5,
	"total": 450
}
Fetched 4 record(s) in 1ms
```