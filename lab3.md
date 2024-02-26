# Part 1
## A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)
```
@Test
  public void testReversed() {
    int[] input1 = {1,2,3};
    assertArrayEquals(new int[]{3,2,1}, ArrayExamples.reversed(input1));
  }
```


## An input that doesn't induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)
```
@Test
  public void testReversed2() {
    int[] input1 = {0,0,0};
    assertArrayEquals(new int[]{0,0,0}, ArrayExamples.reversed(input1));
  }
```


## The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)
*failutre-inducing input*
```
JUnit version 4.13.2
.E
Time: 0.01
There was 1 failure:
1) testReversed(ArrayTests)
arrays first differed at element [0]; expected:<3> but was:<0>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReversed(ArrayTests.java:16)
        ... 32 trimmed
Caused by: java.lang.AssertionError: expected:<3> but was:<0>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 38 more
```
*no failure input*
```
JUnit version 4.13.2
.
Time: 0.009

OK (1 test)
```


## The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)
*Before*
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
*After*
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1]; //HAVE TO SWITCH ASSIGNMENTS!! 
    }
    return newArray;
  }
```
* Before, the code was assigning elements from the newly created array to the original array, not the other way around. The original method was not changing `newArray` and instead replacing every index in `arr` with a 0 and returning `arr` instead of `newArray`. 

# Part 2

`grep`: searches a file for a specific pattern 
* SYNTAX: `grep [options] pattern [files]`

1.  `l` --> List the names of files that have at least one match of the specified pattern. This opition is helpful, especially when dealing with many files, because it quickly identifies the desired pattern across many files without overwhelming the user with alot of information like the specific lines in the file it matched with.

* This command prints out the files in which the string "Mensenchymal cells" is mentioned in all `.txt` files in the `biomed` directory. This allows for efficient searching. 
  * command: `grep -l "Mesenchymal cells" biomed/*.txt`
  * output:
  ```
  biomed/1471-213X-1-11.txt
  biomed/1477-7827-1-36.txt
  biomed/1477-7827-1-46.txt
  ```
* This command line searches for the string "JSTOR" within all `.txt` files in the `plos` directory and prints the file name(s) where the string is mentioned. Like the example above, this command allows for efficient searching, especially when dealing with a large number of files.
  * command: `grep -l "JSTOR" plos/*.txt`
  * output: `plos/journal.pbio.0020010.txt`

2.  `n` --> Prints on the matched lines with their respective line numbers. This is helpful because it creates a quick reference point for the location of the pattern, which makes searching and potentially debugging more efficient.

* This command searches for and prints out all the file names where the string "Mensenchymal cells" is found and will additionally output the line number within the file where the string is exactly found. This is one step more effiencet than `-l` since it gives more direction to where the key string is located. 
  * command: `grep -n "Mesenchymal cells" biomed/*.txt`
  * output:
  ```
  biomed/1471-213X-1-11.txt:92:          Mesenchymal cells
  biomed/1471-213X-1-11.txt:108:          Mesenchymal cells are present in the lamina propria
  biomed/1477-7827-1-36.txt:388:          the ERβ antibody (right column). Mesenchymal cells
  biomed/1477-7827-1-46.txt:559:          macrophages (see below). Mesenchymal cells in levator an
  ```
* This command searches for and prints out all the file names and the specific lines where the string "cancer" is mentioned in the `biomed` directory. The `i` performs a case-insensitive search when looking for matched lines.  It is really easy to mix up case when trying to search for something, so this command is beneficial. The output could include lines that have a variation of the word "cancer" including "Cancer" (with a capital C).
  * command: `grep -ni "cancer" biomed/*.txt`
  * output:  
  ```
  biomed/1468-6708-3-1.txt:133:          of arthritis, cancer, diabetes, fair or poor self-rated
  biomed/1468-6708-3-10.txt:359:          group were attributed to cancer, compared to 9% (6/70) in
  biomed/1468-6708-3-4.txt:308:          cancer history. Since no missing data would occur, the
  biomed/1471-2091-2-5.txt:39:        tumors taken from cancer patients [ 12]. In all of these
  biomed/1471-2091-3-14.txt:466:          67 ] . ProTα was shown as a marker for breast cancer [ 68
  biomed/1471-2091-3-14.txt:470:          prognosis of lung cancer [ 70 ] . In ligand blotting
  biomed/1471-2091-3-4.txt:71:        patients suffering from cancer, cystic fibrosis, drug
  biomed/1471-2105-3-24.txt:9:        cancer. For this to be the case, disease-associated amino
  biomed/1471-2105-3-24.txt:46:        20,000 entries) [ 2 ] and the National Cancer Institute's
  biomed/1471-2105-3-24.txt:47:        CGAP-GAI (Cancer Genome Anatomy Project Genetic Annotation
  biomed/1471-2105-3-24.txt:78:        cancer susceptibility gene, BRCA1, showed that
  biomed/1471-2105-3-24.txt:154:        website, http://cancer.stanford.edu/mut-paper/.
  biomed/1471-2105-3-26.txt:23:        cancer therapy. Successful application of array-based tools
  biomed/1471-2105-3-26.txt:28:        subsets of cancer [ 3 4 ] .
  biomed/1471-2105-3-4.txt:33:        particularly on cancer, have appeared [ 14 15 16 17 18 19 ]
  .... many other lines that I can't paste here because it would be too much!
  ```

3. `head` OR `tail` --> This option for the `grep` command limits the number of lines displayed in the output. `head` prints the first few lines, while `tail` displays the last few lines. This is useful when dealing with large outputs (perfect for this example), allowing someone to quickly preview the beginning or end of the results.

* This command searches for the string "cancer" case-insensitively (`-i` option) in all `.txt` files within the `biomed` directory and outputs the line number where it is referenced (`-n` option). The pipe symbol (`|`) redirects the output of one command as the input of another command. The `head` keyword is used to display the first 10 lines of the output by default. Adding the `head` keyword helps with making a quick assessment of where the string "cancer" is used. If the output size is large, this keyword helps with efficently analyzing some inital matches without getting overwhelmed.
  * command: `grep -ni "cancer" biomed/*.txt | head`
    * output: the first 10 lines
    ```
    biomed/1468-6708-3-1.txt:133:          of arthritis, cancer, diabetes, fair or poor self-rated
    biomed/1468-6708-3-10.txt:359:          group were attributed to cancer, compared to 9% (6/70) in
    biomed/1468-6708-3-4.txt:308:          cancer history. Since no missing data would occur, the
    biomed/1471-2091-2-5.txt:39:        tumors taken from cancer patients [ 12]. In all of these
    biomed/1471-2091-3-14.txt:466:          67 ] . ProTα was shown as a marker for breast cancer [ 68
    biomed/1471-2091-3-14.txt:470:          prognosis of lung cancer [ 70 ] . In ligand blotting
    biomed/1471-2091-3-4.txt:71:        patients suffering from cancer, cystic fibrosis, drug
    biomed/1471-2105-3-24.txt:9:        cancer. For this to be the case, disease-associated amino
    biomed/1471-2105-3-24.txt:46:        20,000 entries) [ 2 ] and the National Cancer Institute's
    biomed/1471-2105-3-24.txt:47:        CGAP-GAI (Cancer Genome Anatomy Project Genetic Annotation
    ```
* This command searching for the string "cancer" in all `.txt` files within the `biomed` directory. The command will only output the last 15 lines because the keyword `tail` allows the user to see the tail end of the output. Adding `-n 15` to tail specifies that you want to display the last 15 lines of the output. This command allows for more control over the size of your output and making searching more efficient and less overwhelming.
  * command: `grep "cancer" biomed/*.txt | tail -n 15`
  * output:
  ```
  biomed/gb-2003-4-7-r46.txt:          tumors. Other disease-related terms include 'Precancerous
  biomed/gb-2003-4-7-r46.txt:          to regulate self-renewal in stem cells and cancer cells,
  biomed/gb-2003-4-7-r46.txt:          more in common from one cancer to the next, processes of
  biomed/gb-2003-4-7-r46.txt:          placed in comparable tissue environments, cancer cells
  biomed/gb-2003-4-7-r46.txt:        of host factors. The ability of cancer cells to proliferate
  biomed/gb-2003-4-7-r46.txt:        of cancer [ 11 ] . To stimulate their own growth and
  biomed/gb-2003-4-7-r46.txt:        In terms of new biological insight into cancer
  biomed/gb-2003-4-7-r46.txt:        development, our findings suggest that cancer cells of
  biomed/gb-2003-4-7-r46.txt:        cancer. This conclusion is based on the significant
  biomed/gb-2003-4-7-r46.txt:        of cancer cells to the increased expression may be
  biomed/gb-2003-4-7-r46.txt:        the cancerous cells in the tumor tissue. This conclusion is
  biomed/gb-2003-4-7-r46.txt:        ECM signaling pathways are active in different cancers,
  biomed/gb-2003-4-7-r46.txt:        the specific pathways dysregulated in a particular cancer
  biomed/gb-2003-4-7-r46.txt:        cancers 
  biomed/gb-2003-4-7-r46.txt:        cancers, including 
  ```
4. 
---
  ## Sources: 
  * [GeeksForGeeks](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)
    * for commands `l`, `n`, `i`
  * ChatGPT
    * for the `head` and `tail` options.
    * I asked the AI, "what commands can we use in Linux to display the first/last few lines." This is the output that I received:
  
    ```
    head: This command is used to display the first few lines of a file.
    Example: head filename.txt
    By default, head displays the first 10 lines. You can specify the number of lines using the -n option.
    For example, head -n 20   filename.txt will display the first 20 lines.
    ```
    ```
    tail: This command is used to display the last few lines of a file.
    Example: tail filename.txt
    By default, tail displays the last 10 lines. You can specify the number of lines using the -n option.
    For example, tail -n 20     filename.txt will display the last 20 lines.
    ```
