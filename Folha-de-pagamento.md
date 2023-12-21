#include <stdio.h>
#include <locale.h>
#include <math.h>
#include "FolhaDePagamento1.h"
//Developed by JPFCoding

int main()
{
    setlocale(LC_ALL, "portuguese");//Brazilian portuguese
    char nome[100];
    float sal,s=0;
    int a,z=0,sw;
    FILE *f;
    char linha[100];

    printf("\nTudo bem?\nSelecione a opção desejada:\n\tPara preencher hollerichs, digite um.\n\tPara ler hollerichs, digite 2.\n\t ");
    scanf("%d",&sw);
    switch(sw){
        case 1 :
            printf("\nQuantidade de funcionários\n");
            scanf("%d",&z);
            for(a=0;a<z;a++){
            printf("\nDigite o nome do Funcionário, sem acento e com hífen ou ''Wonderline'' ao invés de espaço:\n\t");
            scanf("%100s",nome);
            printf("\nQual o seu salário?\nR$");
            scanf("%f",&sal);
            if(sal<=1100){
                printf("\nCategoria 1\n");
                s=salario1(sal);
                printf("Nome do Funionário: %s",nome);
                printf("\nSalário Bruto %4.f",sal);
                printf("\nDesconto do INSS\nR$ %4f",s);
            }
            if(sal>1100 && sal<=2203.48){
                printf("\nCategoria 2\n");
                s=salario2(sal);
                printf("Nome do Funionário: %s",nome);
                printf("\nSalário Bruto %4.f",sal);
                printf("\nDesconto do INSS\nR$ %4.f",s);
            }
             if(sal>2203.49 && sal<=3305.22){
                printf("\nCategoria 3\n");
                s=salario3(sal);
                printf("Nome do Funionário: %s",nome);
                printf("\nSalário Bruto %4.f",sal);
                printf("\nDesconto do INSS\nR$ %4.f",s);
            }
             if(sal>3305.22 && sal<=6433.47){
                printf("\nCategoria 4\n");
                s=salario4(sal);
                printf("Nome do Funionário: %s",nome);
                printf("\nSalário Bruto %4.f",sal);
                printf("\nDesconto do INSS\nR$ %4.f",s);
            }
             if(sal>6433.47){
                printf("\nCategoria 5\n");
                s=salario5(sal);
                printf("Nome do Funionário: %s",nome);
                printf("\nSalário Bruto %4.f",sal);
                printf("\nDesconto do INSS\nR$ %4.f",s);
             }
            f=fopen("Holerich.txt","a");//A=append ou acrescentar;R=read ou ler;W=write ou escrever;
            fprintf(f,"Nome do Funcionário: %s\n",nome);
            fprintf(f,"Salario Bruto: %f\n",sal);
            fprintf(f,"Desconto INSS: %f\n\n",s);
            fclose(f);
            }
            break;
        case 2:
            f = fopen("Holerich.txt", "r");
            if (f == NULL) {
                printf("\nHollerich inexistente.\nPor favor, preencha primeiro.");
                return(1);
            }
            while(fgets(linha, sizeof(linha), f) != NULL){
                printf("%s", linha);
            }
            fclose(f);

            break;
        default :
            printf("Opção inexistente. Reinicie o programa.");
            break;
        }
    return (0);
}
