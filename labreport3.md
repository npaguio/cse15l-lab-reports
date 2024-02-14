# Nathan Paguio - Lab Report 3

## Part 1:

### Failure-inducing Input:

```
@Test
public void testReversed4(){
  int[] arr = new int[]{10, 20, 30, 40, 50};
  assertArrayEquals(new int[]{50, 40, 30, 20, 10}, ArrayExamples.reversed(arr);
}

```

### Input that doesn't induce a Failure:

```

@Test
public void testReversed5{
  int[] arr = new int[]{0};
  assertArrayEquals(new int[]{0}, ArrayExamples.reversed(arr);
}

```

### Symptom:

![Image][arraytestsSS.png]

### Program before Fix:
