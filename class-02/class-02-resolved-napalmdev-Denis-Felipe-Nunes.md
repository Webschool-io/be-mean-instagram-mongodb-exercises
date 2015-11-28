# MongoDB - Aula 02 - Exercício
autor: Dênis Nunes

## Listagem das databases (passo 2)

```javascript
	show dbs
```

## Listagem das coleções (passo 3)

```javascript
	show collections
```


## Cadastro dos pokemons (passo 4)

```javascript
	var pokemon = {
	  name: "Pikachu",
	  description: "pokemon que solta um choque do capiroto enquanto fica falando obscenidades",
	  attack: 60,
	  defense: 20,
	  height: 0.5,
	  type: "Eletricidade"}
	db.pokedex.insert(pokemon)  
```

```javascript
	var pokemon = {
	  name: "Bulbasaur",
	  description: "pokemon da paz que tem uma fro nas costas",
	  attack: 50,
	  defense: 30,
	  height: 0.5,
	  type: "Grama"}
	db.pokedex.insert(pokemon)  
```

```javascript
	var pokemon = {
	  name: "Charmander",
	  description: "pokemon com fogo no rabo",
	  attack: 55,
	  defense: 25,
	  height: 0.6,
	  type: "Fogo"}
	db.pokedex.insert(pokemon)  
```

```javascript
	var pokemon = {
	  name: "Charizard",
	  description: "pokemon mal humorado com mais fogo no rabo ainda.",
	  attack: 65,
	  defense: 35,
	  height: 0.8,
	  type: "Fogo"}
	db.pokedex.insert(pokemon)  
```

```javascript
	var pokemon = {
	  name: "Squirtle",
	  description: "tartaruga que saliva bagarai.",
	  attack: 50,
	  defense: 30,
	  height: 0.5,
	  type: "Agua"}
	db.pokedex.insert(pokemon)  
```



## lista dos pokemons (passo 5)

```javascript
db.pokedex.find()

```

## pikachu (passo 6)

```javascript
  	var poke = db.pokedex.find({name:"Pikachu"})
```

## atualização do pikachu (passo 6)

```javascript
  	poke.description = "pokemon que solta choque do rabo e fica falando obscenidades"

  	db.pokedex.save(poke)
```
