# Resumo:

## Por que escrever testes?

- Facilita a identificação de bugs, facilita refatoração, aumenta confiança no sistema, tende a melhorar a qualidade do código;

---

## Testes Unitários

- **e2e** - Teste do sistema completo simulando o comportamento do usuário final, simulam ambiente real.
- **Integração** - Testam o funcionamento em conjunto de duas unidades do sistema 
- **Unitários** - Testam uma funcionalidade isolada do sistema, a menor unidade do código, não dependem de outros colaboradores externos, como conexão com banco de dados, etc.

---

## FIRST

- **F - Faster**
- **I - Independent** (Não deve depender do resultado de outro teste para sua realização)
- **R - Repeatable** (Devem ser previsíveis, produzir o mesmo resultado toda vez que rodar, uso  de injeção de dependência e simulações de ambientes para realizar o teste)
- **S - Self Validating** (Os testes devem detectar automaticamente se falharam ou passaram, sem interpretação externa.)
- **T - Timely/Thorough** (Realizar os testes antes ou junto com o desenvolvimento do programa. não depois/, além disso, devem cobrir casos diversos, não apenas o caso ideal)

Seguindo esses princípios os testes se tornam mais confiáveis e fáceis de manter/modificar.

---

## TDD (Test Driven Development)

Essa metodologia é baseada em escrever os testes antes de escrever os códigos do sistema em si, a ideia é escrever os testes baseado na regra de negócio do projeto.

O TDD é baseado em ciclos de 3 fases:

- **Red - Failing Test:** Escrever um teste que FALHE
- **Green - Passing Test:** Escrever um teste que passe com sucesso
- **Blue - Refactoring:** Refatorar o teste, melhorando estrutura e qualidade.

O TDD segue três leis principais:

- **1 Lei** - Não se deve escrever nenhum código de produção antes de ter um teste falhando.
- **2 Lei** - Você não pode escrever mais de um teste unitário para fazer seu teste falhar, ou seja, você deve escrever um código para cada funcionalidade específica por vez, e deve falhar.
- **3 Lei** - Você não deve escrever mais do que o necessário para fazer seu teste passar, seu teste deve dar success com o mínimo possível.

### Vantagens de seguir o TDD

- Diminui o tempo perdido com debugging, visto que ao desenvolver uma funcionalidade, já existirá o teste dela para verificar se está funcionando conforme o esperado ou não.
- Maior cobertura de testes para o sistema, visto que é mais difícil cobrir todo o necessário quando já se tem todo o código de produção feito, ao realizar os testes primeiro, já foi feita a cobertura de todas as funcionalidades, portanto basta desenvolvê-las.
- Maior confiabilidade, visto que ao realizar alguma alteração ou feature nova, o teste vai dizer se está funcionando corretamente ou não, diminuindo o medo de quebrar alguma coisa.
- Ajuda como forma de documentação, pois como os testes devem seguir a lógica de negócio, ajuda a entender o comportamento daquela parte do código.
- Desacoplamento, pois ao desenvolver pequenas peças do código por vez, e seguindo o princípio da Independência do FIRST, os códigos se tornam mais escaláveis pois diminui o acoplamento geral.

---

## Testes Double

Qualquer objeto que finge ser um objeto real para testar. Podem ser divididos em cinco categorias:

- **Mocks:** São criados mocks de dependências externas, ou seja, é simulado o comportamento das dependências externas que são necessárias para testar determinada funcionalidade. Não queremos ficar criando registros no banco de dados nem consumir tokens das APIs apenas para realizar testes.
- **Stubs:** Servem para testar se o resultado obtido ao testar a dependência externa mockada é igual ao resultado esperado, testar sucesso, falhas, etc.
- **Spy:** Executa o depois e depois verifica qual foi o comportamento realizado. A diferença dele pro mock é que o mock primeiro já define o que deve acontecer e já falha se essa exigência não for cumprida, o spy deixa tudo acontecer primeiro e depois verifica se o método foi chamado por exemplo.
- **Fakes:** Não utilizados em testes unitários, geralmente em testes de integração. Os fakes são usados para testar como a aplicação reage a grande quantidades de dados. Pode-se usar um servidor local para testar chamadas e grandes quantidades de dados.
- **Dummies:** São argumentos utilizados para preencher parâmetros obrigatórios de um método ou classe.

---

## AAA

É um padrão que todo teste deve seguir, Arrange, Act, Assert.

- **Arrange:** Preparar o teste, configuração de tudo que vai ser necessário para o teste rodar, variáveis, mocks;
- **Act:** Realização do teste
- **Assert:** Verificar se o teste obteve o comportamento esperado.
