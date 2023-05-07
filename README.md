Download Link: https://assignmentchef.com/product/solved-operating-systems-project-the-dining-philosophers-monitor
<br>
<strong>Goal</strong>: Implement a Monitor to solve the Dining Philosophers problem.

<strong>Description</strong>: Section 5.8.2 of the text describes a solution to the dining philosophers problem using monitors.  Implement this solution using Java’s condition variables.

<strong>Input</strong>: n/a

<strong>Output</strong>: Print output to System.out to demonstrate your functioning solution.

<strong>Deliverables</strong>: Java program in an executable jar file names [YOUR_NAME]DiningPhilos.jar, all sources

(please include your entire src folder), a readme.txt, and a post-mortem in a zip file named

[YOUR_NAME]DiningPhilos.zip.  All source code belongs in a package named edu.frostburg.cosc460.

[YOUR_NAME] = LastNameFirstName The program will be tested in Ubuntu 16.

<strong>Details: </strong>

<strong>Part 1</strong>: Reread section 5.8 – 5.8.2 on Monitors and help you design the basics.

Begin by setting up your project.  You should have 3 components: The server, the philosophers, and the driver.  Begin by creating these classes.  The server should implement the following interface:

public interface DiningServer {




/* called by philosopher that wishes to eat */     public void takeChopsticks(int philNumber);




/* called by philosopher when it has finished eating */     public void returnChopsticks(int philNumber); }




The driver runs your program, and the Philosophers simply alternate between thinking and eating.  You should also include an enumerated type for Philosopher states (HUNGRY, EATING, THINKING).

<strong>Part 2</strong>: Implement the Philosophers

The philosophers don’t do much of anything.  They represent units of work in parallel processing, but don’t actually do anything useful.  A philosopher only needs two pieces of data, its ID (0 – 4) and a reference to the server from where it can collect chopsticks.

Each philosopher runs independently (i.e. are Runnable) and infinitely alternates between thinking and eating.  To keep things running at a manageable pace, they should wait with Thread.sleep() for random amounts of time between each step.  In other words, a philosopher should wait (think), then takeChopsticks(myID) (hungry), then wait (eat), and then return the chopsticks.  Forever.  Such is life for the philosopher.

<strong>Part 3</strong>: Implement the Server using the pseudocode in 5.8.2.

The pseudocode get you far in your solution, but it misses a key component, how to manage the Condition variables.  Java attaches condition variables to the ReentrantLock class.  (<a href="https://docs.oracle.com/javase/7/docs/api/java/util/concurrent/locks/ReentrantLock.html">API</a><a href="https://docs.oracle.com/javase/7/docs/api/java/util/concurrent/locks/ReentrantLock.html">)</a>  You can get a Condition from your lock.

Lock lock = new ReentrantLock();

// get condition with lock.newCondition().  You need 5

Use Java’s condition variables to synchronize the activity of the philosophers and prevent deadlock.

After you have completed the DiningPhilosophersServer, you can create your driver class.  Your driver will set up and start the Philosopher threads, then simply loop, printing out the state of the server every now and then.

<strong>Part 4</strong>: Testing and Wrap-Up

Once you have completed the above, it can be difficult to tell what you have done.  Make good use of the debugger and system output to make sure that your philosophers each get a chance to eat.  <a href="https://netbeans.org/kb/docs/java/debug-multithreaded.html">(</a><a href="https://netbeans.org/kb/docs/java/debug-multithreaded.html">Debugging threads in Netbeans</a><a href="https://netbeans.org/kb/docs/java/debug-multithreaded.html">)</a>.

After you are satisfied that your program runs correctly, make sure to complete your documentation and submit your project to Blackboard by the due date.







Checklist

<table width="336">

 <tbody>

  <tr>

   <td width="52"> </td>

   <td width="208">Item</td>

   <td width="76">Value</td>

  </tr>

  <tr>

   <td width="52"> </td>

   <td width="208">Part 1</td>

   <td width="76">10%</td>

  </tr>

  <tr>

   <td width="52"> </td>

   <td width="208">Part 2</td>

   <td width="76">30%</td>

  </tr>

  <tr>

   <td width="52"> </td>

   <td width="208">Part 3</td>

   <td width="76">30%</td>

  </tr>

  <tr>

   <td width="52"> </td>

   <td width="208">Part 4</td>

   <td width="76">10%</td>

  </tr>

  <tr>

   <td width="52"> </td>

   <td width="208">Documentation</td>

   <td width="76">10%</td>

  </tr>

  <tr>

   <td width="52"> </td>

   <td width="208">Deliverables</td>

   <td width="76">5%</td>

  </tr>

  <tr>

   <td width="52"> </td>

   <td width="208">Post-mortem</td>

   <td width="76">5%</td>

  </tr>

 </tbody>

</table>




<h1>Avoid</h1>

<table width="336">

 <tbody>

  <tr>

   <td width="52"> </td>

   <td width="208">Item</td>

   <td width="76">Value</td>

  </tr>

  <tr>

   <td width="52"> </td>

   <td width="208">Bugs</td>

   <td width="76">-x</td>

  </tr>

  <tr>

   <td width="52"> </td>

   <td width="208">Runtime errors</td>

   <td width="76">-y</td>

  </tr>

  <tr>

   <td width="52"> </td>

   <td width="208">Unsatisfactory quality</td>

   <td width="76">-z</td>

  </tr>

  <tr>

   <td width="52"> </td>

   <td width="208">Compilation errors</td>

   <td width="76">–50+%</td>

  </tr>

 </tbody>

</table>


