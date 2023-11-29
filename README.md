# Cucumber-ContaBancaria

## Descrição
Desenvolvimento de um projeto Java centrado na implementação do Cucumber e JUnit, modelando uma conta bancária simples.

## Classes Projeto
```java 
import io.cucumber.java.en.Given;
import io.cucumber.java.en.Then;
import io.cucumber.java.en.When;

/**
 * Classe que representa uma conta para testes de saque.
 */
public class Conta {
    private int saldo;          // Saldo atual da conta
    private int saldoEsperado;  // Saldo esperado após uma operação

    /**
     * Configura o saldo inicial para um cliente especial.
     *
     * @param saldoInicial O saldo inicial da conta do cliente especial.
     */
    @Given("Um cliente especial com saldo atual de {int} reais")
    public void um_cliente_especial_com_saldo_atual_de_reais(int saldoInicial) {
        this.saldo = saldoInicial;
    }

    /**
     * Realiza a operação de saque para um cliente especial.
     *
     * @param valorSaque O valor a ser sacado da conta.
     */
    @When("for solicitado um saque no valor de {int} reais")
    public void for_solicitado_um_saque_no_valor_de_reais(int valorSaque) {
        this.saldoEsperado = this.saldo - valorSaque;
    }

    /**
     * Verifica se o saque foi efetuado com sucesso e atualiza o saldo da conta.
     *
     * @param saldoAtualizado O saldo atualizado da conta após o saque.
     */
    @Then("deve efetuar o saque e atualizar o saldo da conta para {int} reais")
    public void deve_efetuar_o_saque_e_atualizar_o_saldo_da_conta_para_reais(int saldoAtualizado) {
        assertSaldoEquals(saldoAtualizado);
    }

    /**
     * Configura o saldo inicial para um cliente comum.
     *
     * @param saldoInicial O saldo inicial da conta do cliente comum.
     */
    @Given("Um cliente comum com saldo atual de {int} reais")
    public void um_cliente_comum_com_saldo_atual_de_reais(int saldoInicial) {
        this.saldo = saldoInicial;
    }

    /**
     * Realiza a operação de saque para um cliente comum.
     *
     * @param valorSaque O valor a ser sacado da conta do cliente comum.
     */
    @When("solicitar um saque de {int} reais")
    public void solicitar_um_saque_de_reais(int valorSaque) {
        // Lógica para saque de um cliente comum
        // (Pode ser implementada conforme a necessidade)
    }

    /**
     * Verifica se o saque não foi efetuado e se a mensagem de saldo insuficiente é retornada.
     */
    @Then("não deve efetuar o saque e deve retornar a mensagem Saldo Insuficiente")
    public void não_deve_efetuar_o_saque_e_deve_retornar_a_mensagem_saldo_insuficiente() {
        // Lógica para verificar se o saque de um cliente comum não foi efetuado
        // e se a mensagem de saldo insuficiente é retornada.
    }

    /**
     * Verifica se o saldo esperado é igual ao saldo atualizado.
     *
     * @param esperado O saldo esperado após uma operação.
     */
    private void assertSaldoEquals(int esperado) {
        if (this.saldoEsperado != esperado) {
            throw new RuntimeException("Saldo não corresponde ao esperado");
        }
    }

    /**
     * Verifica mais resultados (método pendente).
     */
    @Then("check more outcomes")
    public void check_more_outcomes() {
        throw new io.cucumber.java.PendingException();
    }
}

```

## Saída Cucumber
```
nov. 28, 2023 11:40:38 PM cucumber.api.cli.Main run
ADVERTÊNCIA: You are using deprecated Main class. Please use io.cucumber.core.cli.Main

@tag @tag1
Scenario: Cliente especial com saldo negativo                            # src/test/java/arquivo_teste.feature:25
  Given Um cliente especial com saldo atual de -200 reais                # Conta.um_cliente_especial_com_saldo_atual_de_reais(int)
  When for solicitado um saque no valor de 100 reais                     # Conta.for_solicitado_um_saque_no_valor_de_reais(int)
  Then deve efetuar o saque e atualizar o saldo da conta para -300 reais # Conta.deve_efetuar_o_saque_e_atualizar_o_saldo_da_conta_para_reais(int)
  And check more outcomes                                                # Conta.check_more_outcomes()
      io.cucumber.java.PendingException: TODO: implement me
	at Conta.check_more_outcomes(Conta.java:88)
	at ✽.check more outcomes(file:///C:/Users/limei/eclipse-workspace/BDD/src/test/java/arquivo_teste.feature:29)


@tag @tag2
Scenario Outline: Cliente comum com saldo negativo                            # src/test/java/arquivo_teste.feature:32
  Given Um cliente comum com saldo atual de -200 reais                        # Conta.um_cliente_comum_com_saldo_atual_de_reais(int)
  When solicitar um saque de 200 reais                                        # Conta.solicitar_um_saque_de_reais(int)
  Then não deve efetuar o saque e deve retornar a mensagem Saldo Insuficiente # Conta.não_deve_efetuar_o_saque_e_deve_retornar_a_mensagem_saldo_insuficiente()

Pending scenarios:
file:///C:/Users/limei/eclipse-workspace/BDD/src/test/java/arquivo_teste.feature:25 # Cliente especial com saldo negativo

2 Scenarios (1 pending, 1 passed)
7 Steps (1 pending, 6 passed)
0m0,519s


io.cucumber.java.PendingException: TODO: implement me
	at Conta.check_more_outcomes(Conta.java:88)
	at ✽.check more outcomes(file:///C:/Users/limei/eclipse-workspace/BDD/src/test/java/arquivo_teste.feature:29)



```

## Professor
Daniel Domingos Akira de Sa Pimentel Ohata
