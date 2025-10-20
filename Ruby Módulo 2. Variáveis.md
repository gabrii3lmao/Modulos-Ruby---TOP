Para declarar uma variável em Ruby, basta atribuir um nome a um valor, como no exemplo a seguir:
``` ruby
minha_variável = "Hello"
```
#### Nomeando variáveis em Ruby
Sempre que for nomear uma variável em Ruby, lembre-se do seguinte trecho: 
> *"Sempre escreva o seu código como se a próxima pessoa que for lê-lo fosse um psicopata violento que sabe onde você mora."*

Ex: 
``` ruby
#Prática ruim
a = 15
abacaxi = "mamão"

#boa prática
idade = 19
nome = "gabriel"
pode_nadar = false
```
Como você pode perceber, é um padrão utilizar o `snake_case` (como no python) quando tiver uma variável com dois nomes.

#### Variáveis são referências
O valor que você armazena em uma variável é mantido na memória do computador. Assim, uma variável é uma **referência** a um objeto nessa memória — e não o objeto em si.
Por exemplo, digamos que temos esse código: 
IRB
``` ruby 
1| a = "hi there" #=> "hi there"
2| b = a #=> "hi there"
3| a = "not here" #=> "not here"
4| b #=> "hi there"
```
Por que `b` não mudou após `a` ser reatribuída?  
Isso acontece porque variáveis em Ruby armazenam **referências a objetos**, e não a outras variáveis.  
Quando `a` recebe um novo valor, ela passa a apontar para outro objeto, mas `b` ainda referencia o antigo.”
![exemplo 1](https://github.com/gabrii3lmao/Modulos-Ruby---TOP/blob/main/imagens/variables_as_pointers_1.1.png?raw=true)

Esse ‘pulo’ de endereço só acontece quando reatribuímos uma variável com o operador `=`.  
Se, em vez disso, modificarmos o objeto que ela referencia, algo interessante acontece:
``` ruby
1|a = "hi there" #=> "hi there"
2|b = a #=> "hi there"
3|a << ", bob" #=> "hi there, bob"
4|b #=> "hi there, bob"
``` 
![exemplo 2](https://github.com/gabrii3lmao/Modulos-Ruby---TOP/blob/main/imagens/variables_as_pointers_1.2.png?raw=true)

É importante entender que alguns operadores modificam o objeto original (mutação), enquanto outros criam um novo objeto e fazem a variável apontar para ele.

Ir para o [[Ruby Módulo 3. Input e Output]]
