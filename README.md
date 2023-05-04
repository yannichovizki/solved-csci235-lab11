Download Link: https://assignmentchef.com/product/solved-csci235-lab11
<br>
You will use a lab account for a VNC display. The lab account already started a VNC session, so you don’t need to do Step 3 or 4 of Lab 7’s Task #1. Two steps that you need to do are:

<ol>

 <li>Create a tunnel from your machine to a VNC display (Step 5 of Lab 7’s Task #1).

  <ol>

   <li>A cslab machine number and a display number will be provided to you.</li>

   <li>For example, if the given machine is <strong>cslab10</strong>, and the display number is <strong>12</strong>, the command for creating a tunnel to the display will be:

    <ul>

     <li>Mac Terminal: ssh –L 5901:localhost:<strong>5912</strong> <em>your_loginID</em>@<strong>cslab10</strong>.wheaton.edu</li>

     <li>Windows PuTTY:</li>

    </ul></li>

  </ol></li>

</ol>

Host Name: <strong>cslab10</strong>.wheaton.edu

For Connection, SSH, Tunnels: 5901 for the “Source port” and localhost:<strong>5912</strong> for the “Destination”.

<ol>

 <li>The CS system will prompt for your (ID and) password as usual.</li>

</ol>




<ol start="2">

 <li>Start a VNC viewer on your machine (Step 6 of Lab 7’s Task #1).

  <ol>

   <li>The given display’s VNC password will be provided. You need to use this password to connect to the display.</li>

  </ol></li>

</ol>




Tips:

<ul>

 <li>If you don’t see the menu bar at the top of the CS desktop window, right-click the desktop screen to get Applications menu.</li>

 <li>When you are done with the desktop, close the desktop and connection by doing:

  <ul>

   <li>For TightVNC, use the X button at the top corner of the window.</li>

   <li>For Mac, in Screen Sharing menu at the top, select Connection, and select Close.</li>

  </ul></li>

</ul>




===

<h1>Java Collections</h1>

<strong> </strong>

<strong>Documentation and styling of your code will be part of your grade.  </strong>




Create a new directory and cd to it. Then copy starting files from the lab directory to your current directory.

$ cp /cslab/class/csci235/labs/lab11/* .




You should have two Java files to work on, one class file, and three files that you can use as input for testing.




You will write a program that takes a piece of text and counts the frequency of the words in it. For example, in this sentence, the word <em>times </em>occurs 5 times, <em>occurs </em>also occurs 5 times, <em>and </em>occurs 3 times, and <em>for</em>, <em>example</em>, <em>in</em>, <em>this</em>, <em>sentence</em>, <em>the</em>, <em>word</em>, <em>each </em>and <em>also </em>each occurs 2 times.




Your program will read the text on which to do the word counting from a file. You have been provided with the component that reads in from a file. You will run the program as follows:

$ java FileProcessor <em>filename</em>  (for example, $ java FileProcessor Ps132)




The program reads in a piece of text stored in the file and prints the results to the screen. You will complete two

Java files (FileProcessor.java and SIPair.java) through the small steps below. <strong>Refer to the CollectionAPI document for necessary collection methods. </strong>







<strong>Step #1</strong>: Open FileProcessor.java, and inspect the code. The main method calls

FileAux.filesToWords() from the provided class file, which takes the name of a file, opens and reads that file, and returns an ArrayList&lt;String&gt; of the words it contains (ignoring punctuation, spaces, etc.).




Compile the file, and run it with one of the provided files as input. Which statement generates the output? What method has been used to print the output?




<strong>Step #2</strong>: Now delete the line that prints out the ArrayList object.  Uncomment the code block (enclosed by /* and */) for Step 2, and fill in the loop so that it adjusts the HashMap to account for the current word. <u>Make the</u> <u>word lowercase</u>: we do not want to consider capitalization in the word counting. The loop will read every word in the ArrayList object and count its occurrences.

<ul>

 <li>See how Iterator has been used for the ArrayList object, words.</li>

 <li>next() will return a word of the ArrayList because it has been defined on words.</li>

</ul>




Then, the pair of word (as Key) and occurrences (as Value) will be inserted into the HashMap, <em>tally</em>.  In other words, you need to write the code for the following steps by using appropriate instance methods:

<ul>

 <li>Get a word from the iterator, and make the word lowercase (use toLowerCase()).</li>

 <li>Check if the word is already in the map, <em>tally</em>. o If it is in the map,</li>

 <li>get the word’s current number of occurrences, and increase the number by 1. § Put this updated pair back to the map.

  <ul>

   <li>Else, store a new pair of the word and the occurrence (namely, 1) to the map.</li>

  </ul></li>

</ul>




Compile and test the program.




<strong>Step #3</strong>: Delete the line that prints the HashMap, tally (which is System.out.println(tally); at line 38).  You will write the results, one word per line. Uncomment the code block for Step 3 (don’t uncomment yet the statement, ArrayList&lt;SIPair&gt; pairs…), and fill in the for loop.  The loop should print out a word followed by its frequency, one word per line. Find the statement that declares the iterator within the for loop, and answer to the questions:

<ul>

 <li>Does HashMap provide iterator() method?</li>

 <li>What will be returned by keySet()? o This method returns a set of Key values in the map. For example, assume that a HashMap object, myMap contains three pairs as follows: {apple=3, orange=1, banana=5}</li>

</ul>

myMap.keySet() will return the set of the keys: [apple, orange, banana]

<ul>

 <li>What does the following statement do?</li>

</ul>

Iterator&lt;String&gt; it = tally.keySet().iteractor()

<ul>

 <li>Since keySet() returns the keys of tally, the iterator object, it can be used to get each key of tally.</li>

</ul>

<ul>

 <li>What will be then stored at s from the following statement? String s = it.next();</li>

</ul>




Write the body of the loop. Refer to the CollectionAPI document, and use appropriate HashMap methods. Compile and test the program.




The frequency information would be much more useful if it were in an order. Moreover, since we are more likely to be interested in knowing what the most frequent words are, we would like it <em>backwards sorted</em>. For example, for the file, <em>Ps132,</em>




In order to do this, you will store all the word/frequency pairs in “an ArrayList of pairs” and sort them. Then, you will first need a Java class that represents those pairs.




<strong>Step #4</strong>: Open the file SIPair.java. This is for a class which represents a pair containing a String object and an int (see the instance variables).

Fix the toString() method so that it returns the string followed by a colon and space, then the number (as seen in the figure).




Back in FileProcessor.java, uncomment the line 45 that creates an ArrayList of these pairs (SIPair). Also, uncomment the line further down that prints pairs.

<ul>

 <li>See the types of ArrayList. pairs will hold objects of SIPair.</li>

 <li>On the other hand, words is an ArrayList object that holds String objects.</li>

</ul>

…




Now comment out the body of the loop you wrote in Step 3, and write new code for the body so that instead of printing each pair of String and int, it makes a new SIPair object out of them and adds that object to the ArrayList object, pairs.

<ul>

 <li>Namely, instead of using the HashMap object (tally), you are creating SIPair objects and storing them</li>

</ul>

to the ArrayList object, pairs.




Make sure to understand how SIPair objects are created and stored in pairs. Compile and run the program.

The output should be now in the default format of printing the contents of ArrayList.

<ul>

 <li>Which statement prints the output?</li>

</ul>




<strong>Step #5</strong>: Java comes with the Collections.sort() method in the class Collections, which we can use to order our list. This method will operate on an ArrayList object as long as the type of element stored in the object implements an interface, Comparable. This interface has a single method, compareTo() which allows us to compare two items of the same type so that the sort() method knows what order to put them in.




Open SIPair.java which implements the Comparable interface (see the class heading), and fill in the compareTo() method.  This method is defined as returning zero if the two objects are equal, a negative value if the calling object (this) is “less than” the parameter other, and a positive value if the calling object is “greater than” other. Because we are sorting, “less than” means “belonging before.” We want <em>higher </em>frequency first; so we should <u>get a negative value if the frequency of </u><u>this</u><u> is larger</u>. If two words have the same frequency, we break the tie by putting them in alphabetical order based on the words themselves (for example, “ever”, “his”, and “one” in the above figure), which we can get by <strong>calling </strong><strong>compareTo() method <u>on String object</u></strong>.




Write the body of compareTo. If necessary, write a simple main method in SIPair.java to make a few pairs and see the results of comparing them. If your compareTo works, move to the next step.




<strong>Step #6</strong>: Back in FileProcessor.java, uncomment the line 57 that calls Collections.sort(pairs). This method should work now because SIPair (the type of pairs) has the appropriate code in compareTo(). Compile and test the program.




<strong>Step #7</strong>: Replace the statement that prints pairs (System.out.println (pairs)) with a loop that will write each element in pairs on a line by itself. Make use of the toString() method you wrote in Step 4. Then, the program should print the output similar to the one in the figure.




Compile and test everything with provided testing files, i.e.,<em> Ps132</em>.

<strong> </strong>