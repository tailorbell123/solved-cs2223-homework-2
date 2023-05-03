Download Link: https://assignmentchef.com/product/solved-cs2223-homework-2
<br>
This homework is concerned with how memory is allocated to store information. In Java (and most programming languages) you have two possible choices:

<ul>

 <li>Contiguous memory that stores an array of values</li>

 <li>Fragmented nodes with pointers to other nodes</li>

</ul>

Homework1 was concerned exclusively with arrays. Now we are ready to explore more dynamic structures.

<table width="639">

 <tbody>

  <tr>

   <td width="115">Fragmented</td>

   <td width="523"></td>

  </tr>

 </tbody>

</table>




<h1>Getting Started</h1>

Copy the following files into your <strong>USERID.hw2</strong> package:

<ul>

 <li>hw2.TaleOfTwoCitiesExtractor</li>

 <li>hw2.Q1</li>

 <li>hw2.Q2</li>

 <li>hw2.WordList</li>

 <li>hw2.WordSymbolTable</li>

 <li>hw2.Q3</li>

 <li>hw2.Selection</li>

</ul>

Because I cannot be entirely sure <strong>how</strong> you have checked out the code for HW2, I will post a video that tells you whether you have completed the above steps properly.

In particular, once you have copied TaleOfTwoCitiesExtractor, you should execute it within your project. It should run and tell you that it is “OK.” If this doesn’t happen, contact me or a TA/SA for help.

<h2>Q1. Working With Linked Lists</h2>

Often you will need to construct a <strong><u>set</u></strong> of items and support search capability (i.e., to determine if a target value is in the set of not). A mathematical set contains unique items, so no element can be duplicated in the set. Use the following class, which you will copy into your <strong>USERID.hw2</strong> area and modify to work properly. It exists to maintain a set of unique Strings. You can add to the set, return its size, check whether the set contains a given element, or remove an element from the set.

<strong>public</strong> <strong>class</strong> WordList {




<strong>  class</strong> Node {     String     word;

Node       next;




Node(String w) {       <strong>this</strong>.word = w;

}

}




/**

<ul>

 <li>If the given element doesn’t exist in the set then update</li>

 <li>the set and return true; otherwise return false. This means that</li>

 <li>adding a duplicate element to a set must return false.</li>

 <li><strong>@param</strong> elt element to be added.</li>

</ul>

*/

<strong>  boolean</strong> add(String elt) { … }




/**

<ul>

 <li>Returns true if the element exists within the set.</li>

 <li><strong>@param</strong> elt target element to be searched.</li>

</ul>

*/

<strong>  boolean</strong> contains(String elt) { … }




/** Returns the number of elements in the set. */ <strong>  public</strong> <strong>int</strong> size() { … }

<strong> </strong>

/**

<ul>

 <li>Returns true if the given element was in the set (and was removed) or</li>

 <li>false if the given element did not belong to the set.</li>

 <li><strong>@param</strong> elt element to be removed.</li>

</ul>

*/

<strong>public</strong> <strong>boolean</strong> remove (String elt) { … }




/** For debugging, return comma-separated string of elements in the set. */ <strong>  public</strong> String elements() { … }

}




Your task for question 1 is to use this data type (as implemented using Linked Lists) to answer three questions about the <u>Tale Of Two Cities</u> by Charles Dickens. There are 45 chapters in the book, which I have extracted into separate files. I will admit that the transcription is quite awkward. For example, everything has been converted to lower case, and all punctuation marks have been removed. Some words are subdivided improperly, but this is what we have to work with!

I am providing a helper class, TaleOfTwoCitiesExtractor, which you can use to extract each of the words, in order, from a given chapter. I recommend that you copy this class into your <strong>USERID.hw2</strong> package just in case you have to edit it to locate the chapters from the <u>Tale of Two Cities</u>

Despite there being 45 chapters, your program should be able to answer all three questions in less than 1-2 minutes. For this entire question, you can rely on TaleOfTwoCitiesExtractor to return each of the words one at a time. Simply accept that this class is responsible for determining the words one at a time. <strong>Q1.1 [10 pts.] </strong>Which chapter <u>contains the most number of words in total</u>, out of the 45 chapters?

<strong>Q1.2  </strong>Which chapter (of the 45) contains the <u>fewest number of unique words</u>? Be sure to report how many unique words occur in the chapter you identify.

<strong>Q1.3  </strong>What is the <u>total number of unique words</u> in the entire book (all 45 chapters)?

<strong>Q1.4  </strong>Which two distinct chapters (of the 45) <u>share the most words in common</u>?  You should be able to use WordList to answer this question as well.




Q2. Working with Symbol Tables

A common scenario is to implement a symbol table of keys and accumulate counts of repetitions for these keys. Copy this class into your <strong>USERID.hw2</strong> area and modify to work properly.

<strong>public</strong> <strong>class</strong> WordSymbolTable {




<strong>  class</strong> Node {     String     word;     <strong>int</strong>        count;

Node       next;




Node(String w, <strong>int</strong> count) {       <strong>this</strong>.word = w;       <strong>this</strong>.count = count;

}

}

/** Increase the count for given key. Note: this might need to add the word in the first

<ul>

 <li>Returns TRUE if the word was newly added, otherwise FALSE</li>

</ul>

*

<ul>

 <li><strong>@param</strong> key key whose count has increased by 1. */ <strong>  public</strong> <strong>boolean</strong> increment(String key) { … }</li>

</ul>




/** Decrease the count for given key. Note: this might need to remove the key once the

<ul>

 <li>count reaches zero. Returns TRUE if the word was removed, otherwise FALSE *</li>

 <li><strong>@param</strong> key key whose count is to decrease by 1. */ <strong>  public</strong> <strong>boolean</strong> decrement(String key) { … }</li>

</ul>




/** Returns the number of keys in the symbol table. */ <strong>  public</strong> <strong>int</strong> size() { … }




/** Return the accumulated counts of all keys in the word table. */ <strong>  public</strong> <strong>int</strong> totalCounts() { … }




/** Returns true if the given key was in the word table (and was removed) or

<ul>

 <li>false if the given key did not belong to the word table.</li>

 <li><strong>@param</strong> key key to be removed. */   <strong>public</strong> <strong>boolean</strong> remove (String key) { … }</li>

</ul>




/** Returns count of the key, if it exists in the word table; 0 otherwise. */   <strong>int </strong>count(String key);




/** Returns true if the key exists in the word table; false otherwise. */   <strong>boolean</strong> contains(String key);




/** Returns key whose repetition count is equal to the maximum in the Symbol table

<ul>

 <li>Note that there may be multiple words that have the maximum count, so this method</li>

 <li>only needs to return one of them. */</li>

</ul>

<strong>  public</strong> String mostFrequent() { … }




/** Output semicolon-separated (k,v) pairs in collection to the console. */ <strong>  </strong>String pairs();

}

You can continue to use the helper TaleOfTwoCitiesExtractor class for this question.

<strong>Q2.1  </strong>What is the most frequently used word in <u>The Tale Of Two Cities</u>? How many times is it used?

<strong>Q2.2  </strong>What are the top-ten most frequently used words in <u>The Tale Of Two Cities</u>? How many times is it used?

<strong>Q2.3  </strong>How many words occur exactly once in <u>The Tale Of Two Cities</u>?




<h2>Q3. Mathematical Analysis</h2>

This question is a more complicated version of what you will see on the midterm exam. You can find this code in the algs.hw2.Q3 class. Copy this class into USERID.hw2.Q3 and modify it based on the requirements below.

Given the following proc function, let S(N) be the number of times power(base, exp) is invoked when calling proc(a, 0, n-1)  on an array, a, of length n containing integer values from 0 to n-1.

<strong>static</strong> <strong>long</strong> power(<strong>int</strong> base, <strong>int</strong> exp) { <strong>  return</strong> (<strong>long</strong>) Math.<em>pow</em>(base, exp);

} <strong> </strong>

<strong>public</strong> <strong>static</strong> <strong>long</strong> proc(<strong>int</strong>[] a, <strong>int</strong> lo, <strong>int</strong> hi) { <strong>  if</strong> (lo == hi) {

<strong>    return</strong> <em>power</em>(a[lo], 2) + <em>power</em>(a[hi],2);

}




<strong>  int</strong> m = (lo + hi) / 2;

<strong>  long</strong> total = <em>power</em>(lo, 2) + <em>proc</em>(a, lo, m); <strong>  while</strong> (hi &gt; lo) {     total += <em>power</em>(a[lo], 2);     lo+=2;

}

<strong>  return</strong> total;

}

For this assignment, develop the recurrence relationship for S(N) and compute its closed-form. Then modify the Q3 class to output a modified table that shows the computed counts.

<h3>Question 3.1</h3>

Identify the Base Case for S() and the Recursive Case for S(n). Refer back to lecture for the format of this question.

<strong>Question 3.2 (12 pts.)</strong>

Derive an exact solution to the recurrence for S(N) when N is a power of 2. Be sure to show your work.

<h3>Bonus Question 3.3 (1pt.)</h3>

Can you derive a formula that predicts the Value printed for proc(a, 0, a.length-1) when a contains the integers from 0 to n-1 and N is a power of 2.

<h2>Q4. Working with Linked Lists</h2>

You are in a group of N people that visit a casino and everyone wins a little bit of money. You suggest it would be better if just one person collected all the winnings and you propose the following strategy.

<ol>

 <li>You tell everyone to stand in a circle (yourself included).</li>

 <li>You ask for a volunteer to be starting person #1. In clockwise fashion, everyone in the circle is assigned an increasing number from 1 to <em>N</em>.</li>

 <li>You pick a number 0 &lt; <em>k</em> &lt; <em>N</em>.</li>

</ol>

Beginning with the starting person, count <em>k</em> people clockwise. The <em>k<sup>th</sup></em> person leaves the circle which shrinks by one in size; starting with the next person, again count <em>k</em> people clockwise and that person leaves the circle. The last one remaining collects all winnings. Visualize the situation for N=5 people with k=3 as follows. The large number in red is the person eliminated in that round (there are always N-1 rounds).




Start with person #1 and count three clockwise, so the first person eliminated is #3. Continuing clockwise around, the third person (starting at person #4) is person #1, who is then eliminated. In the third round, starting with person #2, the third remaining person is #5, who is eliminated. Finally, with two people left (#2 and #4) the last person to be eliminated is #2. The final person standing is #4.

Copy algs.hw2.Selection into the USERID.hw2 package and modify it to produce the correct output. Modify the countoff() method to produce a FixedCapacityQueue&lt;Integer&gt;reflecting the order in which people are eliminated. The final item in the queue is the person who collects all winnings.

Your implementation MUST create a Linked List using the provided Node class. Unlike in these diagrams above, <strong><u>your linked list should not have the final Node connect back to the first Node</u></strong>. It must remain a true linear linked list whose final Node (the person 5 above in this example) has <strong>null</strong> as next reference. <strong>Question 4.1 (10 pt.) When your program executes, the following two cases should work as follows </strong>

For new Selection(5, 3).countOff(), the resulting queue should be [3 1 5 2 4] where the last person who receives all winnings is person #4.

For new Selection(17, 7).countOff(), the resulting queue should be [7 14 4 12 3 13 6 17 11 9 8 10 16 5 15 1 2] where the last person who receives all winnings is person #2.

<strong> </strong>

<h3>Bonus Question 4.2 (1 pt.)</h3>

If you generate the first few values of the last remaining person method, you may find some interesting relationships. Let <em>T(n,k)</em> be the last person standing from an initial circle of N people where you eliminate every k<sup>th</sup> person until only one remains. Place the results in a triangle as follows (which I call the Josephus Triangle – see <a href="http://www.josephustriangle.org/">www.josephustriangle.org</a><a href="http://www.josephustriangle.org/">)</a>.

Diagonal 1

/ Diagonal 2

/ / Diagonal 3

Row 1                    1 / / Diagonal 4

Row 2                   2 1 / /

Row 3                  3 3 2 /        Row 4                 4 1 1 2

Row 5                5 3 4 1 2

Row 6               6 5 1 5 1 4

Row 7              7 7 4 2 6 3 5




If you know <em>T(n,k)</em> for row n and diagonal k, can you come up with a formula for <em>T(n+1, k)</em>?

<h3>Bonus Question 4.3 (1 pt.)</h3>

There is a clear pattern in diagonal 1. Can you identify the pattern that appears in Diagonal 2? And if so, can you come up with a formula that computes <em>T(n,2)</em> for any n &gt;= 2?

<h3>Bonus Question 4.4 (1 pt.)</h3>

If you consider the right diagonal heading south east, (i.e., 1, 1, 2, 2, 2, 4, 5, …), these numbers form an unusual sequence (<a href="https://oeis.org/A007495">https://oeis.org/A007495</a><a href="https://oeis.org/A007495">)</a> that seems to defy any attempt at coming up with a closed formula. There are two cases that I find interesting, however, and I have been working on them for weeks.

<ul>

 <li>In mathematics, Prime Numbers are studied EXHAUSTIVELY! One conjecture is that there are infinitely many <a href="https://en.wikipedia.org/wiki/Twin_prime">twin primes</a><a href="https://en.wikipedia.org/wiki/Twin_prime">,</a> such that both <em>p</em> and <em>p+2</em> are prime numbers. With this concept in mind, I introduce the concept of <u>twin consecutive pairs</u> in this sequence, such that the value in the right diagonal I neighboring rows is the same. The first twin pairs are (1,1), (2,2), (2,2), and the next one occurs at (9,10) when both values are 8. Can you compute the rows for when the next twin pair occurs?</li>

 <li>The number 1, in all of my computations, only occurs as the right value in the first two rows. I am not bold enough to assert that it never occurs again. However, consider when the right value in row n is equal to n-1 (such as occurs in row two above). This seems like a fruitful place to search. This occurs ten times in the first 1000 rows. Can you compute the rows for these values?</li>

</ul>


