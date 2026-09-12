# ATIVIDADE: AULA 01

### ATIVIDADE UTILIZADA: SISTEMA DE SENSORES

Essa atividade fez parte do conteúdo de alocação dinâmica, onde um engenheiro chefe não sabe quantos registros de nível de água serão feitos por dia, então deveria ser feito um algoritmo que não usasse um número fixo de medições.

O passos necessários eram:

* Usar uma `malloc` para criar um vetor de inteiros exatamente do tamanho necessário;
* usar `sizeof` pro `malloc` saber o tamanho de cada "gaveta";
* Realizar uma verificação pra saber se a alocação foi feita corretamente
* Usar um laço pra receber os valores das medições;
* Ao final liberar a memória com o uso d `free`.

---

Código da atividade:

```
#include <stdio.h>
#include <stdlib.h>

int main() {
  int n, i;
  int *medicoes;

  printf("Quantas medições você deseja realizar hoje? ");
  scanf("%d", &n);

  medicoes = (int*) malloc(n*sizeof(int));

  if (medicoes == NULL) {
  printf("Erro na alocação de memória");
  return 1;
  }

  for (i=0;i<n;i++) {
  printf("Digite a medição: ", i + 1);
  scanf("%d", &medicoes[i]);
  }

  for (i=0;i<n;i++) {
  printf("%d - %d\n", i + 1, medicoes[i]);
  }

  for (i=0;i<n;i++) {
  printf("%d - %d - %p\n", i + 1, medicoes[i], (medicoes+i));
  }

  free(medicoes);
  medicoes = NULL;
  return 0;
}

```
