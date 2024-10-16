---
id: 1727657007-insertion-sort
aliases:
  - Insertion Sort
tags:
  - algorithms
  - sorting
---

# Insertion Sort

- Insertion sort posiciona cada elemento en su índice correcto.
- Compara cada elemento con el anterior y los intercambia si el elemento actual es menor que el anterior.
- itera sobre la lista hasta que el elemento actual (currValue) sea el menor de todos los anteriores desde su posición inicial
- Contiene dos iteraciones, la primera recorre la lista y selecciona el elemento actual y la segunda compara con todos los valores anteriores hasta encontrar la posición correcta del valor actual.

## Código

```ts
function insertionSort(arr: number[]): number[] {
  for (let i = 1; i < arr.length; i++) {
    const currValue = arr[i];
    let j = i - 1;

    while (j >= 0 && arr[j] > currValue) {
      arr[j + 1] = arr[j];
      j--;
    }

    arr[j + 1] = currValue;
  }

  return arr;
}
```
