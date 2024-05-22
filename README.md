# Calculadora-Cientifica-em-C

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

// Função para somar dois números
int soma(int a, int b) {
    return a + b;
}

// Função para subtrair dois números
int subtrai(int a, int b) {
    return a - b;
}

// Função para multiplicar dois números
int multiplica(int a, int b) {
    return a * b;
}

// Função para dividir dois números
float divide(float a, float b) {
    if (b != 0)
        return a / b;
    else {
        printf("Erro: Divisão por zero!\n");
        return 0;
    }
}

// Função para calcular a raiz quadrada
float raiz_quadrada(float a) {
    if (a >= 0)
        return sqrt(a);
    else {
        printf("Erro: Número negativo!\n");
        return -1;
    }
}

// Função para calcular o seno de um ângulo (em radianos)
float seno(float a) {
    return sin(a);
}

// Função para calcular a potência de um número
float potencia(float base, float expoente) {
    return pow(base, expoente);
}

// Função para limpar a tela
void clear_screen() {
    #ifdef _WIN32
        system("cls");
    #else
        system("clear");
    #endif
}

/* CALCULADORA CIENTÍFICA EM C */

int main(int argc, char** argv) {
    int operador;
    float num1, num2, resultado;
    int continuar = 1;

    while (continuar) {
        // Limpar a tela
        clear_screen();

        // Exibir o menu
        printf("Escolha a operação:\n");
        printf("1: Soma\n");
        printf("2: Subtração\n");
        printf("3: Multiplicação\n");
        printf("4: Divisão\n");
        printf("5: Raiz Quadrada\n");
        printf("6: Seno\n");
        printf("7: Potência\n");
        printf("8: Sair\n");
        printf("Digite o operador: ");
        scanf("%d", &operador);

        if (operador >= 1 && operador <= 4 || operador == 7) {
            // Para operações que necessitam de dois operandos
            printf("Digite o primeiro número: ");
            scanf("%f", &num1);
            
            printf("Digite o segundo número: ");
            scanf("%f", &num2);
        } else if (operador == 5 || operador == 6) {
            // Para operações que necessitam de apenas um operando
            printf("Digite o número: ");
            scanf("%f", &num1);
        } else if (operador == 8) {
            // Sair da calculadora
            continuar = 0;
            continue;
        }

        // Realizar a operação com base no operador
        switch (operador) {
            case 1:
                resultado = soma(num1, num2);
                printf("A soma é: %.2f\n", resultado);
                break;
            case 2:
                resultado = subtrai(num1, num2);
                printf("A subtração é: %.2f\n", resultado);
                break;
            case 3:
                resultado = multiplica(num1, num2);
                printf("A multiplicação é: %.2f\n", resultado);
                break;
            case 4:
                resultado = divide(num1, num2);
                if (num2 != 0)
                    printf("A divisão é: %.2f\n", resultado);
                break;
            case 5:
                resultado = raiz_quadrada(num1);
                if (num1 >= 0)
                    printf("A raiz quadrada é: %.2f\n", resultado);
                break;
            case 6:
                resultado = seno(num1);
                printf("O seno é: %.2f\n", resultado);
                break;
            case 7:
                resultado = potencia(num1, num2);
                printf("A potência é: %.2f\n", resultado);
                break;
            default:
                printf("Operador inválido!\n");
                break;
        }

        // Esperar o usuário pressionar Enter para continuar
        printf("Pressione Enter para continuar...");
        getchar(); // Para consumir o caractere de nova linha deixado pelo scanf
        getchar(); // Para aguardar o usuário pressionar Enter
    }

    return 0;
}
