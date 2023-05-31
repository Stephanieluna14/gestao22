#include <stdio.h>
#include <stdlib.h>
#include <locale.h>
#include <math.h>
#include <string.h>
#include <ctype.h>

int main() {
	
	setlocale(LC_ALL, "Portuguese");
    // Informações do funcionário
	char nome[50];
	char cpf[12];
	char cargo[50];
	float salarioDia, valeTransporte, impostoRenda;
	float planoSaude = 600.0;
    int diasTrabalhados;
	int i = 0, escolha, voltar = 0;
    bool caracter;
    float salarioBruto, salarioLiquido;

    // Dados de descontos
	
	do {
        caracter = false;

        printf("Informe o nome do funcionario: ");
        fflush(stdout); // Limpa o buffer de saída antes de ler a entrada
        gets(nome);

        // Verifica cada caractere do nome
        for (int i = 0; nome[i] != '\0'; i++) {
            if (!isalpha(nome[i]) && nome[i] != ' ') {
                caracter = true;
                break;
            } 
        }
	    if (caracter) {
	            printf("\nO nome deve conter apenas letras. Tente novamente.\n\n");
	        }
	    } while (caracter);
	    system("cls");
    
    
    do {
        caracter = false;

        printf("Informe o cargo do funcionario: ");
        fflush(stdout); // Limpa o buffer de saída antes de ler a entrada
        gets(cargo);

        // Verifica cada caractere do nome
        for (int i = 0; cargo[i] != '\0'; i++) {
            if (!isalpha(cargo[i]) && cargo[i] != ' ') {
                caracter = true;
                break;
            } 
        }
	    if (caracter) {
	            printf("\nO cargo deve conter apenas letras. Tente novamente.\n\n");
	        }
	    } while (caracter);
	    system("cls");
	    
	
	    while (1) {
	        printf("Informe o CPF (11 dígitos, sem pontos ou traços): ");
	        fflush(stdout);
	        if (scanf("%11s", &cpf) != 1) {
	            printf("Entrada inválida! Digite apenas números.\n\n");
	            while (getchar() != '\n'); // Limpa o buffer do teclado
	            break; // Reinicia o loop
	        }
	
	        int count = 0;
	        for (int i = 0; cpf[i] != '\0'; i++) {
	            if (cpf[i] < '0' || cpf[i] > '9') {
	                printf("Entrada inválida! Digite apenas números.\n\n");
	                count = -1; // Sinaliza que a entrada é inválida
	                break; // Sai do loop for
	            }
	            count++;
	        }
			
			system("cls");
	        if (count == 11) {
	        	
                 break;// Sai do loop while
	        } else {
	           printf("CPF inválido! Digite exatamente 11 dígitos.\n");
        	}
		}
	    
	    
        printf("Informe o numero de dias trabalhados: ");
	    scanf("%d", &diasTrabalhados);
		system("cls");
			
	    printf("Informe o salario por dia: ");
	    scanf("%f", &salarioDia);
    	system("cls");
    	
	    salarioBruto = diasTrabalhados * salarioDia;
	    if (salarioBruto <= 1900.0) {
	        impostoRenda = 0.0;
	    } else if (salarioBruto <= 2800.0) {
	        impostoRenda = salarioBruto * 0.075;
	    } else if (salarioBruto <= 3700.0) {
	        impostoRenda = salarioBruto * 0.15;
		} else if (salarioBruto <= 4600.0) {
	        impostoRenda = salarioBruto * 0.225;
	    } else if (salarioBruto > 4601.0) {
	        impostoRenda = salarioBruto * 0.275;
	    }
	    
	    if (salarioBruto <= 1900.0) {
	        valeTransporte = 0.06;
	    } else if (salarioBruto <= 2800.0) {
	        valeTransporte = salarioBruto * 0.06;
	    } else if (salarioBruto <= 3700.0) {
	        valeTransporte = salarioBruto * 0.06;
		} else if (salarioBruto <= 4600.0) {
	        valeTransporte = salarioBruto * 0.06;
	    } else if (salarioBruto > 4601.0) {
	        valeTransporte = salarioBruto * 0.06;
	    }
	
	    // Cálculo do salário líquido com descontos
	    salarioLiquido = salarioBruto - valeTransporte - planoSaude - impostoRenda;
		
		while(escolha != 3){
		
		printf("1 - Ver folha de Pagamento.\n");
		printf("2 - Ver recibo de Salário.\n");
		printf("3 - Sair\n");
		printf("Escolha uma opção: ");
		scanf("%d", &escolha);
		
		system("cls");
		
		switch (escolha) {
			case 1:
				printf("\nFolha de Pagamento\n");
			    printf("Nome: %s\n", nome);
			    printf("Cargo: %s\n", cargo);
			    printf("CPF: %s\n", cpf);
			    printf("Dias Trabalhados: %d\n", diasTrabalhados);
			    printf("Salario por Dia: %.2f\n", salarioDia);
			    printf("salario Bruto: %.2f\n", salarioBruto);
			    printf("Descontos:\n");
			    printf(" - Vale Transporte: %.2f\n", valeTransporte);
			    printf(" - Plano de Saude: %.2f\n", planoSaude);
			    printf(" - Imposto de Renda: %.2f\n", impostoRenda);
			    printf("Salario Liquido: %.2f\n", salarioLiquido);
			
			break;
			
			case 2:
		        printf("\nRecibo de Salario\n");
			    printf("Nome: %s\n", nome);
			    printf("Cargo: %s\n", cargo);
			    printf("CPF: %s\n", cpf);
			    printf("Salario Bruto: %.2f\n", salarioBruto);
			    printf("Descontos:\n");
			    printf(" - Vale Transporte: %.2f\n", valeTransporte);
			    printf(" - Plano de Saude: %.2f\n", planoSaude);
			    printf(" - Imposto de Renda: %.2f\n", impostoRenda);
			    printf("Salario Liquido: %.2f\n\n", salarioLiquido);
				
			break;
			
			case 3:
				printf("Encerrando...");
				abort();
				break;
				
			default:
				printf("Opção inválida! Escolha a opção 1 ou 2!\n");
    }
    printf("\n------------------------------------------\n");
}
}
