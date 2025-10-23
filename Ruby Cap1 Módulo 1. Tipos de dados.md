### Convertendo tipos de números

Para converter algum tipo numérico para outro, você pode usar essas propriedades que já vem na própria linguagem:
``` ruby

# converter de um inteiro para float: .to_f
13.to_f   #=> 13.0

# converter de um float para inteiro: .to_i
13.0.to_i #=> 13
13.9.to_i #=> 13  
# perceba que o ruby apenas tira a casa após a virgula, sem arredondar — apenas truncando o valor após a vírgula
```
Alguns métodos de números interessantes em Ruby: 
``` ruby
6.even? # => true
6.odd? # => false
# esses métodos retornam um booleano dependendo se o número é par ou é ímpar
```

### Strings
#### Concatenar entre variáveis: 
```ruby

"Bem vindo " + "Ao " + "Ruby! " # => "Bem vindo ao ruby!"
#(Ruby não corrige sua gramática, infelizmente.)

#Com o operador de append (omg c++ hiii!!!!): 
"Bem vindo " << "Ao " << "Ruby! " # => "Bem vindo ao ruby!"

#com o método .concat: 
"Bem vindo ".concat("Ao").concat("Ruby!") # => "Bem vindo ao ruby!"
```

#### Substrings: 
``` ruby
"hello"[0]      #=> "h"

"hello"[0..1]   #=> "he"

"hello"[0, 4]   #=> "hell"

"hello"[-1]     #=> "o"
```

#### Métodos comuns de strings: 

``` ruby
#capitalize
"hello".capitalize #=> "Hello"

#include? 
"hello".include?("lo")  #=> true

"hello".include?("z")   #=> false

#upcase 
"hello".upcase  #=> "HELLO"

#downcase
"Hello".downcase  #=> "hello"

#empty? 
"hello".empty?  #=> false

"".empty?       #=> true

#reverse 
"hello".reverse #=> "olleh"

#split Nota: 'split' funciona normalmente em qualquer contexto, mas se você usar 'puts' para imprimir o resultado (que é um Array), a formatação pode ficar confusa. Prefira `p` ou `print` se quiser ver a estrutura completa.
"hello world!".split() #=> ["hello", "world!"]
"hello".split("") #=> ["h", "e", "l", "l", "o"]

#strip
" hello, world   ".strip  #=> "hello, world"

```
#### [[Symbols]]
Strings são mutáveis. Cada vez que uma string é usada, o Ruby cria uma nova cópia na memória, mesmo que já exista outra igual.
Symbols, por outro lado, são armazenados na memória apenas uma vez, tornando-os mais rápidos em determinadas situações.

Para criar um Symbol, basta usar: 
```ruby 
:my_symbol
```

Ir para o [[Ruby Cap1 Módulo 2. Variáveis]]