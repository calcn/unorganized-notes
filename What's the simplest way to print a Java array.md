Since Java 5 you can use Arrays.toString(arr) or Arrays.deepToString(arr) for arrays within arrays. Note that the Object[] version calls .toString() on each object in the array. The output is even decorated in the exact way you're asking.

## Simple Array

```
String[] array = new String[] {"John", "Mary", "Bob"};
System.out.println(Arrays.toString(array));
```

Output:

```
[John, Mary, Bob]
```

## Nested Array

```
String[][] deepArray = new String[][] {{"John", "Mary"}, {"Alice", "Bob"}};
System.out.println(Arrays.toString(deepArray));
//output: [[Ljava.lang.String;@106d69c, [Ljava.lang.String;@52e922]
System.out.println(Arrays.deepToString(deepArray));
```

Output:

```
[[John, Mary], [Alice, Bob]]
```

## double Array

```
double[] doubleArray = { 7.0, 9.0, 5.0, 1.0, 3.0 };
System.out.println(Arrays.toString(doubleArray));
```

Output:

```
[7.0, 9.0, 5.0, 1.0, 3.0 ]
```

## int Array
```
int[] intArray = { 7, 9, 5, 1, 3 };
System.out.println(Arrays.toString(intArray));
```

Output:

```
[7, 9, 5, 1, 3 ]
```