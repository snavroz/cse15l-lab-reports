# Lab Report 3

## Part 1 - Bugs
* Failure Inducing Input:
```
  @Test
  public void testReverseInPlaceTwo() {
    int[] input1 = {2, 5};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 5, 2 }, input1);
  }
```
The failure inducing input here is the array [2,5].

* Input that does not induce failure:
```
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 7 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 7 }, input1);
	}
```
The input here that does not induce failure is the array [7].

* Symptom:
![Image](symptom.png)

* Bug Fix
Before:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

After:
```
  static void reverseInPlace(int[] arr) {
    int[] tempArr = Arrays.copyOf(arr, arr.length);
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = tempArr[arr.length - i - 1];
    }
  }
```

* Explanation: In order to fix this bug I needed to make a copy of the original array that holds the same values as that array because before, the array was setting the reversed values from the values of itself, so the values would be changed by the time the index got there.

## Part 2 - Researching Commands

### We will be focusing on the options for the **grep** command.

* `-n` option
  1. `grep -n "trials" technical/biomed/1468-6708-3-3.txt`
      Output: ```
11:        disease. These trials found that when compared with
19:        these trials did not assess the effect of lipid-lowering
89:        prevention trials, the benefit of statin therapy was not
95:        prevention statin trials had excluded patients with
149:        Nevertheless, a number of trials have established the
153:        recent trials have suggested that higher risk patients with
259:        and the A-2-Z trials, this study will not assess the
268:        trials will be carried out in this area. Future secondary```

    The -n option for the grep command prints out all of the lines of the given file with the given string argument, "trials" in this case, and includes the line number for each line. This is useful if you want to see the line number and contents of the line at the same time.
  2. `grep -n "Arizona" technical/911report/*.txt`
      Output:
      ![Image](grepn.png)
    The -n option prints out all of the lines with the given string in each txt file in the 911report directory with the corresponding line number before each line. In this case it's useful if you want to see every line and line number in a directory that contains the specific string. 

* `-l` option
  1. `grep -l "chicken" technical/biomed/1468-6708-3-3.txt`
      Output: `NONE`

    The -l prints out which files of the given files contains the string or pattern given which is "chicken" in this case and there is only file given as an argument in this case. The file given does not contain the "chicken" string, so no files are printed.
  2. `grep -n "Arizona" technical/911report/*.txt`
      Output:
      ![Image](grepn.png)
    The -n option
  
