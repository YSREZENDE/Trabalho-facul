class Yasmin {

    static Scanner console = new Scanner(System.in);

    static final int TOTAL_AVALIACOES = 3;
    static final String[] NOMES_AVALIACOES = { "A1", "A2", "A3" };
    static final double[] NOTA_MAX_AVALIACOES = { 30.00, 30.00, 40.00 };

    static double[] notas = new double [TOTAL_AVALIACOES];


    static double lerNota(String mensagem, double notaMaxima) {

        double nota = 0.0;

        do {

            System.out.printf("%s = ", mensagem);
            nota = console.nextDouble();

        } while (nota < 0.00 || nota > notaMaxima);

        return nota;
    }


    static void atualizarNota(int indiceNota) {

        System.out.println();
        notas[indiceNota] = lerNota(NOMES_AVALIACOES[indiceNota], NOTA_MAX_AVALIACOES[indiceNota]);

    } // Fim do método atualizarNota

    static String avaliarSituacao(double notaFinal) {

        if(notaFinal < 30)
            return "REPROVADO";
        else if (notaFinal < 70)
            return "EM RECUPERAÇÃO";
        else
            return "APROVADO";

    } // Fim do método avaliarSituacao()

    public static double calcularMedia(double[] notas){
        double calcMedia= (Yamin.notas[0] + Yasmin.notas[1] + Yasmin.notas[2])/3;
        return calcMedia;
    }

    static String maiorNota(double[] notas){
        String maiorNota= "";
        double verificarMaior= 0;

        for (int i= TOTAL_AVALIACOES - 1; i>= 0; i--){
            if (notas[i] > verificarMaior){
                verificarMaior= notas[i];
                maiorNota= NOMES_AVALIACOES[i];
            }

        }
        return maiorNota;
    }

    static void atualizarNotaAI(double[] notas){
	double notaAI = 0;
	int menorNota = Yasmin.notas[0] <= Yasmin.notas[1]? 0:1;

	System.out.println("digite a nota da prova AI: ");                
	notaAI = lerNota("Nota AI", NOTA_MAX_AVALIACOES[menorNota]);

	if (notaAI > notas[menorNota]){
            notas[menorNota] = notaAI;
            System.out.printf("A Avaliação %s Foi Substituida Pela Avalição AI\n", NOMES_AVALIACOES[menorNota]);
	}
        else{
            System.out.println("A nota da prova AI não foi suficiente para alterar alguma prova");
        }
    }


    static void condicaoNotaAI(double[] notas) {
        double notaFinal= Yasmin.notas[0] + Yasmin.notas[1] + Yasmin.notas[2];
        if(notaFinal < 70) {
            System.out.printf("\n Insira a nota da AI: ");
	    double AI = console.nextDouble();

            if(AI > Yasmin.notas[0] || AI > Yasmin.notas[1]){
                if(AI > Yasmin.notas[0] && Yasmin.notas[0] < Yasmin.notas[1]){
                Yasmin.notas[0] = AI;
                }
                else{
                    Yasmin.notas[1] = AI;
                }
            }    
        }

    }       
            //notaAI(TOTAL_AVALIACOES);
	    //mostrarNotas();

    static void mostrarNotas() {

        double notaFinal = 0.0;

        System.out.printf("\n\n ===========================================");
        System.out.println("\n\t\tNOTAS");
        System.out.println();

        for (int i = 0; i < TOTAL_AVALIACOES; i++) {

            System.out.printf("   Avaliação %s = %.2f pts", NOMES_AVALIACOES[i], notas[i]);
            System.out.println();
            notaFinal += notas[i];
        }
        System.out.printf("\n   Média = %.2f pts", calcularMedia(notas));
        System.out.printf("\n   Maior nota: "+ maiorNota(notas));
        System.out.printf("\n   Nota Final = %.2f pts", notaFinal);
        System.out.printf("\n   Situação = %s", avaliarSituacao(notaFinal));
        System.out.printf("\n =========================================== \n");


    } // Fim do método mostrarNotas()


    static void notaAI(double notas){

    }


    static void mostrarMenu() {

        System.out.println("\n\n");
        System.out.println("\t\tMENU");
        System.out.println();

        System.out.println("[1] Cadastrar Notas A1");
        System.out.println("[2] Cadastrar Nota A2");
        System.out.println("[3] Cadastrar Nota A3");
        System.out.println("[4] Mostrar Notas");
        System.out.println("[0] SAIR");

        System.out.print("\nDigite uma opção:  ");
        byte opcao = console.nextByte();


        switch(opcao) {

            case 0:
                System.exit(0);
                break;

            case 1:
                atualizarNota(0);
                break;
            case 2:
            atualizarNota(1);
            break;

            case 3:
                atualizarNota(2);
                break;

            case 4:
                mostrarNotas();
                condicaoNotaAI(notas);
                break;

            default:
                mostrarMenu();
                break;

        }

        mostrarMenu();

    } // Fim do método mostrarMenu()


    public static void main(String[] args) {

        mostrarMenu();

    } // Fim do método main();

} // Fim da classe Main
