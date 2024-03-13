# Nathan Paguio - Lab Report 5

## Part 1:

#### Mark Grayson (Student): So I've been having a problem with my `NumPattern.java` code and I don't know why it's failing. I've looked over the code a few times after forking it but I probably can't think at the moment, I sent a screenshot of my symptom below. Looking at it, I believe that I'm not adding the right number values to my `List<Integer>` object that's being returned, following a different pattern to what I expected.

![Image](ArraySymptom.png)

#### Barry Wilson (TA): Alright, looking at your symptom, try seeing if there are any mistakes in what's being added to the return array. Hope that helps!

#### Mark Grayson (Student): I tried that and saw that I wasn't updating one of my variables properly, so instead of adding the next integer that's supposed to be in the array, my method would just follow the pattern of adding 2 or 4 to the first element, being the same 2 numbers aside from the original number. In this case, my number pattern array was `{1, 3, 5, 3, 5}` instead of `{1, 3, 7, 9, 13}`. Here's a screenshot of the test working in my terminal, thank you so much for helping me out!

![Image](ProperOutput.png)

### Setup Information:
The files used were `NumPattern.java`, `NumPatternTests.java`, and a `test.sh` file that compiled what was necessary to use `NumPatternTests.java` (ex. JUnit, `NumPatternTests.java` itself). The directory was `Downloads/labreport5code/lab5report`.

### File Contents Before Bug Fix:
`NumPattern.java`:
```
import java.util.ArrayList;
import java.util.List;

class NumPattern {

  static List<Integer> pingPongPattern(Integer base) {
    List<Integer> result = new ArrayList<Integer>();
    result.add(base);
    for(int i = 1; i < 5; i++){
      if(i%2 != 0){
        result.add(base + 2);
      }
      if(i%2 == 0){
        result.add(base + 4);
      }
    }
    return result;
  }

}

```
`NumPatternTests.java`:
```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.*;


public class NumPatternTests {
	@Test(timeout = 500)
	public void testPingPongPattern() {
		List<Integer> exp = new ArrayList<Integer>();
		exp.add(1);
		exp.add(3);
		exp.add(7);
		exp.add(9);
		exp.add(13);
		assertArrayEquals(exp.toArray(), NumPattern.pingPongPattern(1).toArray());
	}

}

```
`test.sh`:
```
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore NumPatternTests
```
### Fixing the Bug:
 `NumPatternTests.java` and `test.sh` were not edited at all when fixing the bug, but lines 11 and 14 of `NumPattern.java` were the lines that triggered the bug when `bash test.sh` was entered into the terminal, where the test would fail in line 15 of `NumPatternTests.java` as the `pingPongPattern()` method would not produce the expected array of `{1, 3, 7, 9, 13}`. What I did was edit lines 11 and 15 of `NumPattern.java` such that the argument integer, `base`, would be added upon based on `i`'s value in the for loop, such that odd indices would contain the sum of the previous number plus 2, while even indices (0 excluded) would be contain the sum of the previous number plus 4. In this code, `base` would not be altered at all, with the same 2 numbers (either the sum of `base` and 2 or the sum of `base` and 4) being in the `result` array after the element at index 0, which is `base`.
 
## Part 2:
Honestly, I really enjoyed learning about the `git` commands such as `git push` and `git commit`, along with the use of `vim`. I feel like these are going to be very important in the future with projects or quick edits to any of my work. When I hear about updating code, I usually think that it would all be saved on my computer via VSCode or it would be saved automatically as I kept coding in an online workspace like Edstem, similar to how my typing on my file would be saved automatically on it in Google Docs. With the `git` commands, I can basically push out my code to my GitHub repository which is great and saves me lots of time where I don't need to copy and paste my new edits into the same file in GitHub, or delete the file in GitHub and reupload it with the new edits, as I can just use `git commit` and `git push` instead. `vim` basically allows me to edit my files in my terminal instead of having to click off to my workspace/another window in VSCode, so with `vim` having shortcuts like finding the first/last instance of an appearance in my code (ex. a variable name, string, operator, etc.), I have another option to edit my files, so in situations where I need to act quick or only work inside a terminal, `vim` is amazing for that. I really think I learned a good amount of skills from the later part of this course that can help me improve my productivity in the future when programming, and I can't wait to have more fun using these commands and toying around with code like the lab sessions in this class.
