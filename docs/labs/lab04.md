# Lab 4 - RISC-V

## Objetivos

- Divertirse con RISC-V
- Encontrar los errores de Ali
- Hacer algo imposible
- Pensar en la idea de hacer lo imposible

## Lecturas

![PH](/assets/img/PH.jpg)

- P&amp;H: 2.12

## Preparación

Para comenzar con el laboratorio primero tienen que tener todos los archivos base, estos se encuentran [aquí](https://classroom.github.com/a/K8HV0OQl). Recuerden que deben
aceptar la asignación de **GitHub Classroom** y se les creará automáticamente un repositorio con una extensión que termina con su usuario de GitHub.
Cuando ya se haya creado el repositorio, pueden ejecutar los siguientes comandos abriendo una terminal (<kbd>CTRL</kbd><kbd>+</kbd><kbd>T</kbd>):

```shell
git clone <link del repositorio>
```

> **NOTA**: Tienen que reemplazar <link del repositorio\> con el link del repositorio que se creó.

## Ejercicio 1: Depurando megalistmanips.s

Hace mucho tiempo, su catedrático Ali era un principiante en RISC-V, y escribió su solución a un lab en este archivo: **megalistmanips.s**. Ustedes, ahora que ya son expertos en RISC-V, deben arreglar los bugs que cometió Ali.

El objetivo principal de este ejercicio es que encuentren los errores en la función **map** en **megalistmanips.s**.
Antes de hacer eso, familiarícense con lo que la función trata de hacer.

En el lab anterior, teníamos una lista encadenada de enteros, ahora nuestra estructura de datos es una lista encadena cuyo valor en cada nodo es un **arreglo** de enteros. Recuerden que cuando se trabaja con arreglos en structs, necesitamos almacenar explícitamente el tamaño del array. En código de C, el `struct` se vería así:

```c
struct node {
  int *arr;
  int size;
  struct node *next;
};
```

Aquí también está lo que la nueva función **map** hace: atraviesa la lista encadenada y para cada elemento del arreglo de cada nodo, aplica la función y vuelve a guardarlo en el array. En C, esto se miraría de la siguiente manera:

```c
void map(struct node *head, int (*f)(int)) {
  if (!head) { return; }
  for (int i = 0; i < head->size; i++) {
    head->arr[i] = f(head->arr[i]);
  }
  map(head->next, f);
}
```

Lean todos los comentarios en la función **map** en **megalistmanips.s** (antes de que retorne con `jr ra`), y asegúrense de que las líneas hagan lo que el comentario dice.

Algunas pistas:

- ¿Por qué necesitamos guardar cosas en el stack antes de llamar a `jal`?
- ¿Cuál es la diferencia entre `add t0, s0, x0` y `lw t0, 0(s0)`?
- Presten atención a los tipos de los atributos en el `struct`.

¡Gracias por hacer el ejercicio! Estamos seguros de que Ali se estará preguntando dónde estaban para ayudarlo cuando no entendía RISC-V hace un tiempo atrás.

## Ejercicio 2: Escriban una función sin utilizar branches

Consideren la función $f$ de valor discreto definida en el set de enteros ${-3, -2, -1, 0, 1, 2, 3}$. Esta es la definición de la función:

$\begin{align}
&f(-3) = 6\\\\
&f(-2) = 61\\\\
&f(-1) = 17\\\\
&f(0) = -38\\\\
&f(1) = 19\\\\
&f(2) = 42\\\\
&f(3) = 5
\end{align}$

No les vamos a mentir, es una función muy tonta. Sin embargo, su tarea es implementarla en RISC-V, con la condición de que **<span style="color: red;">NO</span>** pueden utilizar las instrucciones de branch por ningún motivo. Por suerte alguna persona ha dejado por accidente un array de enteros en la sección `.data` de **_discrete_fn.s_**. ¿Cómo pueden utilizarlo para tener ventaja sobre eso y completar esta tarea que aparenta ser imposible?

## Calificación

Por favor actualizar siempre la versión del CLI de autograders:

```
pip3 install --upgrade autograders-cli
```

Entregaremos este lab de la misma manera que el pasado.

Navegue hacia la carpeta donde tiene sus archivos, haga un ls y asegurese que le aparece el archivo autograders.json; si aparecio, esta en el lugar correcto. Ahora puede entregar su laboratorio con...

```
autograder --upload
```

Espera un minuto aprox. y luego puede ver sus resultados con...

```
autograder --stats
```

Si le aparece Queued: True, espere un par de minutos y luego repita el `autograder --stats` únicamente. Al terminar todo, suba el link de su repositorio al GES.
