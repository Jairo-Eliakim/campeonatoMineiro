#include<iostream>
#include<stdio.h>
#include<string.h>

using namespace std;

struct Time {
    char sigla[4];
    int v, e, d, gp,gc,sg,pt;
};




void troca(Time v[], int a, int b) {
    struct Time tmp = v[a];
    v[a] = v[b];
    v[b] = tmp;
}


void bubbleSort(Time v[]) {
    for (int i = 0; i < 12 - 1; i++) { // Número de vezes a repetir
        for (int j = 0; j < 12 - 1; j++) { // Número de comparações
            if (v[j].pt < v[j + 1].pt) { // Se não atende o critério de ordenação
            troca(v , j,  j+1);
            }
        }
    }
}


int main() {

    FILE *arq = fopen("tabela.txt", "r");

    Time times[12];
    char sigla1[4], sigla2[4];
    int resultado1, resultado2, ct = 0,v,n;

    while (fscanf(arq, "%s %dX%d %s", sigla1, &resultado1, &resultado2, sigla2) != -1) {
        int time1 = -1, time2 = -1;
        for (int t = 0; t < ct; t++) {
            if (strcmp(sigla1, times[t].sigla) == 0) time1 = t;
            if (strcmp(sigla2, times[t].sigla) == 0) time2 = t;
        }
        if (time1 == -1) {
            time1 = ct;
            strcpy(times[time1].sigla, sigla1);
            times[time1].v = 0;
            times[time1].e = 0;
            times[time1].d = 0;
            times[time1].pt = 0;
            times[time1].gp = 0;
            times[time1].gc = 0;
            times[time1].sg = 0;
            ct++;
        }
        if (time2 == -1) {
            time2 = ct;
            strcpy(times[time2].sigla, sigla2);
            times[time2].v = 0;
            times[time2].e = 0;
            times[time2].d = 0;
            times[time2].pt = 0;
            times[time2].gp = 0;
            times[time2].gc = 0;
            times[time2].sg = 0;

            ct++;
        }
        if (resultado1 > resultado2) {
            times[time1].v++;
            times[time1].pt = times[time1].pt + 3;
            times[time2].d++;

        } else if (resultado2 > resultado1) {
            times[time1].d++;
            times[time2].pt = times[time2].pt + 3;
            times[time2].v++;
        } else {
            times[time1].e++;
            times[time1].pt++;
            times[time2].pt++;
            times[time2].e++;
        }
            times[time1].gp = times[time1].gp + resultado1;
            times[time1].gc = times[time1].gc + resultado2;
            times[time2].gp = times[time2].gp + resultado2;
            times[time2].gc = times[time2].gc + resultado1;
            times[time1].sg = times[time1].gp - times[time1].gc;
            times[time2].sg = times[time2].gp - times[time2].gc;




    }
             bubbleSort(times);


    printf("TIME\tV\tE\tD\tP\tGP\tGC\tSG\n");
    for (int t = 0; t < 12; t++) {
        printf("%s\t%d\t%d\t%d\t%d\t%d\t%d\t%d\n", times[t].sigla, times[t].v, times[t].e, times[t].d, times[t].pt, times[t].gp, times[t].gc, times[t].sg);
    }

    return 0;
}
