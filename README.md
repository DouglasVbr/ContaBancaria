# ContaBancaria

PARTE.1
package contabancaria;

public class ContaBancaria {
    public static void main(String[] args) {
        // Criando um objeto ContaBancaria
        ContaBancaria2 conta1 = new ContaBancaria2(12345, "Douglas Vieira", 1200);
        
        // Exibindo informações da conta
        System.out.println("Número da Conta: " + conta1.getnumeroConta());
        System.out.println("Nome do Titular: " + conta1.getnomeTitular());
        System.out.println("Saldo: " + conta1.getsaldo());
        
        // Depositando um valor na conta
        conta1.depositar(1000.0);
        System.out.println("Novo saldo após depósito: " + conta1.getsaldo());
        
        // Sacando um valor da conta
        conta1.sacar(500.0);
        System.out.println("Novo saldo após saque: " + conta1.getsaldo());
    }
}

PARTE.2

//Classe Conta Bancária:
//Crie uma classe ContaBancaria com os atributos numeroConta, nomeTitular, saldo.
//Implemente um método construtor que inicialize os atributos numeroConta e nomeTitular,
//e defina o saldo inicial como zero. Em seguida,
//crie métodos acessores para os atributos numeroConta,
//nomeTitular e saldo, além de métodos para depositar e sacar valores da conta.
package contabancaria;

public class ContaBancaria2 {

    private int numeroConta;
    private String nomeTitular;
    private double saldo;

    // Construtor
    public ContaBancaria2(int numeroConta, String nomeTitular, double saldo) {
        this.numeroConta = 12345;
        this.nomeTitular = "Douglas Vieira";
        this.saldo = 1.20000;
    }

   

    //metodo setnumero da conta
    public int setnumeroConta(int numeroConta) {
        this.numeroConta = numeroConta;
        return numeroConta;
    }

    // Métodos getnumeroConta
    public int getnumeroConta() {
        return numeroConta;
    }

    //metodo setnometitular
    public String setnomeTitular(String nomeTitular) {
        this.nomeTitular = nomeTitular;
        return nomeTitular;

    }

    public String getnomeTitular() {
        return nomeTitular;
    }
    
    // metodo setsaldo
    public double setsaldo(double saldo){
        this.saldo = saldo;
        return saldo;
    
    }

    public double getsaldo() {
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


