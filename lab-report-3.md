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

# Part 2: Researching commands

## `grep`

1. `grep` with | pipes output of command through `grep`. It can use `grep` as a filter for the output.
    1. Example 1: In this example, I piped the output of `ls government/Gen_Account_Office` to `grep` and searched for `6.txt`. This is useful because I can use just one line to do a `grep` command to search from filesnames in a directory.
        
        ```java
        merlin@Merlins-MacBook-Air technical % ls government/Gen_Account_Office | grep 6.txt
        Sept27-2002_d02966.txt
        og96026.txt
        og96036.txt
        og97046.txt
        og98026.txt
        og98046.txt
        og99036.txt
        merlin@Merlins-MacBook-Air technical % 
        ```
        
    2. Example 2: In this example, I piped the output of `ls biomed` through `grep` and searched for `X-1`. This is useful because it can make it very simple to find files in any directory I want through the command line.
        
        ```java
        merlin@Merlins-MacBook-Air technical % ls biomed | grep X-1
        1471-213X-1-1.txt
        1471-213X-1-10.txt
        1471-213X-1-11.txt
        1471-213X-1-12.txt
        1471-213X-1-13.txt
        1471-213X-1-15.txt
        1471-213X-1-2.txt
        1471-213X-1-3.txt
        1471-213X-1-4.txt
        1471-213X-1-6.txt
        1471-213X-1-9.txt
        1471-230X-1-10.txt
        1471-230X-1-5.txt
        1471-230X-1-6.txt
        1471-230X-1-8.txt
        1472-684X-1-5.txt
        1476-069X-1-3.txt
        1476-511X-1-2.txt
        merlin@Merlins-MacBook-Air technical % 
        
        ```
        
2. `grep` can be used with a search term and file containing information
    1. Example 1: I used `grep` to find all instances of the word ‘most’ in the file `chapter-13.3.txt`. This is useful because I don’t have to go directly to the file and type cmd+f to find if a word is in that file.
    
    ```java
    merlin@Merlins-MacBook-Air technical % cd 911report
    merlin@Merlins-MacBook-Air 911report % grep most chapter-13.3.txt 
                    months after the invasion . . . almost the entire population of Kabul climbed on
                    Azzam, Apr. 18, 1997. By most accounts, Bin Ladin initially viewed Azzam as a
                    Iraq and al Qaeda regarding chemical weapons and explosives training, the most
                    Juan O. Tamayo,"Mix-Up Almost Permitted Deportation of Men Suspected of Terrorist
                    most economic and military assistance to Pakistan. Clinton administration officials
                162. Mike interview (Jan. 6, 2004). Maher told us he thinks it "almost impossible"
    merlin@Merlins-MacBook-Air 911report % 
    
    ```
    
    b. Example 2: I used `grep` to find all instances of the word `axis` in the file `1471-213X-1-2.txt`. This is useful because I could also redirect command line output into a text file for organization and use `grep` to find words in that text file easily.
    
    ```java
    merlin@Merlins-MacBook-Air biomed % grep axis 1471-213X-1-2.txt 
            along the dorsal-ventral axis [ 4]. All of these genes are
            anterior-posterior axis of 
              promoters in pBluescript with a Maxiscript kit (Ambion).
    merlin@Merlins-MacBook-Air biomed % 
    
    ```
    
3. `grep` with a caret at the start of a regular expression, such as  `“^g”`, searches for lines starting with the regular expression
    1. Example 1: I used `grep` to find all lines starting with `Alcohol` in `Session2-PDF.txt`. This is useful because I can filter `grep` specifically to only include my regular expression when it is at the start of a line.
        
        ```java
        merlin@Merlins-MacBook-Air Alcohol_Problems % grep '^Alcohol' Session2-PDF.txt 
        Alcohol problems defined
        Alcohol problems designate a spectrum from risk behavior to
        Alcohol concentration
        Alcohol Use Disorders Identification Test in screening trauma
        Alcohol Clin Exp Res 1987;11:269-73.
        Alcohol Use Disorders Identification Test in screening trauma
        Alcohol 1995;56:695-700.
        Alcoholism. Criteria for the diagnosis of alcoholism. Am J
        Alcohol. 1998;33:304-9.
        Alcohol Clin Exp Res 1998;22:892-6.
        Alcoholism screening in the elderly. J Am Geriatr Soc
        Alcohol Depend 1993;33:139-49.
        merlin@Merlins-MacBook-Air Alcohol_Problems % 
        
        ```
        
    2. Example 2: I used `grep` to find all lines starting with `be` in `Session4-PDF.txt`. This is useful because I could also do things like find lines that only start with a bullet point or only with a capital letter.
        
        ```java
        merlin@Merlins-MacBook-Air Alcohol_Problems % grep '^be' Session4-PDF.txt
        be needed to accomplish this goal. This paper describes the factors
        believe that screening was the responsibility of emergency
        believe that clinical judgment is reliable and formal screening is
        be provided to emergency department personnel on a priority basis
        because such funding will lead to their professional development,
        because peer-reviewers do not view alcohol-related research as
        being vital. There are equally formidable obstacles when attempting
        because surveys consistently show that a substantial number of
        be stigmatized. The laws are contained in the Code of Federal
        because their primary function is not to provide substance abuse
        been developed on the basis of evidence that treatment for
        be a suitable outcome for emergency physicians.
        be as important an outcome to ED staff as decreased re-visits to
        be a useful source of follow-up data, as can a simple phone call to
        merlin@Merlins-MacBook-Air Alcohol_Problems % 
        
        ```
        
4. `grep` + a regular expression with a dot ( . ) at the end like `‘an.’` to find any single series characters within any expression
    1. Example 1: I used `grep` to find all instances of the series of letters `par` in `journal.pbio.0020001.txt`. This is useful because not only do I find the word `par` alone, I also find words containing `par` like `partial`.
        
        ```java
        merlin@Merlins-MacBook-Air plos % grep 'par.' journal.pbio.0020001.txt 
                several scientists, who present overwhelming evidence for the disparity in scientific
                is a statistical bias on the part of the SCI as a bibliometric database, since it
                2001). But is the disparity in scientific contributions between the developed and
                focusing on the Americas as a case study. Not surprisingly, there was a huge disparity in
                1990 as a comparison, revealed that scientific publishing in Latin America increased the
                particularly from 1995 until 2000 (Figure 2).
                picked up by the SCI in relation to the number of scientists in a particular country, also
                productivity is remarkable when we compare it with the relatively low investment in science
                itself as compared with the GDP of Latin America as a whole. In fact, Albornoz (2001)
                effort compared with that of the United States (2.84%) and Canada (1.5%).
                performed particularly well. For example, Uruguay, Chile, Panama, and Cuba averaged,
                development investment in the 10 years studied, which is notoriously high compared with
                is that scientific development during the 1990s was particularly strong for many countries
                Latin America compared with the relatively flat increases in the United States and Canada,
                twice as many publications to journals in the second category (8% in the top 11–20 compared
                meetings for researchers in the developing compared with the developed world.
                benefit from the contributions of many disparate groups around the world, rather than being
                publications as a measure of scientific output, particularly if these publications can
        merlin@Merlins-MacBook-Air plos % 
        
        ```
        
    2. Example 2: I used `grep` to find every instance of the sequence of characters in `plac` in `journal.pbio.0020267.txt`. This is useful because I can use it to find suffixes or prefixes relevant to what I am searching for.
        
        ```java
        merlin@Merlins-MacBook-Air plos % grep 'plac.' journal.pbio.0020267.txt 
                therapist physically restrains his hands, placing them back on the tabletop until he stops
                in their brains—measured through a network of electrodes placed on the scalp—is similar
                places can result in a “freezer full of fish.” He also says that parent organizations keep
        merlin@Merlins-MacBook-Air plos % 
        
        ```
        

All commands for `grep` are from https://docs.oracle.com/cd/E19504-01/802-5826/6i9iclf5k/index.html
