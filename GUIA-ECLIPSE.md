# Guia do Eclipse · Do download ao primeiro teste

Use **Eclipse IDE for Java Developers**, **JDK 17 ou superior** e **Google Chrome**. Na primeira execução, o Maven e o Selenium podem precisar de internet para obter as dependências e o ChromeDriver.

## 1. Importar o projeto

1. Baixe o ZIP da etapa pelo [README](README.md). No Windows, clique com o botão direito no arquivo e escolha **Extrair Tudo**.
2. No Eclipse, vá em **File → Import → Maven → Existing Maven Projects**.
3. Em **Root Directory**, selecione a pasta que contém o `pom.xml`. Marque o projeto na lista e clique em **Finish**.
4. Aguarde a importação das bibliotecas. As versões do Selenium e do JUnit já estão no `pom.xml`.

## 2. Ver a página no Chrome

A página está em `src/main/resources`. Na etapa de login, abra `login.html`. Na etapa de operações, abra `banco.html`. Você pode abrir o arquivo direto no Chrome, a partir da pasta extraída.

## 3. Rodar o exemplo pronto

Em **src/test/java → aula.bancox**, clique com o botão direito na classe correspondente e escolha **Run As → JUnit Test**.

| Etapa | Classe | Resultado inicial |
| --- | --- | --- |
| Login | `LoginTest.java` | 1 passou, 3 ignorados |
| Operações | `OperacoesBancoTest.java` | 1 passou, 2 ignorados |

O Chrome abre, executa as ações e fecha. Confira o resultado na aba **JUnit**. Se uma verificação falhar, clique no método e veja o texto na área **Failure Trace**.

## 4. Rodar o exercício que você completou

Escreva o código no método indicado. Retire a anotação `@Disabled(...)` desse método e a linha `fail(...)`. Mantenha o `@Test`, salve e rode a classe novamente. Use [Dicas de sintaxe](docs/dicas-de-sintaxe.md) para consultar os comandos.

## Se aparecer um erro

| Sintoma | O que conferir |
| --- | --- |
| O Eclipse não mostra o projeto na importação | Selecione a pasta que contém o `pom.xml`, dentro da pasta extraída. |
| As bibliotecas do Selenium ou do JUnit não são reconhecidas | Confira a internet. No projeto, use **Maven → Update Project…**. |
| O Java 17 não aparece ou o compilador reclama da versão | Confira o JDK em **Window → Preferences → Java → Installed JREs**. |
| O teste aparece como ignorado | Veja se o método ainda tem `@Disabled`. |
| A barra do JUnit está vermelha | Abra **Failure Trace** e compare o resultado esperado com o obtido. |
