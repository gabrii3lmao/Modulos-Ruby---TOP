Em Ruby, existem diversas formas de escrever loops. Aqui estão alguns métodos para criar um loop em Ruby: 
####  Loop `loop`
o loop `loop`  é um método que irá se repetir infinitamente. Logo, você precisa de um `break`, com alguma condição, para o código parar. Exemplo:
``` ruby
i = 0
loop do
  puts("i é #{i}"))
  i += 1
  break if i == 10
end
```
Entretanto, o loop `loop`, felizmente, não é muito usado em Ruby, já que existem métodos melhores, como falarei a seguir.

#### Loop `while` 
O loop `while`é semelhante ao loop `loop`, com a diferença que você coloca a condição que vai parar o loop na própria declaração:
``` ruby
i = 0
while i < 10 do
puts("i é #{i}")	
i += 1
end
```
Esse é um exemplo do loop while com um count. Você também pode usar o loop while até que algum outro tipo de condição seja atendida:
``` ruby
while gets.chomp != "sim" do
	 puts("nós já chegamos?")
end
```

#### Loop `until`
O loop `until` é exatamente o oposto do loop `while`. O loop `while` se repete enquanto o retorno da condição for `false`, porém ele para quando a condição retornar `true`. Já o loop `until` se repete enquanto a condição é verdadeira, e para quando ela se tornar falsa.
``` ruby
i = 0
until i >= 10 do
  puts("O valor de i é #{i}")
  i += 1
end
```
Você pode ver que o loop `until`vai continuar até o `i`for igual ou maior a 10.
``` ruby
until gets.chomp == "sim" do
  puts "você gosta de pizza?"
end
```
Da pra ver que o código fica de melhor compreensão, já que não precisamos do operador `!` que precisaríamos em um loop `while`.

#### Loop `range` 
E se nós soubéssemos quantas vezes nós precisaríamos repetir o nosso código? O operador `range`nos ajuda com isso, precisando apenas de um simples intervalo.
``` ruby
(1..5)      # intervalo inclusivo: 1, 2, 3, 4, 5 (i <= 5)
(1...5)     # intervalo exclusivo: 1, 2, 3, 4 (i < 5)

# Podemos fazer com um intervalo de letras também!
('a'..'d')  # a, b, c, d
```

#### Loop `for`
Um loop `for` é usado para iterar através de uma coleção de informações, como um array ou intervalo. Esses loops são úteis se você precisar fazer algo um determinado número de vezes, ao mesmo tempo em que usa um iterador.
``` ruby
for i in 0..5
  puts("Eu vejo com meus olhinhos #{i} zumbis!")
end
```

#### Loop `upto`e `downto`
Você pode usar esses métodos para iterar de um número inicial para cima ou para baixo de outro número, respectivamente.
``` ruby
5.upto(10) { |num| print "#{num} " }     #=> 5 6 7 8 9 10

10.downto(5) { |num| print "#{num} " }   #=> 10 9 8 7 6 5
```
### Interators
Em Ruby, iterators são métodos que permitem percorrer coleções de forma elegante e idiomática. Diferente de loops tradicionais, eles encapsulam a lógica de iteração e são a forma **preferida** na linguagem.
##### `each` - O Iterator Fundamental
O `each` é o iterator mais comum em Ruby. Ele executa o bloco para cada elemento da coleção.
``` ruby
# Array
[1, 2, 3].each do |numero|
  puts "Número: #{numero}"
end
#=> Número: 1
#=> Número: 2  
#=> Número: 3

# Range
(1..3).each do |i|
  puts "Contagem: #{i}"
end
```

#### `each_with_index` - Com Posição
Quando você precisa do índice junto com o elemento:

```ruby
frutas = ["maçã", "banana", "laranja"]

frutas.each_with_index do |fruta, indice|
  puts "#{indice + 1}. #{fruta}"
end
#=> 1. maçã
#=> 2. banana
#=> 3. laranja
```
#### `times` - Para Repetições Simples
Ideal quando você sabe quantas vezes quer repetir:

```ruby
5.times do |i|
  puts "Iteração número #{i + 1}"
end
# Nota: i começa em 0!

3.times { puts "Ruby é legal!" }
#=> Ruby é legal!
#=> Ruby é legal!  
#=> Ruby é legal!
```
#### `step` - Com Incremento Personalizado
Para intervalos com passos específicos:

``` ruby
# De 0 a 10, pulando de 2 em 2
0.step(10, 2) do |num|
  puts "Número par: #{num}"
end
#=> Número par: 0
#=> Número par: 2
#=> Número par: 4
# ... até 10
```

Ir para o [[Ruby Módulo 6. Arrays]]
