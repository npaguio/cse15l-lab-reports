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

For my command, I decided to research the `find` command. Some of the command options involved being able to find directories within a directory by using the path/argument `-type d` with the find command, finding files based on how old they are with the path `-mtime [+/-(time in days)]`, looking for files that are older than a certain time or made within a certain time span (ex. within the last week), as well as finding a file based on name by using `-name` with the `find command`. The `find` command can also be used to find empty files with the path. (Source: [https://www.redhat.com/sysadmin/linux-find-command#:~:text=10%20ways%20to%20use%20the%20Linux%20find%20command,8%208.%20Find%20empty%20files%20...%20More%20items])

- Disclaimer: I had found my source after looking up "alternate ways to use the find command" online, as typing in "find command-line java" had directed me to websites teaching about command lines and arguments in Java.
  
![Image][searchCommands.png]

### Finding Directories with `find`:
```
aweso@DESKTOP-BNMJGSL MINGW64 ~/Documents/GitHub/docsearch/technical (main)
$ find -type d
.
./911report
./biomed
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm
./plos
```
### Source: [https://www.redhat.com/sysadmin/linux-find-command#:~:text=10%20ways%20to%20use%20the%20Linux%20find%20command,8%208.%20Find%20empty%20files%20...%20More%20items]
Here, using `-type d` with the `find` command allows for users to look for directories within their working directory. This is very useful as it allows for people to look at what directories are in their working directory, pointing out directories within that directory to look into in case they were looking for a specific file or needed to change their directory.


```
aweso@DESKTOP-BNMJGSL MINGW64 ~/Documents/GitHub/docsearch/technical (main)
$ find ./government -type d
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm
```
Source: [https://www.redhat.com/sysadmin/linux-find-command#:~:text=10%20ways%20to%20use%20the%20Linux%20find%20command,8%208.%20Find%20empty%20files%20...%20More%20items]
Similarly to the previous example, using `-type d` with the find command allows for users to search for directories within a specific directory they're curious about or looking into, as certain directories may contain files that the user may want to access, so the user would want to change their working directory to a directory within the given results.

### Finding Empty Files with the `find` Command:
```
aweso@DESKTOP-BNMJGSL MINGW64 ~/Documents/GitHub/docsearch/technical (main)
$ find -type f -empty
./911report/empty.txt
```
Source: [https://www.redhat.com/sysadmin/linux-find-command#:~:text=10%20ways%20to%20use%20the%20Linux%20find%20command,8%208.%20Find%20empty%20files%20...%20More%20items]
With the `find` command and using the path `-type f -empty`, users can search for files in their current directory that have nothing inside them. This could be useful for when someone needs to remove files that may be taking up storage space, or if they're debugging as results or other contents were not printed into a specific file like they wanted.

```
aweso@DESKTOP-BNMJGSL MINGW64 ~/Documents/GitHub/docsearch/technical (main)
$ find ./plos -type f -empty

```
Source: [https://www.redhat.com/sysadmin/linux-find-command#:~:text=10%20ways%20to%20use%20the%20Linux%20find%20command,8%208.%20Find%20empty%20files%20...%20More%20items]
Also by using the `find` command to look for empty files, users can use this feature of the command to see if their code worked properly and if a String or algorithm was added to an empty file. By seeing if a directory is not empty at all, users can ensure that their code works or that all of their files are not empty at all.

## Finding Files with the `find` Command Based on File Type:
```
aweso@DESKTOP-BNMJGSL MINGW64 ~/Documents/GitHub/docsearch (main)
$ find technical/911report/*.txt
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911report/chapter-12.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-2.txt
technical/911report/chapter-3.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-8.txt
technical/911report/chapter-9.txt
technical/911report/empty.txt
technical/911report/preface.txt

```
Source: [https://www.redhat.com/sysadmin/linux-find-command#:~:text=10%20ways%20to%20use%20the%20Linux%20find%20command,8%208.%20Find%20empty%20files%20...%20More%20items]
Through the use of the `find` command to find files based on their file type, like `.Java` or `.txt` files, users can quickly find specific files in large directories, helping narrow down the amount of files to look through. For example, a directory could contain lots of files, like student `.Java` file submissions, `.png` files, and `.md` files, but the user is looking for error logs and descriptions which are in `.txt` format. Using the `find` command like in the embedded code above allows for users to find these files quickly instead of spending minutes navigating through a large directory.

```
aweso@DESKTOP-BNMJGSL MINGW64 ~/Documents/GitHub/docsearch (main)
$ find *.java
DocSearchServer.java
Server.java
TestDocSearch.java
```
Source: [https://www.redhat.com/sysadmin/linux-find-command#:~:text=10%20ways%20to%20use%20the%20Linux%20find%20command,8%208.%20Find%20empty%20files%20...%20More%20items]\
By searching for `.Java` files with the `find` command, users can look for files related to their projects while in a workspace, look for student submissions in the case of grading, or get a list of all the `.Java` files in a directory.
