# Javascript - Instanciação

**autor**: Jansser Santos

Este artigo tem como objetivo detalhar as maneiras como o Javascript cria e instancia as variáveis.

## Hoisting
Hoisting é um comportamento padrão do Javascript que move todas as declarações de variáveis para o início do escopo, as declarações de variáveis são processadas antes da execução de qualquer outro código. Dessa forma, uma variável pode ser usada antes de ser declarada.

'''
	myName = 'Heisenberg';
	var myName;
	console.log(myName); // Heisenberg;
'''

O que é o mesmo que

'''
	var myName;
	myName = 'Heisenberg';
	console.log(myName); // Heisenberg
'''

## Closure
Closures são funções que são definidas dentro de outra função e com isso podem referenciar quaisquer variáveis no escopo da função na qual foram definidas.

'''
	var saveMyName = function (name) {
		var message = '!!!';

		function sayMyName() {
			alert(name + message);
		};

		sayMyName();
	};
'''

Um dos principais benefícios de usar closures é poder encapsular informações, conforme o exemplo abaixo:

'''
function account(money) {
	var myAccount = {};
	var myMoney   = money;

	function deposit(value) {
		myMoney += value;
		console.log('Thanks !');
	};

	myAccount.deposit = deposit;

	return myAccont;
};

var myAccount = account(300);
myAccount.deposit(100); //Thanks!
'''

No exemplo o desenvolvedor não consegue utilizar diretamente a variável myMoney, somente através dos métodos públicos.

## Variável Global
Quando uma variável é declarada fora de um função ela pode ser acessada e alterada dentro de qualquer função, o que significa que ela pertence ao escopo global do programa.

'''
	var myName = 'One Name';

	function say() {
		myName = 'Heisenberg';
		console.log(myName);
	};

	say(); //Heisenberg;
'''

Outra forma de criar uma variável global é quando inicializamos uma variável dentro de uma função sem a sua declaração (sem o 'var').

'''
	function say() {
		myName = 'Barry Allen';
	};

	myName = 'Heisenberg';

	say(); //Heisenberg
'''

## Variável por parâmetro
Ao passar um parâmetro para um função, o mesmo passa a ser uma variável local no escopo da função. Até mesmo quando passamos uma variável global como parâmetro o seu conteúdo é copiado para uma variável de escopo local.

'''
var age = 10;

show = function (age) {
	age = 20;

	console.log(age);
};

show(); //20

console.log(age);//10
'''

## Instanciação usando uma IIFE (Immediately Invoked Function Expression)
IIFE (Immediately Invoked Function Expression) são funções que são executadas no momento em que são definidas, dessa forma restringimos o escopo das variáveis apenas à aquela função.

'''
(function () {
	var myName = 'Heisenberg';
	console.log(myName); //Heisenberg
})();

console.log(myName); //Uncaught ReferenceError: myName is not defined
'''

No exemplo acima não é possível acessar a variável 'myName' fora da função IIFE pois 'myName' pertence apenas ao escopo da IIFE.
