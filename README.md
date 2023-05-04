Download Link: https://assignmentchef.com/product/solved-csci1300-1310-assignment-4-measuring-dna-similarity
<br>



Objectives:




<ol>

 <li>Apply the concept of program decomposition.</li>

 <li>Manipulate strings. Design functions in program construction that use pointers.</li>

</ol>

<strong> </strong>

DNA is the hereditary material in human and other species. Almost every cell in a person’s body has the same DNA. All information in a DNA is stored as a code in four chemical bases: adenine (A), guanine (G), cytosine (C) and thymine(T). Different order of these bases means different information.




One of the challenges in computational biology is determining what the codons in a DNA sequence represent. A codon is a sequence of three nucleotides that form a unit of genetic code in a DNA or RNA molecule.​ ​For example, given the sequence GGGA, the codon could be a GGG or a GGA, depending on where the gene begins and the active bases in the gene. Clues about how to interpret a DNA sequence can be found by comparing an unknown DNA sequence to a known sequence and measuring their similarity. If sequences are similar, then it can be hypothesized that they have similar functions and proteins.




Assignment Details:

In this assignment, you will develop a few functions for DNA analysis. These functions will calculate common measures of DNA similarity, such as the Hamming distance and the Best Match between two DNA sequences. Each of the DNA sequences you need for this assignment can be copied from this write-up and stored in a variable in your program. There is a sample DNA sequence for a mouse, human, and an unknown species. Your mission is to determine the identity of the unknown by comparing it to the human and the mouse. If the unknown species is more similar to the human than it is to the mouse, then you can conclude that the unknown sequence is from a human. Otherwise, you can conclude that the unknown is from a mouse.




​4

Your assignment needs to include at least the following functions for full credit:




void calculateSimilarity(double *similarity, string DNA1, string DNA2);




string calculateB​ estMatch(double *bestscore, int *index, string DNA1, string DNA2);




What to submit?

The assignment is set up in moodle. There are three code-runner questions. The first question is for the full code (directives, prototypes, definitions and main) to test for correctness. The other two questions will help for getting partial credit and they are for the functions cal​ culateSimilarity ​and ​ calculateBestMatch.  It is your responsibility to copy them from the full code into these individual questions. If you need any helper functions, then include them in the space provided but above the function that will make the call. If you are not sure, please ask the instructors before the deadline. Don’t forget that after the deadline, you have the right to request an interview with your TA to review your work.




Hamming distance and similarity between two strings

Hamming distance is one of the most common ways to measure the similarity between two strings of the same length. Hamming distance is a position-by-position comparison that counts the number of positions in which the corresponding characters in the string are different. Two strings with a small Hamming distance are more similar than two strings with a larger Hamming distance.




Example:

first string = “ACCT” second string = “ACCG”

A C C T

|   |   |  *

A C C G




In this example, there are three matching characters and one mismatch, so the Hamming distance is one.




The similarity score for two sequences is then calculated as follows:




similarity_score = (string length-hamming distance) / string length




similarity_score = (4-1)/4=3/4=0.75




Two sequences with a high similarity score are more similar than two sequences with a lower similarity score.




The Best Match algorithm extends the Hamming distance calculation by finding the best overlap of the two strings. For any two strings, calculate the Hamming distance between the string and substring starting at each position of the string.




<h2>calculateSimilarity(double*, string, string)</h2>

The calculateSimilarity()​ function should take two arguments that are both strings and a double pointer that stores the similarity between the strings. You can declare a double pointer just as you would an integer pointer:




double x;

double *dPtr = &amp;x;




The function should calculate the similarity score for the two strings and update the similarity with that score.




Note: when you test calculateSimilarity()​ , pass in strings where you can calculate the similarity by hand before passing it real data. That will help you identify errors in your algorithm.




<h2>calculateBestMatch(double*, int*, string, string)</h2>

The calculateBestMatch()​ function should take four arguments – one integer pointers and double pointer and two strings. The double pointers store the Similarity Score calculation and the integer pointer store the index in the string where the best match starts. The two string arguments are the two strings to compare. The second string argument is the substring to search for. The first string is the string you are searching.  This functions returns a string which is DNA sequence from the mouse/human DNA which best matches with the user entered sequence with a high similarity score.




Note: you will need to be aware of the end of each string to make sure that you don’t loop off the end of either string.




<h2>Functionality in main()</h2>

In your main()​ function, you will need to call the other functions you have written. You need to use the mouse and human DNA samples shown below in this write-up and unknown DNA sample just for testing your program.  Your first task is to ask the user to enter the unknown DNA sequence and store it in a variable. You should output the result of the function calls in the main()​ function. After calling calculateSimularity(), you need to output the identity of the unknown DNA sequence. <strong> </strong>







if the unknownDNA is more similar to the humanDNA  print “Human”

else if the unknownDNA is more similar to the mouseDNA  print “Mouse”

else unknownDNA is equally similar to both mouse and human print “Identity cannot be determined.”




Before calling calculateBestMatch(),​ you need to prompt the user for a search string. You need to compare the search string to the mouse DNA and Human DNA, you would do something like the following:




cout&lt;&lt;”Enter a substring:; getline(cin, subStr);

calculateBestMatch(&amp;similarityscore, &amp;index, mouseDNA, subStr);

calculateBestMatch(&amp;similarityscore, &amp;index, humanDNA, subStr);




After calling calculateBestMatch()​ , you need to display the DNA sequence that is the best match as well as the best similarity score. If there isn’t a match of any character, print “Match not ​ found.”




Here is the skeleton/high level code which you need to follow:




#include &lt;iostream&gt; #include &lt;string.h&gt;

using namespace std;




//Declare the humanDNA as const string &amp; initialize with the value mentioned in writeup  //Declare the mouseDNA as const string &amp; initialize with the value mentioned in writeup




//Declare the Function Headers




int main()

{

//Declare all the necessary variables needed for your program

​ cout&lt;&lt;“Enter an unknownDNA:”&lt;&lt;endl; ​  //ask the user to enter the unknowDNA

​  cin&gt;&gt; unknownDNA;




//Call the ​calculateSimilarity function to compare unknownDNA with humanDNA

//Call the calculateSimilarity function to compare unknownDNA with mouseDNA




//If the unknownDNA is more similar to the humanDNA  cout &lt;&lt; “Human” &lt;&lt;endl;

//Else If the unknownDNA is more similar to the mouseDNA  cout &lt;&lt; “Mouse” &lt;&lt;endl;

//Else unknownDNA is equally similar to both mouse and human

cout&lt;&lt; “Identity cannot be determined”&lt;&lt;endl;




cout&lt;&lt;“Enter a substring:”&lt;&lt;endl; /​ /Ask the user to enter a sequence   cin&gt;&gt; subStr;




//Pass the user entered sequence with humanDNA and mouseDNA to the

//calculateBestMatch function




calculateBestMatch(&amp;similarityscore, &amp;index, humanDNA, subStr);

//If a best match is found print in the below format

​  cout&lt;&lt; “The Best Match found in humanDNA is “&lt;&lt; bestsequence &lt;&lt; ” with a similarity score of ” &lt;&lt; similarityscore &lt;&lt;endl;

//else print

cout&lt;&lt;”Match not found”&lt;&lt;endl;




calculateBestMatch(&amp;similarityscore, &amp;index, mouseDNA, subStr);

//If a best match is found print in the below format

cout&lt;&lt; “The Best Match found in mouseDNA is “&lt;&lt; bestsequence &lt;&lt; ” with a similarity score of ” &lt;&lt; similarityscore &lt;&lt;endl;

//else print

cout&lt;&lt;”Match not found”&lt;&lt;endl; return 0;

}




<h2>Other helpful hints</h2>

Write the code without pointers first. Once you are confident that your algorithms are correct, modify your functions to use pointers.




<h2>DNA samples</h2>

Use the following human, mouse, and unknown DNA strings in your program.




humanDNA =

“CGCAAATTTGCCGGATTTCCTTTGCTGTTCCTGCATGTAGTTTAAACGAGATTGCCAG

CACCGGGTATCATTCACCATTTTTCTTTTCGTTAACTTGCCGTCAGCCTTTTCTTTGAC

CTCTTCTTTCTGTTCATGTGTATTTGCTGTCTCTTAGCCCAGACTTCCCGTGTCCTTTC

CACCGGGCCTTTGAGAGGTCACAGGGTCTTGATGCTGTGGTCTTCATCTGCAGGTGTCT

GACTTCCAGCAACTGCTGGCCTGTGCCAGGGTGCAGCTGAGCACTGGAGTGGAGTTTTC

CTGTGGAGAGGAGCCATGCCTAGAGTGGGATGGGCCATTGTTCATG”




mouseDNA =

“CGCAATTTTTACTTAATTCTTTTTCTTTTAATTCATATATTTTTAATATGTTTACTAT

TAATGGTTATCATTCACCATTTAACTATTTGTTATTTTGACGTCATTTTTTTCTATTTC

CTCTTTTTTCAATTCATGTTTATTTTCTGTATTTTTGTTAAGTTTTCACAAGTCTAATA

TAATTGTCCTTTGAGAGGTTATTTGGTCTATATTTTTTTTTCTTCATCTGTATTTTTAT

GATTTCATTTAATTGATTTTCATTGACAGGGTTCTGCTGTGTTCTGGATTGTATTTTTC

TTGTGGAGAGGAACTATTTCTTGAGTGGGATGTACCTTTGTTCTTG”




unknownDNA =

“CGCATTTTTGCCGGTTTTCCTTTGCTGTTTATTCATTTATTTTAAACGATATTTATAT

CATCGGGTTTCATTCACTATTTTTCTTTTCGATAAATTTTTGTCAGCATTTTCTTTTAC

CTCTTCTTTCTGTTTATGTTAATTTTCTGTTTCTTAACCCAGTCTTCTCGATTCTTATC

TACCGGACCTATTATAGGTCACAGGGTCTTGATGCTTTGGTTTTCATCTGCAAGAGTCT

GACTTCCTGCTAATGCTGTTCTGTGTCAGGGTGCATCTGAGCACTGATGTGGAGTTTTC

TTGTGGATATGAGCCATTCATAGTGTGGGATGTGCCATAGTTCATG”




Additional practice problems:

If you are interested in additional problems for practice, here are a few more problems you can work on. We won’t be grading them, but a little extra practice never hurt anyone.




<h2>Complement sequence function</h2>

DNA is double stranded even though we always write a single strand’s nucleotide sequence.  This is because we can infer the other stands sequence from the given strand.  Every A on one strand has a complementary T on the opposite strand (every C has a G).  Therefore we can create the complement strand by swapping the nucleotides with the complementary nucleotide.  Create a function to take the​           sequence and produce the complement sequence.




<h2>Reverse complement sequence function</h2>

You now have the complement strand, but the DNA is read in the forward direction for the given strand and in the reverse direction for the complementary strand. Therefore, we must reverse the strand (first character becomes the last character, second becomes second to last, and so on.) to print it correctly.  Create a function to​ reverse the complement of a given DNA sequence. Now we can search both strands of the given DNA sequences by using our previously created functions.


