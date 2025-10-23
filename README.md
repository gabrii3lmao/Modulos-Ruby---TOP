# 💎 Ruby Fundamentals — Study Notes  

> Anotações pessoais baseadas no curso **The Odin Project: Basic Ruby**, com exemplos práticos e linguagem acessível.  
> Foco: aprendizado ativo, clareza e consultas rápidas (sem precisar decorar métodos).

---

## 📚 Módulos Concluídos  

### 🧩 Módulo 1: Tipos de Dados  
- Conversão entre tipos numéricos (`.to_f`, `.to_i`)  
- Métodos úteis para números (`even?`, `odd?`, `round`, `ceil`, `floor`)  
- Manipulação de strings (concatenação, substrings, `strip`, `split`, `capitalize`, `reverse`)  
- Interpolação de strings (`"Olá #{nome}"` vs `'Olá #{nome}'`)  
- Diferença entre aspas simples e duplas  
- Symbols vs Strings (imutabilidade, performance e uso como chaves de Hashes)  

---

### 💡 Módulo 2: Variáveis  
- Declaração e nomenclatura (`snake_case`)  
- Variáveis como referências na memória  
- Mutação vs reatribuição  
- Boas práticas de nomenclatura  
- Conceito de objetos imutáveis e mutáveis  

---

### 🖥️ Módulo 3: Input e Output  
- Comandos de output (`print`, `puts`, `p`)  
- Diferenças entre `puts` e `print`  
- Captura de input com `gets.chomp`  
- Conversão de tipos em inputs (`Float(gets.chomp)`, `to_i`, etc.)

---

### ⚙️ Módulo 4: Lógica Condicional  
- Estruturas `if`, `elsif`, `else`, `unless`  
- Valores *truthy* e *falsy* em Ruby  
- Operadores de comparação (`>`, `<`, `==`, `!=`, `eql?`, `equal?`)  
- Operadores lógicos (`&&`, `||`, `!`)  
- Expressão `case` e cláusula `else`  
- Operador ternário (`condição ? se_true : se_false`)  

---

### 🔁 Módulo 5: Loops e Iterators  
- Loops: `loop`, `while`, `until`, `for`  
- Iterators: `each`, `each_with_index`, `times`, `upto`, `downto`, `step`  
- Ranges inclusivos (`1..5`) e exclusivos (`1...5`)  
- Preferência por iterators sobre loops tradicionais  
- Interrupção de loops com `break` e `next`  

---

### 🧮 Módulo 6: Arrays  
- Criação de arrays (literais e `Array.new`)  
- Acesso a elementos por índice  
- Métodos de adição/remoção (`push`, `pop`, `shift`, `unshift`)  
- Operações entre arrays (`+`, `-`, `concat`)  
- Métodos úteis (`empty?`, `reverse`, `include?`, `join`, `uniq`, `sample`, `shuffle`, `index`, `select`, `map`)  

---

### 🗂️ Módulo 7: Hashes  
- Criação e acesso a pares chave-valor  
- Symbols como chaves (sintaxe moderna: `{ nome: "Gabriel" }`)  
- Métodos específicos (`keys`, `values`, `fetch`)  
- Fusão de hashes com `merge`  
- Adição, modificação e remoção de elementos (`[]=`, `delete`)  
- Uso de `Hash.new` e valores padrão  

---

### 🧱 Módulo 8: Métodos  
- Criação de métodos com `def ... end`  
- Parâmetros e argumentos  
- Parâmetros padrão (`def ola(nome = "estranho")`)  
- Retorno implícito e uso do `return`  
- Métodos em cadeia (`"ruby".reverse.capitalize`)  
- Convenções de nomes (`!`, `?`, `=`)  

---

### 🔢 Módulo 9: Métodos Enumerable  
- Conceito de `Enumerable` e iteração elegante  
- Métodos principais:  
  - `each`, `each_with_index`  
  - `map` / `collect`  
  - `select` / `filter` / `reject`  
  - `reduce` / `inject`  
- Métodos “explosivos” (`map!`, `select!`) e mutação de dados  
- Diferença entre retorno e modificação do objeto original  

---

### ❓ Módulo 10: Métodos de Predicado  
- Métodos que retornam booleanos (`true`/`false`)  
- `include?`, `any?`, `all?`, `none?`, `one?`  
- Uso em Arrays e Hashes  
- Combinação com blocos condicionais  

---

### 🧩 Módulo 11: Nested Collections  
- Arrays e Hashes aninhados  
- Acesso com índices múltiplos (`arr[0][1]`, `hash[:user][:email]`)  
- Cuidados com `Array.new` e objetos mutáveis  
- Iteração com `each_with_index` duplo  
- Métodos úteis: `flatten`, `filter_map`, `compact`  
- Práticas seguras para lidar com dados complexos  

---

📘 **Referências**  
- [The Odin Project — Ruby Basics](https://www.theodinproject.com/paths/full-stack-ruby-on-rails/courses/ruby)  
- [Ruby Documentation (3.4+)](https://docs.ruby-lang.org/en/3.4/)  
- [RubyGuides](https://www.rubyguides.com/)  

---

> “Sempre escreva seu código como se o próximo a lê-lo fosse um psicopata violento que sabe onde você mora.”  
> — *Boas práticas em Ruby, versão definitiva.*
