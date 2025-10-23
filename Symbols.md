### 🧩 Symbol (Ruby)

**Resumo:**  
Um `Symbol` é um identificador **imutável e único**, usado principalmente como chave, rótulo ou marcador eficiente em memória. Ele é criado apenas uma vez e reutilizado pelo Ruby internamente, ao contrário das `Strings`.
#### 🧠 Diferença principal em relação a String
- `String`: mutável, recriada a cada uso.
- `Symbol`: imutável, o mesmo objeto sempre que usado.
``` ruby
:foo.object_id == :foo.object_id   # true  
"foo".object_id == "foo".object_id # false
```
---
#### ⚙️ Uso comum

- Como **chave em hashes**:
``` ruby
user = { name: "Gabriel", age: 22 }
# equivalente a
user = { :name => "Gabriel", :age => 22 }
```

- Como **identificadores internos** (métodos, variáveis, etc.)
---
#### 🧾 Referências

- [Ruby Docs – Symbol](https://ruby-doc.org/3.4.1/Symbol.html)
- [Ruby guides - Symbol](https://www.rubyguides.com/2018/02/ruby-symbols/)