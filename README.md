# 🔢 Tipos de estructuras de datos en C#

## 📚 Tipos de Arrays

### 🔸 Arrays unidimensionales
Un **array unidimensional** almacena una lista de elementos del mismo tipo.

```csharp
int[] arrayNumbers = new int[5]; // Declaration with type size but without initialization
int[] arrayNumbersTwo = { 10, 20, 30, 40, 50 }; // Declaration with auto-detect type initialization
int[] arrayNumbersThree = new int[] { 5, 15, 25, 35, 45 }; // Explicit declaration with initialization

//Get the length of the array (number of elements)
Console.WriteLine($"The length of arrayNumbers is: {arrayNumbers.Length}");
// Alternative way to get the length of concrete dimension (for multi-dimensional arrays 0 - First dimension, 1 - second dimension, 2 - third dimension)
Console.WriteLine($"The length of arrayNumbers in the first dimension is: {arrayNumbers.GetLength(0)}");

Console.WriteLine(arrayNumbers[0]);
```
### 🔁 Recorrer array

### 🔸 con for
```csharp
for (int i = 0; i < arrayNumbers.GetLength(0); i++)
{
    Console.WriteLine($"arrayNumbers[{i}]: {arrayNumbers[i]}");
}
```
### 🔸 con while
```csharp
int count = 0;
while (count < arrayNumbers.GetLength(0))
{
    Console.WriteLine($"arrayNumbers[{count}]: {arrayNumbers[count]}");
    count++;
}
```
### 🔸 con foreach
```csharp
int index = 0;
foreach (int number in arrayNumbers)
{
    Console.WriteLine($"arrayNumbers[{index}]: {number}");
    index++;
}
```

### 🔸 Arrays multidimensionales (matrices)

Una matriz tiene varias dimensiones (por ejemplo, filas y columnas).

```csharp
int[,] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};

Console.WriteLine(matrix[0, 1]);

Console.WriteLine($"matrix.Length: {matrix.Length}");      // Número total de elementos
Console.WriteLine($"matrix.GetLength(0): {matrix.GetLength(0)}"); // Número de filas
Console.WriteLine($"matrix.GetLength(1): {matrix.GetLength(1)}"); // Número de columnas
```

### 🔁 Buscar en array
### 🔸 con for
```csharp
int numberToFind = 3;
bool found = false;
for (int t = 0; t < arrayNumbers.GetLength(0) && !found; t++)
{
    if (arrayNumbers[t] == 3) Console.WriteLine($"Element {numberToFind} found at index: {t}");
}
```
### 🔸 con while
```csharp
int q = 0;
found = false;
while (q < arrayNumbers.GetLength(0) && !found)
{
    if (arrayNumbers[q] == 3)
    {
        found = true;
    }
    else
    {
        q++;
    }

}
Console.WriteLine(found ? $"Element {numberToFind} found at index: {q}" : $"Element {numberToFind} not found.");
```
### 🔁 Ordenación BubbleSort
```csharp
int[] bubbleArray = { -2, 45, 3, 11, -9 };

//Show the original array
Console.WriteLine("Original array:");
foreach (int bubble in bubbleArray)
{
    Console.Write($"{bubble} ");
}

//First loop to compare until the penultimate number (length -2)
for (int s = 0; s <= bubbleArray.GetLength(0) - 2; s++)
{
    //Second loop to compare each element with the next one
    for (int r = 0; r <= bubbleArray.GetLength(0) - 2; r++)
    {
        //If the current element is greater than the next one, swap them
        if (bubbleArray[r] > bubbleArray[r + 1])
        {
            //Auxiliary variable to perform the swap
            int aux = bubbleArray[r + 1];
            //Assin the value of the current element to the next position
            bubbleArray[r + 1] = bubbleArray[r];
            //Assign the value of the auxiliary variable to the current position
            bubbleArray[r] = aux;
        }
    }
}
Console.WriteLine(" ");
Console.WriteLine("Sort array:");
foreach (int bubble in bubbleArray)
{
    Console.Write($"{bubble} ");
}
```
### 🔁 Matrices
```csharp
//Declaration of a 2D array (matrix) with initialization
const int ROWS = 2;
const int COLS = 3;
int[,] matrix = new int[ROWS, COLS];
int[,] matrixTwo = { { 1, 1, 1 }, { 2, 2, 2 } };
int[,] matrixThree = new int[,] { { 1, 2, 3 }, { 1, 2, 3 } };

//Assign values to the matrix
matrix[0, 0] = 1;
matrix[0, 1] = 2;
matrix[0, 2] = 3;
matrix[1, 0] = 4;
matrix[1, 1] = 5;
matrix[1, 2] = 6;

//Get the length of the matrix (number of elements)
Console.WriteLine($"The length of matrix is (total elements): {matrix.Length}");
// Alternative way to get the length of concrete dimension (for multi-dimensional arrays 0 - First dimension, 1 - second dimension, 2 - third dimension)
Console.WriteLine($"The rows length of matrix in the first dimension is: {matrix.GetLength(0)}");
Console.WriteLine($"The cols length of matrix in the second dimension is: {matrix.GetLength(1)}");
```
### 🔁 Recorrer matrices
### 🔸 con for
```csharp
for (int i = 0; i < matrix.GetLength(0); i++)
{
    for (int j = 0; j < matrix.GetLength(1); j++)
    {
        Console.WriteLine($"matrix[{i},{j}]: {matrix[i, j]}");
    }
}

```
### 🔸 con while
```csharp
int rows = 0, cols;

while (rows < matrix.GetLength(0))
{
    cols = 0;
    while (cols < matrix.GetLength(1))
    {
        Console.WriteLine($"matrix[{rows},{cols}]: {matrix[rows, cols]}");
        cols++;
    }
    rows++;
}
```
### 🔸 con foreach
```csharp
int indexMatrix = 0;
Console.Write("matrix values: ");
foreach (int number in matrix)
{
    Console.Write($"{number} ");

    indexMatrix++;
}
```
## 🧩 Jagged Arrays (Arrays Irregulares)
Un jagged array es un array de arrays.
Cada "fila" puede tener una longitud diferente.
```csharp
//Declaration of a jagged array (array of arrays)

/* Declaration with 3 rows but without columns
 * Example: A library with 3 shelves (rows) but we don't know how many books (columns) each shelf will have
 */
int[][] listOfBooks = new int[3][];
listOfBooks[0] = new int[2] { 1, 2 }; // First shelf with 2 books
listOfBooks[1] = new int[3] { 3, 4, 5 }; // Second shelf with 3 books
listOfBooks[2] = new int[1]; //Manually declare the size of the third shelf
listOfBooks[2] = new int[] { 6 }; // Third shelf with 1 book


//Example: A library with 3 shelves (rows) and different number of books (columns) on each shelf

//Declaration and initialization in a single line (Direct method)
int[][] listOfBooksTwo = new int[][]
{
    new int[] { 1, 2 },
    new int[] { 2, 3, 3, 3, 3 },
    new int[] { 3 }
};
/*Declaration and initialization in a single line (Short-hand method)
 */
int[][] listOfBooksThree = {
    new int[] { 1, 2 },
    new int[] { 2, 3, 3, 3, 3 },
    new int[] { 3 }
};
```
### 🔁 Recorrer Jagged Arrays

### 🔸 con for
```csharp
for (int i = 0; i < listOfBooks.Length; i++)
{
    for (int j = 0; j < listOfBooks[i].Length; j++)
    {
        Console.WriteLine($"listOfBooks[{i}][{j}]: {listOfBooks[i][j]}");
    }
}
```
### 🔸 con while
```csharp
rows = 0;
while (rows < listOfBooks.Length)
{
    cols = 0;
    while(cols < listOfBooks[rows].Length)
    {
        Console.WriteLine($"listOfBooks[{rows}][{cols}]: {listOfBooks[rows][cols]}");
        cols++;
    }
    rows++;
}
```
### 🔸 con foreach
```csharp
int row = 0;
foreach(int[] shelf in listOfBooks)
{
    Console.WriteLine($"shelf {row}");

    foreach(int book in shelf)
    {
        Console.WriteLine($"\tBook: {book} ");
    }
    row++;
    Console.WriteLine(" ");
}
```
