# Estruturando seus Projetos em Ruby

Neste módulo, mostraremos como estruturar seus projetos em Ruby para mantê-los organizados, gerenciáveis e fáceis de navegar. Uma boa estrutura é fundamental à medida que seus projetos crescem em complexidade.

## Por que organizar?

Organizar seu projeto em múltiplos arquivos traz benefícios claros que superam em muito o esforço inicial.

- **Manutenibilidade:** É muito mais fácil corrigir ou alterar um comportamento quando o código responsável por ele está isolado em seu próprio arquivo.
- **Legibilidade:** Em vez de um arquivo com milhares de linhas, você terá arquivos menores e focados em uma única responsabilidade.
- **Modularidade:** Facilita o reuso de código e a compreensão de como as diferentes partes do sistema interagem.

> "_Um lugar para tudo e tudo no seu lugar_"

## Convenções Essenciais da Estrutura

Para projetos em Ruby, existem algumas convenções amplamente adotadas pela comunidade:

1. **Uma classe por arquivo:** Cada classe que você criar deve, idealmente, viver em seu próprio arquivo. O nome do arquivo geralmente segue o padrão `snake_case` do nome da classe (ex: classe `MyAwesomeClass` ficaria em `my_awesome_class.rb`).
2. **O diretório `lib`:** Por convenção, a maior parte do código-fonte do seu projeto (classes, módulos, etc.) deve residir dentro de um diretório chamado `lib`.

Uma estrutura de projeto típica se parece com isto:

```
nome_do_projeto/
├── lib/
│   └── minha_classe.rb
└── main.rb
```

- `lib/`: Contém a lógica principal da sua aplicação.
- `main.rb`: (ou `bin/meu_script`) É o "ponto de entrada", o arquivo que você executa para iniciar seu programa.
## Usando Múltiplos Arquivos: `require` vs. `require_relative`

Para que um arquivo possa usar classes ou métodos definidos em outro, ele precisa "carregá-lo". Em Ruby, fazemos isso principalmente com `require_relative` e `require`.

Vamos usar esta estrutura como exemplo:

```
projeto/
├── lib/
│   ├── sort/
│   │   ├── bogo_sort.rb
│   │   ├── bubble_sort.rb
│   │   └── merge_sort.rb
│   └── sort.rb
└── main.rb
```

### `require_relative` (A escolha para arquivos do projeto)

`require` é um pouco mais complexo e se comporta de duas maneiras principais:

1. **Caminhos Relativos/Absolutos:** Se o caminho começar com `./`, `../` ou `/`, ele tentará carregar o arquivo com base no **diretório de trabalho atual** (de onde você _executou_ o script) ou do caminho absoluto.
    - `require './lib/sort'` (funciona se você executar `ruby main.rb` da raiz, mas falha se executar de outro lugar).
2. **Nomes "Nus":** Se você passar um nome sem caminho (ex: `require 'json'`), o Ruby procurará esse arquivo em todos os diretórios listados na variável global `$LOAD_PATH`. É aqui que as bibliotecas padrão do Ruby e as gems instaladas residem.
    

**Convenção:**

- Use `require_relative` para carregar arquivos do **seu próprio projeto**.
- Use `require` para carregar **gems** ou bibliotecas padrão do Ruby (ex: `require 'net/http'`, `require 'pry'`).
### O que é carregado?

Quando você usa `require` ou `require_relative`, o código do arquivo é executado imediatamente (apenas na primeira vez que é carregado).

- **Definições** de classes, módulos e constantes se tornam disponíveis no escopo global.
- **Variáveis locais** definidas no escopo principal do arquivo _não_ são compartilhadas e deixam de existir assim que o arquivo termina de ser carregado.

Ir para [[Ruby Cap2 Módulo 3. Organização de código]]