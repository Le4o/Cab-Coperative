#include <stdio.h>
#include<string.h>
#include<stdlib.h>
#include<time.h>

typedef struct{
    int chave;

    char Placa[8];
    char NomeTaxista[15];
    int CapacidadeTaxi;
}tipoTaxi;

typedef struct Celula* Apontador;

typedef struct Celula{
    tipoTaxi info;
    struct Celula* prox;

}TCelula;

typedef struct TFila{
    Apontador Frente;
    Apontador Tras;
}TFila;
//-------------------------FUNCTIONS------------------------
int INICIAR(TFila* pfila);
int TaxisDisponiveis(TFila* pfila);
int TODOSTaxisDisponiveis(TFila* pfila);
int InserirTaxi(TFila* pfila, tipoTaxi* item);
void MostrarTaxi(TFila* pfila, int chave);
int ChamarTaxi(TFila* pfila);
int ChamarTaxiALEATORIO(TFila* pfila);
LRetiraQualquer(int valor, TFila* pfila);
//--------------------------MAIN--------------------------
int main(){
    int contador = 1;
    char operacao;
    TFila fila1;
    tipoTaxi item;
    INICIAR(&fila1);

	printf("\t\tMIMOSA TAXIS\n\n");
    printf("T - Numero total taxis disponiveis. \n");
    printf("A - Adicionar um taxi. \n");
    printf("S - Autorizar a saida do primeiro taxi. \n");
    printf("L - Listar todos os taxis disponiveis. \n");
    printf("D - Escolher taxi aleatorio. \n");
    printf("informe a operacao: ");
    scanf (" %c",&operacao);
    while(operacao != 'Z'){
        switch(operacao){
                case 'T' :{
                    printf("O numero total de taxis e de: %d\n", TaxisDisponiveis(&fila1));
                    system("PAUSE");
                break;
            }
                case 'A' :{
                item.chave = contador;
                printf("informe o Nome do Taxista: \n");
                scanf (" %[^\n]c",&item.NomeTaxista);
                printf("informe a Placa: \n");
                scanf (" %[^\n]c",&item.Placa);
                printf("informe a Capacidade do Taxi: \n");
                scanf (" %d",&item.CapacidadeTaxi);
                InserirTaxi(&fila1,&item);
                printf("Inserido com sucesso!!! \n");
                contador++;
                system("PAUSE");
                break;
            }
                case 'S' :{
                    ChamarTaxi(&fila1);
                    system("PAUSE");
                break;
            }
                case 'L' :{
                    TODOSTaxisDisponiveis(&fila1);
                    system("PAUSE");
                break;
            }
                case 'C' :{
                   
                break;
			}
                case 'D' :{
                    ChamarTaxiALEATORIO(&fila1);
                    system("PAUSE");
                break;
			}
                case 'E' :{
                    system("CLS");
                    exit(1);
                    break;
                }
          
            default: {
                printf("Operacao indisponivel\n\n");
                system("PAUSE");
                break;
            }

        }
        system("cls");
    printf("T - Numero total taxis disponiveis. \n");
    printf("A - Adicionar um taxi. \n");
    printf("S - Autorizar a saida do primeiro taxi. \n");
    printf("L - Listar todos os taxis disponiveis. \n");
    printf("D - Escolher taxi aleatorio. \n");
    printf("E - Sair\n");
    printf("informe a operacao: ");
    scanf (" %c",&operacao);
    }



    printf("tudo ok");


    return 1;
}
//--------------------------IMPLEMENTACOES----------------
int INICIAR(TFila* pfila){

    pfila->Frente = (Apontador)malloc(sizeof(TCelula));

    if(pfila->Frente==NULL)
        return 0;

    pfila->Tras = pfila->Frente;
    pfila->Frente->prox = NULL;
    return 1;
}
int InserirTaxi(TFila* pfila, tipoTaxi* item){

    Apontador NovoTaxi;
    NovoTaxi = (Apontador)malloc(sizeof(TCelula));

    if(NovoTaxi==NULL){
        printf("Nao foi possivel adicionar\n");
        return 0;
    }

    pfila->Tras->prox = NovoTaxi;
    pfila->Tras = NovoTaxi;
    NovoTaxi->info = *item;
    NovoTaxi->prox = NULL;
    return 1;
}
int ChamarTaxi(TFila* pfila){

    if(TaxisDisponiveis(pfila)==0){
        printf("Sem taxis disponiveis\n");
        return 0;
    }

    Apontador aux;
    aux = pfila->Frente->prox;

   
    printf("Taxi solicitado com sucesso!! CHAVE: %d \n\n",aux->info.chave);
        int valor = aux->info.chave;
        printf("\tTAXISTA: %s\n", aux->info.NomeTaxista);
    	printf("\tPLACA: %s\n", aux->info.Placa);
    	printf("\tCAPACIDADE DO CARRO: %d\n", aux->info.CapacidadeTaxi);
        
    LRetiraQualquer(aux->info.chave,pfila);
    
    return 1;
}
void MostrarTaxi(TFila* pfila, int valor){

    Apontador aux;
    aux = pfila->Frente;
    while(aux!=NULL && aux->info.chave != valor){
        aux = aux->prox;
    }
    fflush(stdin);
    printf("\tTAXISTA: %s\n", aux->info.NomeTaxista);
    printf("\tPLACA: %s\n", aux->info.Placa);
    printf("\tCAPACIDADE DO CARRO: %d\n", aux->info.CapacidadeTaxi);

}
int TaxisDisponiveis(TFila* pfila){

    int count=0;
    Apontador aux;
    aux = pfila->Frente->prox;
    while(aux!=NULL){
        count++;
        aux = aux->prox;
    }

    return count;
}
int TODOSTaxisDisponiveis(TFila* pfila){

    if(TaxisDisponiveis(pfila)==0){
        printf("Sem Taxis Disponiveis \n");
        return 0;
    }

    Apontador aux;
    aux = pfila->Frente->prox;
    while(aux!=NULL){
        printf("\tTAXISTA: %s\n", aux->info.NomeTaxista);
    	printf("\tPLACA: %s\n", aux->info.Placa);
    	printf("\tCAPACIDADE DO CARRO: %d\n", aux->info.CapacidadeTaxi);
        aux = aux->prox;
    }
    return 1;
}

int ChamarTaxiALEATORIO(TFila* pfila){

    if(TaxisDisponiveis(pfila)==0){
        printf("Sem Taxis Disponiveis\n");
        return 0;
    }

    int maximo = pfila->Tras->info.chave;
    srand((unsigned)time(NULL));
    int aleatorio = rand()%maximo;

    Apontador aux, ant, prox;
    aux = pfila->Frente;

    int soma = aleatorio+1;
    while(aux!=NULL && aux->info.chave != soma){
      //  ant = aux;
        aux = aux->prox;
    //    prox = aux->prox;
    }
if(aleatorio != 0 && soma > maximo ){
    soma = maximo;
}

    printf("Taxi solicitado com sucesso!! %d\n",aux->info.chave);

    MostrarTaxi(pfila, aux->info.chave);
	LRetiraQualquer(aux->info.chave,pfila);

    return 1;
}

LRetiraQualquer(int valor, TFila* pfila)
{
   TCelula *p, *q;
   p = pfila->Frente;
   q = p->prox;
   while (q != NULL && q->info.chave != valor) {
      p = q;
      q = q->prox;
   }
   if (q != NULL ) {
      p->prox = q->prox;
      free (q);
   }
}
