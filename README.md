
#include<stdio.h>
#include<stdlib.h>

int main()
{
    size_t poczatek = 1,srodek = 2;
    size_t koniec = 4 ;
    void *wsk;
    int n=1, pr=0;
 while(pr==0)
    {
    if(wsk=(void*)malloc(koniec)){
        free(wsk);
        poczatek=koniec;
        koniec *= 2;
        n++;
        printf("szukam, %zu %d %zu\n", koniec, n, poczatek);
        }else pr=1;
    }
    printf("znalazlem %zu DO %zu ", poczatek, koniec);
    srodek = (koniec+poczatek)/2;

    while( koniec - poczatek != 1)
    {
        if(!(wsk=(void*)malloc(srodek)))
        {
            koniec = srodek ;
            free(wsk);
        }
        else if((wsk=(void*)malloc(srodek))==NULL)
        {
            poczatek = srodek ;
            free(wsk);
        }
         srodek = (koniec+poczatek)/2;
    }
    if((wsk=(void*)malloc(koniec))==NULL)
    {
        printf("koniec == Null ");
        free(wsk);
    }

    if((wsk=(void*)malloc((4000000000)))==NULL)
    {
         printf("poczatek == Null ");

    }
    printf("\nLiczba bitow max : %zu  ", koniec );
    free(wsk);
    return 0;
}
