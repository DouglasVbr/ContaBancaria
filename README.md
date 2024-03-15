# ContaBancaria

PARTE.1
package Main;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Cliente cliente = null;
        Conta conta = null;
        boolean programaAtivo = true;

        while (programaAtivo) {
            System.out.println("Selecione a opção:");
            System.out.println("1- Cadastro de cliente");
            System.out.println("2- Conta Bancária");
            System.out.println("3- Saldo");
            System.out.println("4- Transação");
            System.out.println("5- Sair");

            int opcao = scanner.nextInt();

            switch (opcao) {
                case 1:
                    System.out.println("Digite o número da conta:");
                    int numeroConta = scanner.nextInt();
                    System.out.println("Digite o nome do titular:");
                    String nomeTitular = scanner.next();
                    System.out.println("Digite o CPF do titular:");
                    String cpf = scanner.next();
                    System.out.println("Digite a agência:");
                    int agencia = scanner.nextInt();
                    System.out.println("Digite o saldo inicial:");
                    double saldoInicial = scanner.nextDouble();
                    cliente = new Cliente(numeroConta, nomeTitular, cpf, agencia, saldoInicial);
                    System.out.println("Cadastro de cliente realizado com sucesso.");
                    System.out.println("Dados do cliente:");
                    System.out.println(cliente);
                    break;
                case 2:
                    if (cliente != null) {
                        conta = new Conta(cliente);
                        System.out.println("Conta bancária criada com sucesso.");
                    } else {
                        System.out.println("Por favor, cadastre um cliente primeiro.");
                    }
                    break;
                case 3:
                    if (conta != null) {
                        System.out.println("Saldo: " + conta.getSaldo());
                    } else {
                        System.out.println("Por favor, crie uma conta bancária primeiro.");
                    }
                    break;
                case 4:
                    if (conta != null) {
                        System.out.println("Digite o número da conta de destino:");
                        int numContaDestino = scanner.nextInt();
                        System.out.println("Digite o valor da transação:");
                        double valorTransacao = scanner.nextDouble();
                        Conta contaDestino = new Conta(null); 
                        Transacao transacao = new Transacao(conta, contaDestino, valorTransacao);
                        transacao.realizarTransacao();
                    } else {
                        System.out.println("Por favor, crie uma conta bancária primeiro.");
                    }
                    break;

                case 5:
                    System.out.println("Encerrando o programa.");
                    programaAtivo = false; // Desativa o loop
                    break;
                default:
                    System.out.println("Opção inválida.");
            }
        }
        scanner.close();
    }
}

PARTE.2

 package Main;
class Conta {

    private static int proximoNumeroConta = 1;

    private int numeroConta;
    private Cliente cliente;
    private double saldo;

    public Conta(Cliente cliente) {
        this.cliente = cliente;
        this.numeroConta = proximoNumeroConta++;
        if (cliente != null) {
            this.saldo = cliente.getSaldo();
        } else {
            this.saldo = 0; // Se o cliente for nulo, saldo inicial será 0
        }
    }

    public double getSaldo() {
        return saldo;
    }

    public int getNumeroConta() {
        return numeroConta;
    }

    public Cliente getCliente() {
        return cliente;
    }

    public void setNumeroConta(int numeroConta) {
        this.numeroConta = numeroConta;
    }

    public void setCliente(Cliente cliente) {
        this.cliente = cliente;
    }

    public void setSaldo(double saldo) {
        this.saldo = saldo;
    }

    public void depositar(double valor) {
        if (valor > 0) {
            saldo += valor;
            System.out.println("Depósito de " + valor + " realizado com sucesso.");
        } else {
            System.out.println("Valor de depósito inválido.");
        }
    }

    public void sacar(double valor) {
        if (valor > 0 && valor <= saldo) {
            saldo -= valor;
            System.out.println("Saque de " + valor + " realizado com sucesso.");
        } else {
            System.out.println("Saldo insuficiente para saque.");
        }
    }
}

parte.3
package Main;
class Cliente {

    private String nomeTitular;
    private String cpf;
    private int numeroConta;
    private int agencia;
    private double saldo;

    public Cliente(int numeroConta, String nomeTitular, String cpf, int agencia, double saldo) {
        this.numeroConta = numeroConta;
        this.nomeTitular = nomeTitular;
        this.cpf = cpf;
        this.agencia = agencia;
        this.saldo = saldo;
    }

    public String getNomeTitular() {
        return nomeTitular;
    }

    public String getCpf() {
        return cpf;
    }

    public int getNumeroConta() {
        return numeroConta;
    }

    public int getAgencia() {
        return agencia;
    }

    public double getSaldo() {
        return saldo;
    }

    public void setNumeroConta(int numeroConta) {
        this.numeroConta = numeroConta;
    }

    public void setNomeTitular(String nomeTitular) {
        this.nomeTitular = nomeTitular;
    }

    public void setCpf(String cpf) {
        this.cpf = cpf;
    }

    public void setAgencia(int agencia) {
        this.agencia = agencia;
    }

    public void setSaldo(double saldo) {
        this.saldo = saldo;
    }

    @Override
    public String toString() {
        return "Nome do titular: " + nomeTitular + "\nCPF: " + cpf + "\nNúmero da conta: " + numeroConta
                + "\nAgência: " + agencia + "\nSaldo: " + saldo;
    }
}
parte.4

package Main;

class Transacao {

   

    private Conta contaOrigem;
    private Conta contaDestino;
    private double valor;

    public Transacao(Conta contaOrigem, Conta contaDestino, double valor) {
        this.contaOrigem = contaOrigem;
        this.contaDestino = contaDestino;
        this.valor = valor;
    }

    public void realizarTransacao() {
        if (contaOrigem.getSaldo() >= valor) {
            contaOrigem.sacar(valor);
            contaDestino.depositar(valor);
            System.out.println("Transação realizada com sucesso. Valor transferido: " + valor);
            System.out.println("Saldo na conta de origem após a transação: " + contaOrigem.getSaldo());
        } else {
            System.out.println("Não há saldo suficiente na conta de origem para realizar a transação.");
        }
    }
}


