# ContaBancaria

PARTE.1

// Arquivo: ContaBancaria.java
package contabancaria;

public class ContaBancaria {
    private int numeroConta;
    private String nomeTitular;
    private double saldo;
    
    // Construtor
    public ContaBancaria(int numeroConta, String nomeTitular) {
        this.numeroConta = 12345;
        this.nomeTitular = "João Silva";
        this.saldo = 0.0;
    }
    
    // Métodos acessores
    public int getNumeroConta() {
        return numeroConta;
    }
    
    public String getNomeTitular() {
        return nomeTitular;
    }
    
    public double getSaldo() {
        return saldo;
    }
    
    // Método para depositar um valor na conta
    public void depositar(double valor) {
        saldo += valor;
    }
    
    // Método para sacar um valor da conta
    public void sacar(double valor) {
        if (valor <= saldo) {
            saldo -= valor;
        } else {
            System.out.println("Saldo insuficiente.");
        }
    }
}


PARTE.2

// Arquivo: ContaBancariaMain.java
package contabancaria;

public class ContaBancariaMain {
    public static void main(String[] args) {
        // Criando um objeto ContaBancaria
        ContaBancaria conta1 = new ContaBancaria(12345, "João Silva");
        
        // Exibindo informações da conta
        System.out.println("Número da Conta: " + conta1.getNumeroConta());
        System.out.println("Nome do Titular: " + conta1.getNomeTitular());
        System.out.println("Saldo: " + conta1.getSaldo());
        
        // Depositando um valor na conta
        conta1.depositar(1000.0);
        System.out.println("Novo saldo após depósito: " + conta1.getSaldo());
        
        // Sacando um valor da conta
        conta1.sacar(500.0);
        System.out.println("Novo saldo após saque: " + conta1.getSaldo());
    }
}
