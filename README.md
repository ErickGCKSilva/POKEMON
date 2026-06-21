//# POKEMON
//Este projeto faz um comparativo entre os pokémons que você listar. Mostrando as estatisticas e seu nível.

#include <stdio.h>
#include <string.h>

typedef struct {

    char nome[50];
    char tipo[15];
    int nivel;
    int cp;
} Pokemon;

void classificacao(Pokemon pokemon[], char classe[][20]) {
    
    for (int i = 0; i<6; i++) {
        
        if(pokemon[i].cp<500) {
            strcpy(classe[i], "INICIANTE");
        } else if(pokemon[i].cp>=500 && pokemon[i].cp<1500) {
            strcpy(classe[i], "INTERMEDIARIO");
        } else {
            strcpy(classe[i], "LENDARIO");
        }
    }
}

void exibicao(Pokemon pokemon, char classe[]) {

    printf("Nome:\t%s | Tipo:\t%s | Nivel:\t%d | CP:\t%d |\nClasse:\t%s\n", pokemon.nome, pokemon.tipo, pokemon.nivel, pokemon.cp, classe);

}

int main() {

    Pokemon pokemon[6];
    char classe[6][20];
    int countfire = 0;
    int maiornivel = 0;
    int maiorcp = 0;
    int qual1 = 0;
    int qual2 = 0;


    for(int i = 0; i<6; i++) {
        printf("Digite o nome do pokemon %d:\t", i+1);
        scanf("%s", pokemon[i].nome);

        printf("Digite o tipo:\t");
        scanf("%s", pokemon[i].tipo);

        printf("Digite o nivel:\t");
        scanf("%d", &pokemon[i].nivel);

        printf("Digite o CP:\t");
        scanf("%d", &pokemon[i].cp);

        if(strcmp(pokemon[i].tipo, "Fogo") == 0) {
            countfire ++;
        }

        if(maiornivel<pokemon[i].nivel) {
            maiornivel = pokemon[i].nivel;
            qual1 = i;
        }

        if(maiorcp<pokemon[i].cp) {
            maiorcp = pokemon[i].cp;
            qual2 = i;
        }
    } 

    classificacao(pokemon, classe);
    
    printf("\n--RELATORIO POKEMON--\n");

    for (int i = 0; i<6; i++) {
        exibicao(pokemon[i], classe[i]);
    }

    printf("Pokemon de maior nivel:\t%s\n", pokemon[qual1].nome);
    printf("Pokemon com maior CP:\t%s\n", pokemon[qual2].nome);
    printf("Qunatidade de Pokemons do tipo Fogo:\t%d", countfire);

    return 0;
}
