# Dicas de sintaxe · Selenium e JUnit

## O que cada ferramenta faz

| Termo | Papel no Banco X |
| --- | --- |
| Maven | Lê o `pom.xml` e resolve as dependências do projeto. |
| `WebDriver` | Interface Java que declara operações para controlar o navegador. |
| `ChromeDriver` | Implementação que controla o Chrome. Em `TesteBanco.java`, `new ChromeDriver()` cria a sessão. |
| `By.id("usuario")` | Cria um localizador que procura o elemento com `id="usuario"` no HTML. |
| `WebElement` | Objeto que representa o elemento encontrado, como um campo ou botão. |
| JUnit | Executa os testes e informa se as verificações passaram. |

## Login do Arthur

O método `fazerLogin("Arthur", "Zane123")` chama o código de `TesteBanco.java` que preenche os dois campos e clica no botão. Por dentro, o preenchimento segue este padrão:

```java
WebElement campoUsuario = navegador.findElement(By.id("usuario"));
campoUsuario.sendKeys("Arthur");
```

`findElement` encontra o campo e devolve o objeto `WebElement`. `sendKeys` digita no campo representado por esse objeto. Pra declarar uma variável desse tipo, importe `org.openqa.selenium.WebElement`.

## Saque de exemplo

```java
navegador.findElement(By.id("valor-saque")).sendKeys("150");
navegador.findElement(By.id("sacar")).click();

String saldo = navegador.findElement(By.id("saldo")).getText();
assertEquals("R$ 350,00", saldo);
```

O Selenium digita e clica. `getText()` lê o saldo visível. O JUnit compara o primeiro argumento, que é o **esperado**, com o segundo, que é o **obtido**. Como o valor veio da tela, a comparação aqui é entre textos.

| Comando | Quando usar |
| --- | --- |
| `isDisplayed()` | Conferir se uma área está visível. Devolve um `boolean`. |
| `assertFalse(condicao)` | Confirmar que a condição é falsa. Importe `org.junit.jupiter.api.Assertions.assertFalse` com `import static`. |
| `Select` | Trabalhar com listas HTML do tipo `<select>`. Crie o objeto com o elemento da lista e use `selectByVisibleText(...)` para escolher uma opção. A classe fica em `org.openqa.selenium.support.ui.Select`. |

## Como o JUnit organiza a execução

- **`@BeforeEach`** executa a preparação antes de cada teste ativo. No Banco X, ele abre uma sessão nova. Na etapa de operações, a preparação também entra na conta.
- **`@Test`** marca o método que será executado como teste.
- **`@AfterEach`** executa a limpeza depois de cada teste ativo. `quit()` fecha a sessão do navegador.
- **`@Disabled(...)`** deixa um exercício ignorado. Ao completar o método, retire essa anotação e a chamada `fail(...)`, que força uma falha enquanto o código está incompleto.

Ao testar um login inválido, o resultado esperado é a recusa do acesso. O JUnit mostra verde quando o teste confirma essa recusa.
