Download Link: https://assignmentchef.com/product/solved-csci340-assignment1
<br>
Compare the performance of process creation and destruction when implemented with and without linked lists.

<strong>Overview: </strong>

Method 1 of the process creation hierarchy uses linked lists to keep track of child processes as described in section 5.1 (within <strong>Week 5 – Class 9 and 10</strong>) <strong>The process control block</strong>, subsection <strong>The PCB data structure</strong>.




For the purposes of performance evaluation, the PCBs are simplified as follows:

<ol>

 <li>Implementation of the table of all the PCBs is an array of size n.</li>

 <li>Each process is referred to by a PCB index, 0 through n-1.</li>

 <li>Each PCB is a structure consisting of only the two fields:

  <ol>

   <li>Parent: a PCB index corresponding to the process’s creator.</li>

   <li>Children: a pointer to a linked list, where each list element contains the PCB index of one child process.</li>

  </ol></li>

</ol>




The necessary functions are simplified as follows:

<ol>

 <li>Create(p) represents the create function executed by process PCB[p]. The function creates a new child process PCB[q] of process PCB[p] by performing the following tasks:

  <ol>

   <li>Allocate a free PCB[q].</li>

   <li>Record the parent’s index, p, in PCB[q].</li>

   <li>Initialize the list of children of PCB[q] as empty.</li>

   <li>Create a new link containing the child’s index q and appending the link to the linked list of PCB[p].</li>

  </ol></li>

 <li>Destroy(p) represents the destroy function executed by process PCB[p]. The function recursively destroys all descendent processes (child, grandchild, etc.) of process PCB[p] by performing the following tasks for each element q on the linked list of children of PCB[p]:

  <ol>

   <li>Destroy(q). /* recursively destroy all descendants. */</li>

   <li>Free PCB[q].</li>

   <li>Deallocate the element q from the linked list.</li>

  </ol></li>

</ol>




Method 2 of the same process creation hierarchy uses no linked lists.  Instead, each PCB contains the 4 integer fields parent, first_child, younger_sibling, and older_sibling, as described in the subsection <strong>Avoiding linked lists</strong>.







<strong>Design: </strong>




<ol>

 <li>Implement the two methods of the process creation hierarchy in Java.</li>

</ol>




<ol start="2">

 <li>Assume that PCB[0] is the only currently existing process and write a test procedure that performs a series of process creations and destructions. For example:</li>

</ol>

Create(0)   /* creates 1st child of PCB[0] at PCB[1]*/

Create(0)   /* creates 2nd child of PCB[0] at PCB[2]*/

Create(2)   /* creates 1st child of PCB[2] at PCB[3] */

Create(0)   /* creates 3rd child of PCB[0] at PCB[4] */

Destroy(0)   /* destroys all descendents of PCB[0], which includes processes PCB[1] through PCB[4] */




<ol start="3">

 <li>The test procedure should do a significant number of process creations and deletions with the calls to create and destroy intermingled</li>

</ol>




<ol start="4">

 <li>Run the test procedure repeatedly in a long loop on each method, with the test procedure computing and then printing the running time for the method. This should show how much time method 2 saves, which avoids dynamic memory management.</li>

</ol>




<ol start="5">

 <li>One or more classes implement the test procedure and the two methods.</li>

</ol>




<ol start="6">

 <li>Create a driver class and make the name of the driver class <strong>Assignment1</strong> containing only one method: public static void main(String args[]).</li>

</ol>

The main method essentially executes the test procedure on each method.




I compile and run your program via the command line using the Java JDK.  Therefore, the command I type to execute your program is <strong>java Assignment1</strong>.  Make sure your project compiles and runs via the command line using the Java JDK.  I will not use any other Java development tool to compile and run your project code.




<ol start="7">

 <li>You must declare public each class you create which means you define each class in its own file.</li>

</ol>




<ol start="8">

 <li>You must declare private all the data members in every class you create.</li>

</ol>




<ol start="9">

 <li><strong>Tip:</strong> Make your program as modular as possible, not placing all your code in one .java file. You can create as many classes as you need in addition to the classes described above.  Methods being reasonably small follow the guidance that “A function does one thing and does it well.”  You will lose a lot of points for code readability if you do not make your program as modular as possible.  But, do not go overboard on creating classes and methods.  Your common sense guides your creation of classes and methods.</li>

</ol>




<ol start="10">

 <li>Do <strong>NOT</strong> use your own packages in your program. If you see the keyword <strong>package</strong> on the top line of any of your .java files then you created a package.  Create every .java file in the <strong>src</strong> folder of your Eclipse project, if you’re using Eclipse.</li>

</ol>




<ol start="11">

 <li>Do <strong>NOT</strong> use any graphical user interface code in your program!</li>

</ol>




<ol start="12">

 <li>Do <strong>NOT</strong> type any comments in your program. If you do a good job of programming by following the advice in number 9 above then it will be easy for me to determine the task of your code.</li>

</ol>





