### Comandos de Output
#### `Print`
Para fazer o output de alguma informação, podemos usar o comando `print`

Exemplo: 
**IRB**
``` ruby
1|print "Learning to code is FUN!"
2|#=> Learning to code is FUN!
3|
4|print "1234"
5|#=> 1234
```
#### `Puts`
Nós também podemos usar o comando `puts`:

**IRB**
``` ruby 
1|puts "Hello world!"
2|#=> hello world!
3|
4|x = "Meu nome é gabriel :)"
5|#=> Meu nome é gabriel :)
6|puts x
7|#=> Meu nome é gabriel :)
```

Para destacar a diferença entre `puts` e `print`, iremos usar o ponto e vírgula. O ponto e vírgula não é necessário em Ruby, mas ele nos permite escrever mais de um trecho de código em uma só linha.
#### Diferença entre `puts` e `print`
Puts e Print têm algumas diferenças bem discretas, mas que mudam o seu uso completamente. Ambas imprimem algo no console, porém, puts automaticamente adiciona uma quebra de linha: 
``` ruby
puts("Olá, mundo!")
puts("Hello, world!")
#=> Olá, mundo!
#=> Hello, world!
puts([3, 4, 5])
#=> 3
#=> 4
#=> 5
```

Enquanto Print não tem esse trabalho de adicionar uma quebra de linha:
``` ruby
print("Olá, mundo!")
print("Hello, world!")
#=>Olá, mundo!Hello, world!

print([1, 2, 3])
#=> [1, 2, 3]

```

### Comandos de Input
Podemos conseguir dados do usuário usando o comando `gets`.
O terminal não prosseguirá até a próxima linha até conseguir uma resposta do usuário. Exemplo: 
``` ruby
x = gets.chomp
puts(x) #=> *input do usuário*
```

É importante ressaltar que o `gets.chomp` automaticamente transforma o input em string, o que pode causar erros no código. Logo, é preciso formatar o código manualmente:
``` ruby
x = Float(gets.chomp) #=> para transformar em Float
puts(x) #=> x.0
```

Ir para o [[Ruby Módulo 4. Lógica condicional]]