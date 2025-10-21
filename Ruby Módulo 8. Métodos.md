Métodos permitem você a reutilizar trechos do próprio código apenas chamando o seu nome, para que você não precise reescrever ele inteiro toda vez. Essa estratégia é comumente chamada de [[DRY - DONT REPEAT YOURSELF]].

Você deve estar se perguntando: "Mas isso não é basicamente uma função? por que o Ruby chama eles de métodos?". Bom, de acordo com o livro [The Ruby Programming Language](https://www.amazon.com/dp/0596516177/?tag=stackoverfl08-20):

> _"Muitas linguagens distinguem entre funções, que não têm um objeto associado, e métodos, que são invocados em um objeto receptor. Como Ruby é uma linguagem puramente orientada a objetos, todos os métodos são verdadeiros métodos e estão associados a pelo menos um objeto."_

Basicamente, como tudo em Ruby é objetos, nós não temos funções. Temos métodos.

### Métodos Built-in do Ruby
Métodos geralmente são chamados a partir da sintaxe: `.nome_metodo` depois da instância de um objeto que tenha esse método.
```ruby
"metodo".reverse   #=> "odotem"
```
Neste caso, `#reverse` é um método built-in dos objetos [Strings](https://docs.ruby-lang.org/en/3.4/String.html).

Também temos alguns métodos globalmente acessíveis em Ruby, como `puts` e `print`. Esses métodos são chamados apenas com seus nomes e argumentos.
```ruby
puts "alguma coisa"  #=> alguma coisa
```

### Criando métodos
Você pode criar o seu próprio método em Ruby usando a seguinte sintaxe:
``` ruby
def meu_nome
"gabriel"
end

puts meu_nome     #=> "gabriel"
```
- `def` -> é uma palavra built-in que diz ao Ruby que esse é o começo de um método.
- `meu_nome` -> é o nome do meu método.
- `"gabriel"` -> é o código dentro da minha função.
- `end` -> é outra palavra built-in que avisa ao Ruby que o método chegou ao fim.
### Nomes de métodos
Em Ruby, temos algumas convenções para os nomes que devemos dar para nomear os nossos métodos.
- Você não pode nomear o seu método com alguma das palavras embutidas do Ruby (tipo `for`, `while` etc).
- Você não pode usar outros símbolos além de `_`, `?`, `!` e `=`.
- Os símbolos `?`, `!`, `=` devem ser usados apenas ao final dos métodos.
- Você não pode começar o nome de um método com um número.

### Parâmetros e argumentos
Se você quiser retornar algo além de um resultado fixo, você dar parâmetros para o seu método.
**Parâmetros** são variáveis que o seu método pode receber quando é chamado. 
``` ruby
def saudacao(nome)
"Olá " + nome + "!"
end

puts saudacao("joão") #=> Olá joão
```
Caso você tenha ficado em dúvida sobre a diferença entre argumento e parâmetro: 
- Parâmetro: é o placeholder do seu argumento, ou seja, ele está ali para especificar o que a sua função pode receber de argumento.
- Argumento: são os valores que a função realmente recebe. Por exemplo: `nome` é o parâmetro, e `"joão"` é o argumento dela.

### Parâmetros padrões
E se você não quiser sempre ter que dar um argumento para um parâmetro? É aí que os parâmetros padrões podem ser úteis.
```ruby
def saudacao(nome = "estranho")
"Olá " + nome + "!"
end

puts saudacao("joão") #=> "Olá joão"
puts saudacao         #=> Olá estranho
```
 Vale mencionar que Ruby é uma das únicas linguagens que não precisa de um `return` explícito ao fim de todo método.
Mas existem alguns casos que o `return` pode ser útil, como nesse trecho de código: 
``` ruby
def par_impar(num)
  unless num.is_a? Numeric
    return "Entre com um número válido"
  end

  if num % 2 == 0
    "é par."
  else
    "é ímpar."
  end
end

puts par_impar(20) #=>  é par.
puts par_impar("Ruby") #=>  é impar.
```

### Métodos em cadeia
Uma das vantagens do Ruby é que você pode usar métodos em sequência, um atrás do outro, em apenas uma linha.
``` ruby
frase = ["ser", "nao", "ou", "ser"]

puts frase.reverse.join(" ").capitalize
#=> "Ser ou nao ser"
```

Ir para o [[Ruby Módulo 9. Métodos Enumerable]]