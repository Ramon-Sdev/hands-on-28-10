# hands-on-28-10
atividade da faculdade 
# Hands on - 20/10

# Hands on - 20/10 - Vetores em Java


```bash
javac ExN.java
java ExN
```

(troque `ExN` por `Ex2`, `Ex3`, ... `Ex7`)

---

## Exercício 1

Considere o vetor `x` e as variáveis `y = 2` e `z = 4`.

| Posição | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---------|---|---|---|---|---|---|---|---|---|---|
| Valor   | 15 | 7 | 3 | 37 | 9 | 10 | 4 | 56 | 1 | 81 |

**Qual o valor correspondente de cada solicitação?**

| Item | Expressão | Cálculo | Resultado |
|------|-----------|---------|-----------|
| a | `x[y+1]` | `x[3]` | **37** |
| b | `x[y*1]` | `x[2]` | **3** |
| c | `x[y+z]` | `x[6]` | **4** |
| d | `x[x[8]*x[6]]` | `x[1*4]` = `x[4]` | **9** |
| e | `x[y+2]` | `x[4]` | **9** |
| f | `x[y*2]` | `x[4]` | **9** |
| g | `x[8-x[6]]` | `x[8-4]` = `x[4]` | **9** |
| h | `x[x[1]]` | `x[7]` | **56** |
| i | `x[x[y+z]]` | `x[x[6]]` = `x[4]` | **9** |

---

## Exercício 2

Faça um programa que preencha dois vetores de dez elementos numéricos cada um e mostre o vetor resultante da intercalação deles.

- Vetor 1: `[3, 5, 4, 2, 2, 5, 3, 2, 5, 9]`
- Vetor 2: `[7, 15, 20, 0, 18, 4, 55, 23, 8, 6]`
- Intercalação: `[3, 7, 5, 15, 4, 20, 2, 0, 2, 18, 5, 4, 3, 55, 2, 23, 5, 8, 9, 6]`

`Ex2.java`

```java
import java.util.Arrays;
import java.util.Scanner;

public class Ex2 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[] v1 = new int[10];
        int[] v2 = new int[10];

        for (int i = 0; i < 10; i++) {
            System.out.print("Vetor 1, posicao " + i + ": ");
            v1[i] = sc.nextInt();
        }
        for (int i = 0; i < 10; i++) {
            System.out.print("Vetor 2, posicao " + i + ": ");
            v2[i] = sc.nextInt();
        }

        int[] inter = new int[20];
        for (int i = 0; i < 10; i++) {
            inter[2 * i] = v1[i];
            inter[2 * i + 1] = v2[i];
        }

        System.out.println("Intercalacao: " + Arrays.toString(inter));
    }
}
```

---

## Exercício 3

Faça um programa que preencha um vetor com oito números inteiros, calcule e mostre dois vetores resultantes. O primeiro vetor resultante deve conter os números positivos e o segundo, os números negativos. Cada vetor resultante vai ter, no máximo, oito posições, que não poderão ser completamente utilizadas.

`Ex3.java`

```java
import java.util.Scanner;

public class Ex3 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[] v = new int[8];
        int[] positivos = new int[8];
        int[] negativos = new int[8];
        int qtdPos = 0, qtdNeg = 0;

        for (int i = 0; i < 8; i++) {
            System.out.print("Numero " + (i + 1) + ": ");
            v[i] = sc.nextInt();
            if (v[i] > 0) {
                positivos[qtdPos++] = v[i];
            } else if (v[i] < 0) {
                negativos[qtdNeg++] = v[i];
            }
        }

        System.out.print("Positivos:");
        for (int i = 0; i < qtdPos; i++) {
            System.out.print(" " + positivos[i]);
        }
        System.out.println();

        System.out.print("Negativos:");
        for (int i = 0; i < qtdNeg; i++) {
            System.out.print(" " + negativos[i]);
        }
        System.out.println();
    }
}
```

---

## Exercício 4

Faça um programa que preencha um vetor com dez números inteiros, calcule e mostre os números primos e suas respectivas posições.

`Ex4.java`

```java
import java.util.Scanner;

public class Ex4 {
    static boolean ehPrimo(int n) {
        if (n < 2) return false;
        for (int d = 2; d * d <= n; d++) {
            if (n % d == 0) return false;
        }
        return true;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[] v = new int[10];

        for (int i = 0; i < 10; i++) {
            System.out.print("Numero " + (i + 1) + ": ");
            v[i] = sc.nextInt();
        }

        System.out.println("Numeros primos e suas posicoes:");
        boolean achou = false;
        for (int i = 0; i < 10; i++) {
            if (ehPrimo(v[i])) {
                System.out.println(v[i] + " na posicao " + i);
                achou = true;
            }
        }
        if (!achou) {
            System.out.println("Nenhum numero primo foi digitado.");
        }
    }
}
```

---

## Exercício 5

Escreva um programa em Java que leia 15 nomes de pessoas e armazene-os em um vetor. Após a digitação do último nome, imprima-os na sequência contrária (ou seja, o último nome digitado deve ser o primeiro a ser impresso e assim por diante).

`Ex5.java`

```java
import java.util.Scanner;

public class Ex5 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String[] nomes = new String[15];

        for (int i = 0; i < 15; i++) {
            System.out.print("Nome " + (i + 1) + ": ");
            nomes[i] = sc.nextLine();
        }

        System.out.println("Nomes na ordem inversa:");
        for (int i = 14; i >= 0; i--) {
            System.out.println(nomes[i]);
        }
    }
}
```

---

## Exercício 6

Escreva um programa em Java que leia 8 elementos e armazene-os em um vetor inteiro A. Construa outro vetor B, de mesma dimensão de A, com seus elementos sendo a multiplicação do elemento correspondente de A por 3. Mostre os elementos de B.

`Ex6.java`

```java
import java.util.Scanner;

public class Ex6 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[] a = new int[8];
        int[] b = new int[a.length];

        for (int i = 0; i < a.length; i++) {
            System.out.print("A[" + i + "]: ");
            a[i] = sc.nextInt();
            b[i] = a[i] * 3;
        }

        System.out.println("Vetor B (A x 3):");
        for (int i = 0; i < b.length; i++) {
            System.out.println("B[" + i + "] = " + b[i]);
        }
    }
}
```

---

## Exercício 7

Faça um programa que leia 6 números inteiros e mostre:

1. Os números pares digitados;
2. A soma dos números pares digitados;
3. Os números ímpares digitados;
4. A quantidade de números ímpares digitados.

`Ex7.java`

```java
import java.util.Scanner;

public class Ex7 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[] v = new int[6];

        for (int i = 0; i < 6; i++) {
            System.out.print("Numero " + (i + 1) + ": ");
            v[i] = sc.nextInt();
        }

        int somaPares = 0, qtdImpares = 0;

        System.out.print("Pares:");
        for (int n : v) {
            if (n % 2 == 0) {
                System.out.print(" " + n);
                somaPares += n;
            }
        }
        System.out.println();
        System.out.println("Soma dos pares: " + somaPares);

        System.out.print("Impares:");
        for (int n : v) {
            if (n % 2 != 0) {
                System.out.print(" " + n);
                qtdImpares++;
            }
        }
        System.out.println();
        System.out.println("Quantidade de impares: " + qtdImpares);
    }
}
```
