
1. Criar uma database chamada be-mean-pokemons;

	> use be-mean-pokemons
	switched to db be-mean-pokemons

2. Liste quais databases você possui nesse servidor;

	> show databases
	be-mean            0.078GB
	be-mean-instagram  0.078GB
	local              0.078GB

3. Insira pelo menos 5 pokemons a sua escolha utilizando o mesmo padrao de campos, name, description, attack, defense e height;

	var pokemon = {'name': 'Zigzagoon', 'description': 'Inquieto, vagueia em todos os lugares, em todos os momentos', 'type':'Normal', attack:45, height: 0.4, defense: 1.6};
	db.pokemons.insert(pokemon);

	var pokemon = {'name': 'Zigzagoon', 'description': 'Inquieto, vagueia em todos os lugares, em todos os momentos', 'type':'Normal', attack:45, height: 0.4, defense: 1.6};
	db.pokemons.insert(pokemon);

	var pokemon = {'name': 'Zigzagoon', 'description': 'Inquieto, vagueia em todos os lugares, em todos os momentos', 'type':'Normal', attack:45, height: 0.4, defense: 1.6};
	db.pokemons.insert(pokemon);

	var pokemon = {'name': 'Zigzagoon', 'description': 'Inquieto, vagueia em todos os lugares, em todos os momentos', 'type':'Normal', attack:45, height: 0.4, defense: 1.6};
	db.pokemons.insert(pokemon);

	var pokemon = {'name': 'Zigzagoon', 'description': 'Inquieto, vagueia em todos os lugares, em todos os momentos', 'type':'Normal', attack:45, height: 0.4, defense: 1.6};
	db.pokemons.insert(pokemon);

4. Liste os pokemons existentes na sua coleção;
	
	db.pokemons.find();

5. Busque o pokemon a sua escolha pelo nome e armazene-o em uma variavel chamada poke;

	var query = {'name':'Zigzagoon'};
	var poke = db.pokemons.findOne(query);

6. modifique sua description e salve-o

	poke.description = 'blablabla';

	db.pokemons.save(poke);