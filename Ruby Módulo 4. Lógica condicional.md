#### IF e ELSE
Em ruby, poderemos controlar o fluxo do nosso código usando `if`, `else` e `elsif`  como no exemplo a seguir: 
``` ruby
idade = 17
if idade >= 18
  puts "Você pode entrar na balada."
else
  puts "Fica pro próximo fim de semana."
end

```
Perceba que em Ruby, não precisa usar chaves nem colchetes na formatação dos ifs.
#### Truthy e falsy em Ruby
Os únicos valores falsos em Ruby são os valores `nil`e `false`. De resto, tudo é considerado true. Vale mencionar que os valores `0`e `""` não são considerados falsos em Ruby.

| False   | True              |
| ------- | ----------------- |
| `nil`   | `string qualquer` |
| `false` | `true`            |
#### Declaração condicional básica
A sintaxe geral de uma declaração `if` é mostrado aqui:
``` ruby
if expressao_a_ser_avaliada == true
  # faça alguma coisa
end

if 1 < 2
  puts "1 é menor que 2!"
end
#=> pqp, 1 é menor que 2!
```

Também dá para escrever essas declarações em apenas uma linha de código! Isso é a coisa mais rubística que existe.
``` ruby
puts("1 é menor que 2!") if 1 < 2
```
Também temos operadores como `else` e `elsif`, mas elas são praticamente a mesma coisa que nas outras linguagens.
### Lógica booleana
Para saber se uma expressão retornará True ou False, poderemos utilizar operadores lógicos, como `>`, `<`, `==`, `!=`, `>=`, `<=` e também temos os operadores `.eql?()`. e `.equal?()`.
Exs:
IRB
``` ruby
 1|5 == 5 #=> true
 2|5 == 6 #=> false
 3|5 != 7 #=> true
 4|5 != 5 #=> false
 5|7 > 5 #=> true
 6|5 > 7 #=> false
 7|5 < 7 #=> true
 8|7 < 5 #=> false
 9|5.eql?(5.0) #=> false; mesmos valores, porém com tipos 
10|#diferentes 
11|5.eql?(5)   #=> true
```

O Ruby também tem o operador `<=>` chamado "spaceship", esse operador retorna o seguinte: 
- `-1` se o valor da esquerda é menor que o da direita
- `0` se o valor da esquerda é igual ao valor da direita
- `1` se o valor da esquerda é maior que o valor da direita.
IRB
``` ruby
1| 5 <=> 10    #=> -1
2| 10 <=> 10   #=> 0
3| 10 <=> 5    #=> 1
```

### Operadores Lógicos
O Ruby também apresenta operadores lógicos, como o `&&`  (and), `||` (or), `!` (not).
Esses operadores fazem exatamente a mesma coisa que em qualquer outra linguagem: 
- `&&` retorna `true` se a expressão na esquerda e na direita retornarem `true`
``` ruby
if 1 < 2 && 5 < 6
  puts ("Hoje tem festa!")
end

# Isso também pode ser escrito na forma literal
if 1 < 2 and 5 < 6
  puts ("Hoje tem festa!")
end
```
- `||` retorna `true`se pelo menos uma das expressões retornarem `true`
``` ruby
if 5 > 3 || 3 > 5 
  puts "Hoje tem festa!"
  
# Isso também pode ser escrito na forma literal
if 1 < 2 or 2 > 3
  puts("Hoje tem festa!")

```
- `!` inverte o valor da expressão. Logo, se ela for `true` ela se torna `false`. 
``` ruby
if !false #=> true

if !(5 > 3) #=> false
```

### Expressão Case
A expressão `Case` processa cada condição por sua vez e, se a condição retornar `false`, ele vai passar para o próximo até que um match seja encontrado. Uma cláusula `else` pode ser fornecida para servir como padrão se nenhuma correspondência for encontrada.
``` ruby
nota = 0

eu_passei = case nota
  when 10 then "Bom demais"
  when 7 then "Tá na média"
  else "'tá fudido meu parceiro' - capitão nascimento"
end 
```
Quando um match é encontrado, o valor desse match é retornado e a expressão case é interrompida.

Você também pode retirar a palavra `then` e colocar a sua expressão na próxima linha, caso ela seja mais complexa:
``` ruby
nota = 0

case nota
when 10
  puts "você é um gênio!"
  conta_do_banco_no_futuro = 5_000_000
when 7
  puts "mais sorte na próxima"
  se_aposentar_cedo = false
else
  puts "'tá fudido meu parceiro' - capitão nascimento"
  virar_saudade = true
end
```

### Expressão `unless`
A expressão `unless`é exatamente o oposto da expressão `if`.
Ela só vai executar o bloco de código caso ele retorne `false`.
Ex:
``` ruby
idade = 19
unless idade < 18
  puts("Arrume um emprego")
end
#=> arrume um emprego
```

### Operador ternário
O operador ternário simula um `if...else`, mas em só uma linha, deixando o código mais conciso. 
A sintaxe é: `condição ? <execute se true> : <execute se false>`. Você também pode associar o valor de retorno à uma variável.
``` ruby
idade = 19
resposta = idade < 18 ? "Você tem a vida inteira pela frente" : "Vá arrumar um emprego!"
puts(resposta)
#=> Vá arrumar um emprego!
```

Ir para o [[Ruby Módulo 5. Loops]]