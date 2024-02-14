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

![Image](arraytestsSS.png)

### Program before Fix:

```

static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}

```

### Program after Fix:

```

  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }

```

### Explanation:

The fix in this code works as originally, the argument array was being altered with values from the new array being made earlier in the method. Due to this, the argument array would be returned with all of its values being 0, as it copies from a new array with all of its values being 0 and having the same length as the argument array. With the fix, instead of the argument array being returned, the new array as returned and is being altered with the argument array's values, copying over those values to the new array (through `newArray[i] = arr[arr.length - i - 1]`, newArray's value at i would be set to arr's value at the opposite index, ex. the values at indices 1 and 4 switch values) such that the values would be arranged where it would be in the reversed order of the original argument array as intended.

## Part 2:
## Researching Commands:

For my command, I decided to research the `find` command. Some of the command options involved being able to find directories within a directory by using the path/argument `-type d` with the find command, finding files based on how old they are with the path `-mtime [+/-(time in days)]`, looking for files that are older than a certain time or made within a certain time span (ex. within the last week), as well as finding files based on what they have (ex. all text files that contain the String value "Birds") by simply using the criteria/what you're looking for with the path `-(contents)`. The `find` command can also be used to find empty files with the path. (Source: [https://www.redhat.com/sysadmin/linux-find-command#:~:text=10%20ways%20to%20use%20the%20Linux%20find%20command,8%208.%20Find%20empty%20files%20...%20More%20items][https://www.redhat.com/sysadmin/linux-find-command#:~:text=10%20ways%20to%20use%20the%20Linux%20find%20command,8%208.%20Find%20empty%20files%20...%20More%20items])
