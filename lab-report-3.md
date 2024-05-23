# Part 1: Bugs

# 1. Buggy code

```java
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

# Test that fails buggy code

```java
@Test
public void testReversedFail(){
	int[] arrayToReverse = {1, 2, 3};
	int[] expectedArray = {3, 2, 1};
	assertArrayEquals(expectedArray, ArrayExamples.reversed(arrayToReverse));
}
```

# 2. Test that passes buggy code

```java
@Test
public void testReversedPass(){
	int[] arrayToReverse = {0, 0};
	int[] expectedArray = {0, 0};
	assertArrayEquals(expectedArray, ArrayExamples.reversed(arrayToReverse));
}
```

# 3. Symptom as output of running two tests

![screenshot of output in cmd line](https://cdn.discordapp.com/attachments/1065014704986128404/1238037692168802314/Untitled1.png?ex=663dd3f3&is=663c8273&hm=fde2b31473f7a07ba054b9d12a66ef2bc338459f9be40c038c060e319145919e&)
# 4. Bug before:

```java
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

# Bug after:

```java
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for (int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```

# 5. Explanation of bug fix

The original issue was that the method would return an array where each element was zero. This was because it assigned every element of `arr` to be an element of a `new int[]` array, which would have elements of 0. I fixed this by setting the `new` array to be equal to the corresponding elements of `arr` in reverse order. 

# Part 2: Researching commands: `grep`

## `grep -l`

```
merlin@Merlins-MacBook-Air 911report % grep -l his chapter-1.txt chapter-5.txt
chapter-1.txt
chapter-5.txt
merlin@Merlins-MacBook-Air 911report % 
```

`grep -l` shows both `chapter-5.txt` and `chapter-1.txt`, which means both of these files contain the word `his`.

The special thing about `grep -l` is that it suppresses normal grep output and only prints the name of each input file from, which is useful if you only need the filenames of those that contain the word you are looking for.

```
merlin@Merlins-MacBook-Air 911report % grep -l strategy chapter-1.txt chapter-5.txt chapter-12.txt 
chapter-12.txt
merlin@Merlins-MacBook-Air 911report % 
```

I used `grep -l` again, but to search for the word strategy in three files: `chapter-5.txt, chapter-1.txt, chapter12.txt`. 

Only `chapter12.txt` contains the word strategy, so `chapter-12.txt` is printed, which can be helpful to pipe filenames as arguments for another command.

## `grep -r`

```
merlin@Merlins-MacBook-Air technical % grep -r 1600
./government/Media/Greedy_Generous.txt:lawyers, the more than 1600 associates who donated to
./plos/journal.pbio.0020439.txt:        studied medicine in Padua (1600–1602, while Galileo was active there), it was believed that
./biomed/1471-2350-4-3.txt:          IgG 700 - 1600 mg/dL; IgG 
./biomed/1471-2202-4-17.txt:            (1:1600) overnight at 4°C and visualized as described
./biomed/1471-2164-4-21.txt:          (heterozygous NA16028 and homozygous NA16000). Other
./biomed/1472-6793-2-16.txt:          200, 400, 600, 800, 1000, 1200, 1400, 1600, 1800, and
./biomed/1471-2180-3-13.txt:          sequence as a probe. Position 1600321 of the 
./biomed/cc1852.txt:          and photographed at a window width of 1600 Hounsfield
./biomed/ar429.txt:          described [ 20 ] . The OD value obtained for the 1:1600
./biomed/1475-9268-1-2.txt:          [Gibco No. 16000-036]; penicillin-streptomycin [10,000
./911report/chapter-12.txt:                1600), the proposed National Preparedness Standard establishes a common set of
merlin@Merlins-MacBook-Air technical % 

```

Here, I used `grep -r` to recursively search for for the term `1600` in each subdirectory and file of my working directory, docsearch. This is useful for searching for a term by looking through every file in the directory, including those in its subdirectories.

```
merlin@Merlins-MacBook-Air Alcohol_Problems % grep -r administered
./Session2-PDF.txt:self-administered. An ideal screening test should not interfere
./Session2-PDF.txt:MAST has been self-administered and used in a computer format. It
./Session2-PDF.txt:of being self-administered, and it has also been administered in a
./Session2-PDF.txt:studied when administered as a stand-alone test.35
./Session2-PDF.txt:less information. Computer-administered or self-administered
./Session2-PDF.txt:(e.g., interview, self-administered forms, and computer
./Session2-PDF.txt:isolation and against other tests. A longer, self-administered
./Session2-PDF.txt:screen-including one administered by computer-should also be tested
./Session2-PDF.txt:effective. Self-administered questionnaires, computer screen
./Session2-PDF.txt:28. Selzer M, Vinokur A, van Rooijen M. A self-administered
./Session2-PDF.txt:computer-administered formats. Alcohol Clin Exp Res
./Session4-PDF.txt:administered on the advice of a physician." Thirty-eight states
merlin@Merlins-MacBook-Air Alcohol_Problems % 

```

In this example, I used `grep -r` inside of a much smaller directory, `docsearch/technical/government/Alcohol_Problems`. This is useful for quickly finding every instance of a term in a directory.

## `grep -c`

```
merlin@Merlins-MacBook-Air 911report % grep -c church chapter-13.3.txt 
2
merlin@Merlins-MacBook-Air 911report % 
```

Using `grep -c`I printed the total number of lines containing the word church in the file `chapter13-3.txt` in the directory docsearch/technical/911report. This is useful for knowing the number of occurrences of a term in a file.

```
merlin@Merlins-MacBook-Air Post_Rate_Comm % grep -c mail Redacted_Study.txt    
80
merlin@Merlins-MacBook-Air Post_Rate_Comm % 
```

I used `grep -c` on the file `docsearch/technical/government/Post_Rate_CommRedacted_Study.txt`. According to the output, there are 80 total lines that contain a match for the word mail in `Redacted_Study.txt`, which can be helpful to know if I need to find which file contains the most instance of a word.

## `grep -A num`

```
merlin@Merlins-MacBook-Air biomed % grep -A 3 luciferase  rr172.txt
          Transfection with NFκB-luciferase reporter
          constructs and assay for gene expression
          A549 cells were grown to 50-80% confluence on 12-well
          plates and transfected with the Mercury pathway profiling
--
          lysis buffer as supplied in the luciferase assay kit from
          Clontech, scraped from the wells and centrifuged 1 min at
          12,000 × 
          g. Aliquots of 20 μl of each lysate
--
          transcriptional activation of luciferase reporter
          construct
          CSC appears to activate NFκB, which should result in
          transcriptional activation of NFκB-inducible genes.
          Therefore, A549 cells were transfected with a luciferase
          reporter plasmid containing a promoter sequence that
          bound NFκB and luciferase activity was measured after
          challenge with CSC. Treatment with 0.4 μg/ml CSC for 30
          min resulted in significant enhancement of luciferase
          reporter expression compared to control (Fig. 4C),
          indicating activation of NFκB. TNF-α used as a positive
          control also activated luciferase gene expression with
          the same plasmid system. Exposure of cells transfected
          with the reporter plasmid to increasing doses of CSC
          showed NFκB expression peaking at a CSC concentration
--
        supplied in the luciferase assay kit from Clontech, scraped
        from the wells and centrifuged 1 min at 12,000 × 
        g. Aliquots of 20 μl of each lysate
        were transferred to flat-bottomed, white microtiter plates

```

I used `grep -A 3 surcharge Redacted_Study.txt`to print the line containing the pattern I was searching for, surcharge, plus the next three lines that are after the line containing the pattern. This can be helpful to find the context of what you are trying to find in a file.

```
merlin@Merlins-MacBook-Air biomed % grep -A 1 bovine  rr172.txt
          USA). Fetal bovine serum was from Atlanta Biochemicals
          (Atlanta, GA, USA). The culture medium (BEGM), growth
--
          bovine serum, 100 U/ml penicillin, 100 U/ml streptomycin,
          and 250 ng/ml amphotericin-B in an atmosphere of 5%
merlin@Merlins-MacBook-Air biomed % 

```

This time, `grep -A 1 bovine rr172.txt` printed out every occurrence of the word bovine in the file `rr172.txt` plus one additional line from the file after the line containing the word. This can be useful for finding what phrases commonly accompany your search pattern in your files.
