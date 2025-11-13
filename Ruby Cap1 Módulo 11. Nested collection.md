Como você bem sabe, arrays e hashes são uma maneira útil e eficiente de guardar dados. Porém, às vezes as informações são mais complexas e precisam de mais estrutura para serem guardadas, do que usando arrays e hashes básicos. 

Você aprenderá a usar arrays e hashes aninhados para guardar alguns tipos específicos de informações.

### Arrays aninhados (nested arrays)
Arrays podem ter qualquer tipo de dado, inclusive outros arrays ou hashes. Um array que contem outro array é chamado de array aninhado, ou um array multidimensional.

Arrays aninhados podem ser úteis para armazenar uma grande quantidade de dados parecidos. Como notas, posições, nomes, etc.
``` ruby
pontuacao_testes = [
[7, 5, 4, 8],
[10, 9, 10, 10],
[9, 6, 7, 9],
[7, 7, 7, 7]
]

correios_professor = [
["jose", "lucas", "benicio", "joao"],
["carlos", "alicia", "andre", "lucas"],
["gabriel", "matheus", "ronaldo", "pedro"],
["michele", "joana", "cicero", "ciro"]
]
```

### Acessando elementos
Para acessar um elemento específico em um array aninhado, você utiliza a sintaxe `array[posição_principal][posição_secundária]`, onde:

- `posição_principal` seleciona qual dos arrays internos você deseja acessar
- `posição_secundária` seleciona qual elemento dentro desse array interno específico

Pense em um sistema de coordenadas, onde a `posição_principal` é o X, e `posição_secundária` o Y (X, Y).
``` ruby
bandas = [
["casiopea", "Jazz", 1976],
["Zé ramalho", "MPB", 1978],
["Slipknot", "Metal", 1995]
]
bandas[0][2]
#=> 1976
```

Se você tentar acessar o índice de um elemento aninhado inexistente, o console jogará na sua cara `NoMethodError`, porque 
a classe `nil` não tem um método `[]`.
Porém, se você tentar acessar o índice de um elemento dentro de um array aninhado, o console simplesmente retornará `nil`, igual a um array normal.

### Problema do Array.new com Objetos Mutáveis

Ao criar arrays aninhados usando `Array.new(tamanho, valor_padrao)`, ocorre um comportamento inesperado quando o valor padrão é um objeto mutável (array, hash, string).

**O Problema:**
```ruby
# Jeito errado - compartilha referências
arrays_ruins = Array.new(3, Array.new(2))
arrays_ruins[0][0] = 1000

# Resultado: [[1000, nil], [1000, nil], [1000, nil]]
# Todos os arrays internos foram modificados
```

**A Solução:**
```ruby
# Jeito correto - cria objetos independentes  
arrays_bons = Array.new(3) { Array.new(2) }
arrays_bons[0][0] = 1000

# Resultado: [[1000, nil], [nil, nil], [nil, nil]]
# Apenas o primeiro array foi modificado
```
**Explicação:**

- `Array.new(3, valor)` cria 3 referências para o MESMO objeto
- `Array.new(3) { valor }` executa o bloco 3 vezes, criando 3 objetos DIFERENTES

**Regra Prática:**  
Use a sintaxe com bloco `{ }` quando o valor padrão for mutável (arrays, hashes, strings). Use o segundo argumento apenas para valores imutáveis (números, booleanos, symbols).

### Adicionando e removendo elementos
Você pode adicionar ou remover elementos ao final de um array aninhado usando o método `#push` ou o operador shovel `<<`. 

Se você quiser adicionar um elemento em um array aninhado específico, terá de falar o seu index após o index do elemento aninhado.
``` ruby
pontuacao_testes << [5, 6, 7, 8]
#=> [7, 5, 4, 8], [10, 9, 10, 10],[9, 6, 7, 9], [7, 7, 7, 7], [5, 6, 7, 8]  

correios_professor[2][5].push("Felipe")
#=> ["gabriel", "matheus", "ronaldo", "pedro", "Felipe"]
```

### Iterando sobre um array aninhado
Para iterar sobre uma array aninhado, preferencialmente usamos o método `#each_with_index`. Pode ser útil pensar em um array aninhado como tendo linhas e colunas, onde cada linha é o elemento alinhado, e cada coluna é o índice do elemento aninhado
``` ruby
correios_professor.each_with_index {|linha, index_linha| 
  puts "linha:#{index_linha} = #{linha}" }
  #=> linha:0 = ["jose", "lucas", "benicio", "joao"]
  #=> linha:1 = ["carlos", "alicia", "andre", "lucas"]
  #=> linha:2 = ["gabriel", "matheus", "ronaldo", "pedro"]
  #=> linha:3 = ["michele", "joana", "cicero", "ciro"]
```

Para iterar sobre o elemento individual de cada linha, você vai precisar aninhar outro método enumerable dentro.
``` ruby
correios_professor.each_with_index do |linha, index_linha| 
  linha.each_with_index do |professor, index_coluna| 
  puts "Linha:#{index_linha} coluna:#{index_coluna} = #{professor}"
  end
end
```

Embora esses códigos sejam gigantes, podemos usar o método `#flatten` para conseguir apenas os nomes dos professores, neste exemplo:
``` ruby
correios_professor.flatten.each do |professor|
 puts "O professor #{professor} é incrível!"
end
```

Agora vamos usar uma lógica mas difícil. Vamos verificar se existe algum aluno que tenha todas as notas acima de 8. Para isso, usaremos o `pontuacao_testes`, mais acima da página.
``` ruby
pontaçao_teste.any? do |notas|
  notas.all?{|nota| nota > 8}
end
#=> true
```

### Hashes aninhadas 
Assim como nos arrays, também podemos ter hashes aninhadas para guardar dados mais complicados.
``` ruby
carros = {
alice: {ano: 2019, fabricante: "Toyota", modelo: "Corolla"},
blake: {ano: 2020, fabricante: "Volkswagen", modelo: "beetle"},
caleb: {ano: 2020, fabricante: "Honda", modelo: "Accord"}
}
```

### Acessando dados
Acessar dados em um hash aninhado é bem semelhante a acessar em um array. Basta usarmos aquela velha sintaxe: `hash[:x][:y]`, onde `[:x]` é a chave do hash, e `[:y]` é a chave do hash aninhado.
``` ruby
carros[:alice][:ano]
#=> 2019
carros[:blake][:fabricante]
#=> "Volkswagen"
carros[:blake][:modelo]
#=> "Accord"
```

### Adicionando e removendo dados
Você pode adicionar mais hashes aninhados fazendo igual quando adiciona a um hash normal.
Vamos ver o carro novo de Jader:
``` ruby
carros[:jader] = {ano: 2024, fabricante: "Renault", modelo: "Kwid"}
#=> alice: {ano: 2019, fabricante: "Toyota", modelo: "Corolla"}, blake: {ano: 2020, fabricante: "Volkswagen", modelo: "beetle"}, caleb: {ano: 2020, fabricante: "Honda", modelo: "Accord"}, jader: {{ano: 2024, fabricante: "Renault", modelo: "Kwid"}
```

Vamos dizer que Jader realmente gostou do seu kwid, que agora até queira dizer a sua cor para os seus amigos:
```ruby
carros[:jader][:cor] = "vermelho"
#=> alice: {ano: 2019, fabricante: "Toyota", modelo: "Corolla"}, blake: {ano: 2020, fabricante: "Volkswagen", modelo: "beetle"}, caleb: {ano: 2020, fabricante: "Honda", modelo: "Accord"}, jader: {{ano: 2024, fabricante: "Renault", modelo: "Kwid", cor: "vermelho"}
```

Para retirar um hash aninhado completo vai ser igual a um hash normal: usando `#delete`. Basta especificar qual hash você quer tirar.
Vamos dizer que Alice decidiu vender o seu carro:
``` ruby
carros.delete(:alice)
#=> blake: {ano: 2020, fabricante: "Volkswagen", modelo: "beetle"}, caleb: {ano: 2020, fabricante: "Honda", modelo: "Accord"}, jader: {{ano: 2024, fabricante: "Renault", modelo: "Kwid", cor: "vermelho"}
```

Para retirar uma chave ou um valor específico, usamos o método `#delete`, mas antes você deve especificar a chave do hash.
Vamos dizer que Jader agora sente vergonha do seu carro. Tanta vergonha que ele quer até esconder o modelo:
``` ruby
carros[:jader].delete(:modelo)
#=> blake: {ano: 2020, fabricante: "Volkswagen", modelo: "beetle"}, caleb: {ano: 2020, fabricante: "Honda", modelo: "Accord"}, jader: {{ano: 2024, fabricante: "Renault", cor: "vermelho"}
```

Ele não aguentou tanta antena para o alto!
### Métodos
Existem diversos métodos que vão te ajudar com hashes aninhados, desde que você saiba que tipo de informação você está procurando. 

Vamos dizer que queremos encontrar quem tem veículos mais novos que são de 2020 pra cima:
``` ruby
carros.select{|nome, data| data[:ano]}
#=> {blake: {ano: 2020, fabricante: "Volkswagen", modelo: "beetle"}, caleb: {ano: 2020, fabricante: "Honda", modelo: "Accord"}}
```

E se quiséssemos apenas os nomes das pessoas? o método `#collect` pode nos ajudar com isso:
``` ruby
carros.collect{|nome, data| nome if data[:ano] >= 2020}
#=> [nil, :caleb, :blake]
```

O método `#collect` funciona quase igual ao método `#map`, ele vai iterar sobre todos os valores. Logo, se tiver um valor que não condiz com a condição, ele retorna `nil`. 
Por sorte, temos um outro método que retorna um array sem os valores `nil`, o método `#compact`.
``` ruby
carros.collect{|nome, data| nome if data[:ano] >= 2020}.compact
#=> [:caleb, :blake]
```

Bom, se quisermos deixar esse código ainda mais rubístico, poderíamos usar o método `#filter_map`, que substitui esses dois métodos:
``` ruby
carros.filter_map {|nome, data| nome if data[:ano] >= 2020}
#=> [:caleb, :blake]
```

Você finalizou o primeiro capítulo de Ruby! Parabéns!
Vá para [[Ruby Cap2 Módulo 0.5 POO - conceitos]] para continuar para o próximo capítulo.