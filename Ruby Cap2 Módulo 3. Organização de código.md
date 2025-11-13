Neste módulo iremos ver algumas estratégias que os profissionais usam para fazer um código bonito, entendível, reutilizável, e principalmente, eficiente.

### Linters e Formatters

Algumas ferramentas muito importantes que você pode usar para seguir as boas práticas do Ruby, é usar os Linters e Formatters:
**Linters**
- São ferramentas que analisam seu código e apontam problemas de estilo, sintaxe e boas práticas.
- Eles não mudam o código - apenas te dizem "Olha, isso aqui tá meio feio, hein?" ou "isso aqui não tá rubístico"
- O mais famoso no mundo Ruby é o RuboCop.
	- Ele verifica centenas de regras: nomes de variáveis, espaçamento, indentação, complexidade de métodos, etc.
	-  Também pode te ajudar a manter o estilo consistente com a comunidade.

Instalação:
``` bash
gem install rubocop
```
Rodando:
``` bash
rubocop
```
Ele analisa todo o projeto e te mostra avisos, erros e sugestões.

**Formatters**
- Esses são os que arrumam seu código automaticamente - formatação, indentação, espaçamento, aspas, etc.
- Eles não se preocupam tanto com boas práticas, e sim com a aparência do código
- O mais comum em Ruby (e usado dentro do RuboCop) é o próprio RuboCop com auto-correct.

Ele vai sair limpando tudo - tubulações, espaços extras, linhas tortas. 
É