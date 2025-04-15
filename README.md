# TrabalhoDosSignos
package trabalhoprojetosigno;

import java.util.Calendar;
import java.util.Scanner;

/**
 * Você foi contratado para desenvolver um sistema para a empresa chamada "Sei
 * de Tudo", que oferece consultoria de Zodíaco. Seu programa deve solicitar as
 * seguintes informações do usuário: nome, sexo, dia, mês e ano de nascimento.
 * Com base nesses dados, o programa calculará a idade do usuário, identificará
 * o signo correspondente e apresentará informações personalizadas, como o
 * número da sorte e a cor da sorte.
 *
 * @author Kelvyn Prichoa
 *
 */
public class TrabalhoProjetoSigno {

    private static Object hoje;

    public static void main(String[] args) {
        //Declaração das variáveis
        String nome, signo = "", cor = "";
        int sexo, dia, mes, ano, idade;
        int numCor,diaAtual, mesAtual, anoAtual, corSorte, numeroSorte;
        boolean dataValida;
        Scanner ler = new Scanner(System.in);

        //Entrada de dados de data de nascimento
        System.out.print("Digite seu nome: ");
        nome = ler.nextLine();

        if (nome.length() < 8) {
            System.out.println("Seu nome não foi informado corretamente");
        }

        System.out.println("Digite seu sexo (1 - Feminino / 2 - Masculino):");
        sexo = ler.nextInt();

        if (sexo != 1 && sexo != 2) {
            sexo = 2;
        }

        System.out.println("Digite o dia de nascimento:");
        dia = ler.nextInt();
        System.out.println("Digite o mês do nascimento:");
        mes = ler.nextInt();
        System.out.println("digite o ano do nascimento:");
        ano = ler.nextInt();

        //Processamento
        //Utilização do comando Calendar.get para obter a data atual
        Calendar hoje = Calendar.getInstance();
        diaAtual = hoje.get(Calendar.DATE);
        mesAtual = hoje.get(Calendar.MONTH) + 1;
        anoAtual = hoje.get(Calendar.YEAR);

        //Vereficação da data
        dataValida = true;

        if (mes == 2 && dia > 28) {
            dataValida = false;
        } else if ((mes == 4 || mes == 6 || mes == 9 || mes == 11) && dia > 30) {
            dataValida = false;
        } else if (dia < 1 || dia > 31 || mes < 1 || mes > 12 || ano < 1900 || ano > anoAtual) {
            dataValida = false;
        }

        //Calculo da idade
        idade = anoAtual - ano;
        if (mes > mesAtual || (mes == mesAtual && dia > diaAtual)) {
            idade--;
        }

        // Identificação dos signos
        if ((dia >= 21 && mes == 3) || (dia <= 19 && mes == 4)) {
            signo = "Áries";
        } else if ((dia >= 20 && mes == 4) || (dia <= 20 && mes == 5)) {
            signo = "Touro";
        } else if ((dia >= 21 && mes == 5) || (dia <= 20 && mes == 6)) {
            signo = "Gêmeos";
        } else if ((dia >= 21 && mes == 6) || (dia <= 22 && mes == 7)) {
            signo = "Câncer";
        } else if ((dia >= 23 && mes == 7) || (dia <= 22 && mes == 8)) {
            signo = "Leão";
        } else if ((dia >= 23 && mes == 8) || (dia <= 22 && mes == 9)) {
            signo = "Virgem";
        } else if ((dia >= 23 && mes == 9) || (dia <= 22 && mes == 10)) {
            signo = "Libra";
        } else if ((dia >= 23 && mes == 10) || (dia <= 21 && mes == 11)) {
            signo = "Escorpião";
        } else if ((dia >= 22 && mes == 11) || (dia <= 21 && mes == 12)) {
            signo = "Sagitário";
        } else if ((dia >= 22 && mes == 12) || (dia <= 19 && mes == 1)) {
            signo = "Capricórnio";
        } else if ((dia >= 20 && mes == 1) || (dia <= 18 && mes == 2)) {
            signo = "Aquário";
        } else if ((dia >= 19 && mes == 2) || (dia <= 20 && mes == 3)) {
            signo = "Peixes";
        } else {
            System.out.println("signo não existe");
        }

        //Numero e cor da sorte
        numeroSorte = 1 + (int) (Math.random() * 99);
        numCor = 1 + (int) (Math.random() * 5);

        switch (signo) {
            case "Áries":
                cor = "amarelo";
                break;
            case "Touro":
                cor = "verde";
                break;
            case "Gêmeos":
                cor = "vermelho";
                break;
            case "Câncer":
                cor = "prata";
                break;
            case "Leão":
                cor = "dourado";
                break;
            case "Virgem":
                cor = "marrom";
                break;
            case "Libra":
                cor = "rosa";
                break;
            case "Escorpião":
                cor = "preto";
                break;
            case "Sagitário":
                cor = "roxo";
                break;
            case "Capricórnio":
                cor = "cinza";
                break;
            case "Aquário":
                cor = "azul";
                break;
            case "Peixes":
                cor = "lilaz";
                break;
            default:
                cor = "indefinida";
                break;
        }

        //Finalização e saida de dados
        if (dataValida) {
            String tratamento = (sexo == 1) ? "Sra." : "Sr.";
            String generoLetra = (sexo == 1) ? "a" : "o";

            System.out.println(tratamento + " " + nome + ", nascid" + generoLetra
                    + " em " + dia + "/" + mes + "/" + ano + ", é do signo de " + signo + ".");
            System.out.println("Você tem " + idade + " anos. Seu número da sorte é "
                    + numeroSorte + " e sua cor é " + cor + ".");
        } else {
            System.out.println("Data de nascimento inválida!");
        }

    }

}
