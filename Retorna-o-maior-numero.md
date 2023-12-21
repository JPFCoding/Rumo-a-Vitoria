#include <stdio.h>
#include <locale.h>
int main()
{
 setlocale(LC_ALL, "portuguese"); //Brazilian Portuguese
 int v[10],a,cm=0;
 float s=0;
     for(a=0;a<10;a++){
        printf("Posição %d",a+1);
        printf("\nDigite um valor:\n\t");
        scanf("%d",&v[a]);
        }
    for(a=0;a<10;a++){
            if(v[a]>cm){
                    cm=v[a];
            }
        }
    for(a=0;a<10;a++){
        s=s+v[a];
    }
    s=s/10;
    printf("\nO maior é: %d",cm);
    printf("\nO somatório é: %f",s);
return(0);
}