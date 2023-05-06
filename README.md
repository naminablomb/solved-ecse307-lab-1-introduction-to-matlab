Download Link: https://assignmentchef.com/product/solved-ecse307-lab-1-introduction-to-matlab
<br>
<h1><strong>0. Objectives</strong></h1>

This lab is divided into two parts. The first part is an introduction to some useful functions in <strong>MATLAB </strong>and how they will be used in the series of following labs. The second part is an application of how to calculate Laplace and inverse Laplace using <strong>MATLAB</strong>. Each part has questions at the end that need to be completed.

<h1><strong>1. How to Submit Lab Reports</strong></h1>

A <strong>MATLAB </strong>LiveScript is an interactive document that combines <strong>MATLAB </strong>code with embedded output, formatted text, equations, and images in a single environment called the Live Editor. LiveScripts are stored using the LiveScript file format in a file with a <strong>.mlx </strong>extension.

Labs consist of a <strong>MATLAB </strong>LiveScript file. You should read and answer the questions inside the LiveScript document. At the end of the lab:

<ol>

 <li>Fill your Name, and ID at the header of the LiveScript.</li>

 <li>Ensure that the LiveScript document runs without errors.</li>

 <li>Export the LiveScript to a PDF format (Click on the arrow under the save icon).</li>

 <li>Submit the LiveScript and the generated PDF in myCourses.</li>

 <li>If requested, attach any auto-generated MAT-file (explained in section 2.4).</li>

</ol>

<h1><strong>2. Useful Functions</strong></h1>

<h2>2.1. Documentation in <strong>MATLAB</strong></h2>

All the functions in <strong>MATLAB </strong>are accompanied with detailed documentation about their usage. You can access inline documentation by typing <strong>help </strong>followed by the function name. For example

help abs

ABS    Absolute value.

ABS(X) is the absolute value of the elements of X. When     X is complex, ABS(X) is the complex modulus (magnitude) of     the elements of X.




See also SIGN, ANGLE, UNWRAP, HYPOT.     Documentation for abs        doc abs     Other functions named abs        codistributed/abs    duration/abs    iddata/abs    sym/abs        dlarray/abs          gpuArray/abs

A more complete documentation can be also obtained by using the <strong>doc </strong>command. For example

doc abs

<h2>2.2. Arrays in <strong>MATLAB</strong></h2>

Matrices and arrays are the fundamental representation of information and data in <strong>MATLAB</strong>. For a basic overview of matrix and array manipulation, you can refer to <strong>MATLAB </strong>on-line documentation: <a href="https://www.mathworks.com/help/matlab/learn_matlab/matrices-and-arrays.html">Matrices </a><a href="https://www.mathworks.com/help/matlab/learn_matlab/matrices-and-arrays.html">and Arrays,</a> and if needed watch the following video <a href="https://www.mathworks.com/videos/working-with-arrays-in-matlab-101637.html">Working with Arrays in MATLAB</a>.

Arrays will be used to model a discrete-time signal. An example of a discrete-time signal is:

<table width="651">

 <tbody>

  <tr>

   <td width="651">dt = 0.01; % timestep of discrete signal in seconds T = 10; % Final value of the time signal in seconds% This creates an array |t = [0, 0.01, 0.02, 0.03, …, 9.98, 9.99, 10.0]|.t = 0:dt:T; % time signal</td>

  </tr>

 </tbody>

</table>

A sine wave signal of amplitude 1 and period 1 rad/second

x<sub>1</sub>(t) = sin(2πt)

can be written as

x1 = sin(2*pi*t);

Logical operations can be used to construct a desired signal. For example, the following signal

x

Can be written as

x2 = zeros(size(t)); % create a zero signal with the same size as time x2(t &lt; 5) = t(t &lt; 5); % value is equal to time, but only when time &lt; 5 x2(t &gt;= 5) = -t(t &gt;= 5) + 10; % value is equal to -time+10, but only when time &gt;= 5

Other useful functions are: <strong>size</strong>, <strong>length</strong>, <strong>ones</strong>. You can use <strong>MATLAB </strong>help for more information.

<h2>2.3. Plotting signals</h2>

In order to present results you can use the <strong>plot </strong>function. <strong>plot(X,Y) </strong>creates a 2-D line plot of the data in Y versus the corresponding values in X.

figure; hold on; grid on; plot(t, x1); plot(t, x2); title(sprintf(‘Student ID %s – Example plot’, Students.ID)); xlabel(‘Time (seconds)’) ylabel(‘Signal’) legend(‘x_1(t)’, ‘x_2(t)’) hold off;

<h2>2.4. Matrices in <strong>MATLAB</strong></h2>

Matrices are extensions of arrays. They will be used to represent linear systems in a state space form. For example to represent the matrix A:

<table width="106">

 <tbody>

  <tr>

   <td width="64">8A = ⎡3⎣4</td>

   <td width="22">159</td>

   <td width="19">67⎤2⎦</td>

  </tr>

 </tbody>

</table>

We write

A = [8, 1, 6; 3, 5, 7; 4, 9, 2]

A =

8     1     6

<ul>

 <li>5 7</li>

 <li>9 2</li>

</ul>

Determinant of A can be obtained by:

det(A)

ans =   -360

Eigenvalues of A can be obtained by:

eig(A)

ans =    15.0000

4.8990

-4.8990

Inverse of A can be obtained by:

inv(A)

ans =     0.1472   -0.1444    0.0639

-0.0611    0.0222    0.1056

-0.0194    0.1889   -0.1028

<h2>2.5. Saving/loading data</h2>

In <strong>MATLAB </strong>you can save any or all the variables in the current workspace to a MAT-file (.mat). You can then reuse the workspace variables later during the current MATLAB session or during another session by loading the saved MAT-file.

For example, to save a variable, you can use:

example = sprintf(‘A variable generated by Student ID &lt;%s&gt;’, Students.ID); save(‘Lab01.mat’, ‘example’)

Now we remove the variable <strong>example </strong>from the workspace.

clear example

You can recover the variable <strong>example </strong>to the workspace from the MAT-file, by doing

load(‘Lab01.mat’, ‘example’) display(example)

example =     ‘A variable generated by Student ID &lt;&gt;’

For hardware labs (labs that requires the use of external hardware), it is possible to save result of your manipulation in this manner. The resulting file can be used to re-examine your data, or change your plots.

<h1>Question 1 (4 marks)</h1>

Answer the following questions in the LiveScript. (Observe that if you finish an expression with a semicolon the results will not show in your report. Use semicolons at the end of your expression with the intention to show or hide your answer)

<ul>

 <li>Define a time signal from 0 to 10 seconds, with a time step of 0.1 second.</li>

</ul>

<table width="651">

 <tbody>

  <tr>

   <td width="20"> </td>

   <td colspan="2" width="631">t = [];</td>

  </tr>

  <tr>

   <td width="20"> </td>

   <td colspan="2" width="631">Define a unit signal equals to 1 from 0 to 10 second. (The unit signal should have the same size as time)y<sub>1</sub>(t) = 1,         t ≥ 0</td>

  </tr>

  <tr>

   <td width="20"> </td>

   <td colspan="2" width="631">y1 = [];</td>

  </tr>

  <tr>

   <td width="20"> </td>

   <td width="337">Define a delayed signal equals zero from 0 to 5 sec0,y<sub>2</sub>(t) ={−1,</td>

   <td width="294">onds and to -1 from 5 to 10 seconds.t &lt; 5 t ≥ 5</td>

  </tr>

  <tr>

   <td width="20"> </td>

   <td width="337">y2 = [];</td>

   <td width="294"> </td>

  </tr>

  <tr>

   <td width="20"> </td>

   <td width="337">Define a ramp signal with slope equals 0.1.y<sub>3</sub>(t) = 0.1t,</td>

   <td width="294">t ≥ 0</td>

  </tr>

  <tr>

   <td width="20"> </td>

   <td width="337">y3 = [];</td>

   <td width="294"> </td>

  </tr>

 </tbody>

</table>

<ul>

 <li></li>

 <li></li>

 <li></li>

 <li>Define a decaying exponential signal with time constant of 10 second.</li>

</ul>

t

−

y<sub>4</sub>(t) = e <sup>10</sup>

y4 = [];

<ul>

 <li>Plot in the same graph the signals ( y<sub>1</sub>(t) , y<sub>2</sub>(t) , y<sub>3</sub>(t) , and y<sub>4</sub>(t) ) versus the time signal.</li>

</ul>

<table width="651">

 <tbody>

  <tr>

   <td width="651">figure; hold on% Fill in your plots commandtitle(sprintf(‘Student ID %s – Question 1 – Signals’, Students.ID)); xlabel(‘Time (seconds)’) ylabel(‘Signals’) grid on; legend(‘y_1(t)’, ‘y_2(t)’, ‘y_3(t)’, ‘y_4(t)’, ‘location’, ‘best’)</td>

  </tr>

 </tbody>

</table>

<h2><strong>3. Laplace transforms</strong></h2>

Recall that the (one-sided) Laplace transform of a function f<sub>(t) </sub>is defined as:

Fstdt

In this section, we will learn how to compute the Laplace and inverse Laplace transforms using <strong>MATLAB</strong>. <em>3.1. Computing Laplace Transform</em>

The command <strong>laplace </strong>in <strong>MATLAB </strong>provides an easy way to calculate the Laplace transform F(s) of a function f(t) . To use <strong>laplace</strong>, first you need to specify that the variable t and s are symbolic ones. This is done with the command:

syms t s

Then, we define the function f(t) .

f = exp(-t)

f =  exp(-t)

Finally, we compute the Laplace transform using the function laplace

F = laplace(f, t, s)




F =




1/(s + 1)




To get more information about the <strong>laplace </strong>function, type:

help laplace

— help for sym/laplace — LAPLACE Laplace transform.     L = LAPLACE(F) is the Laplace transform of the sym F with default     independent variable t.  The default return is a function of s.     If F = F(s), then LAPLACE returns a function of z:  L = L(z).

By definition, L(s) = int(F(t)*exp(-s*t),t,0,inf).

L = LAPLACE(F,z) makes L a function of z instead of the default s:

LAPLACE(F,z) &lt;=&gt; L(z) = int(F(t)*exp(-z*t),t,0,inf).




<table width="653">

 <tbody>

  <tr>

   <td width="653">    L = LAPLACE(F,w,u) makes L a function of u instead of the     default s (integration with respect to w).     LAPLACE(F,w,u) &lt;=&gt; L(u) = int(F(w)*exp(-u*w),w,0,inf).Examples:      syms a s t w x F(t)      laplace(t^5)          returns   120/s^6      laplace(exp(a*s))     returns   -1/(a-z)      laplace(sin(w*x),t)   returns   w/(t^2+w^2)      laplace(cos(x*w),w,t) returns   t/(t^2+x^2)      laplace(x^(3/2),t)    returns   (3*pi^(1/2))/(4*t^(5/2))      laplace(diff(F(t)))   returns   s*laplace(F(t),t,s) – F(0)      See also SYM/ILAPLACE, SYM/FOURIER, SYM/HTRANS, SYM/ZTRANS, SUBS.</td>

  </tr>

 </tbody>

</table>

Often, using <strong>laplace </strong>function gives an expression that is mathematically correct, but not in its simplest form. In such cases, the function simplify can be used to simplify the expression. For example:

simplify(2/(s + 1)-s/(s + 1)^2)

ans =  (s + 2)/(s + 1)^2




To get more information about the <strong>simplify </strong>function, type:

help sym/simplify

<table width="653">

 <tbody>

  <tr>

   <td width="653"> SIMPLIFY Symbolic simplification.     SIMPLIFY(S) simplifies each element of the symbolic matrix S.SIMPLIFY(S,N) or, equivalently, SIMPLIFY(S,’Steps’,N),     searches for a simplification in N steps. The default value of N is 1.         SIMPLIFY(S,’Seconds’,T) aborts the search for a simpler version     at the next end of a simplification step after T seconds. The results     will depend on the speed and system load of your computer and may     not be reproducible. </td>

  </tr>

  <tr>

   <td width="653">    SIMPLIFY(S,’IgnoreAnalyticConstraints’,VAL) controls the level of     mathematical rigor to use on the analytical constraints while simplifying     (branch cuts, division by zero, etc). The options for VAL are TRUE or     FALSE. Specify TRUE to relax the level of mathematical rigor     in the rewriting process. The default is FALSE.         SIMPLIFY(S, ‘Criterion’, ‘preferReal’)     discourages simplify from returning results     containing complex numbers.      SIMPLIFY(S, ‘All’, true)     returns a column vector of aquivalent results. Typically used in     combination with ‘Steps’, N.      Examples:        syms x c alpha beta         simplify(sin(x)^2 + cos(x)^2)  returns  1.        simplify(exp(c*log(sqrt(alpha+beta))))  returns  (alpha + beta)^(c/2).simplify(sqrt(x^2))  returns  sqrt(x^2),        simplify(sqrt(x^2),’IgnoreAnalyticConstraints’,true)  returns  x.u = symunit;        simplify(u.m+u.mm) returns  (1001/1000)*[m].      See also SYMUNIT, SYM/FACTOR, SYM/EXPAND, SYM/COLLECT.</td>

  </tr>

 </tbody>

</table>

<h1>Question 2 (2 marks)</h1>

Write the symbolic expression of the following functions (you can use the symbolic variables <strong>t </strong>and <strong>s </strong>defined previously):

<ol>

 <li>f<sub>1</sub>(t) = δ(t) ( δ(t) is the dirac function, use <strong>help dirac </strong>for more information)</li>

 <li>f<sub>2</sub>(t) = t<sup>2 </sup>+ 4t + 1</li>

 <li>f<sub>3</sub>(t) = te<sup>−t </sup>+ 0.5e<sup>−t </sup>+ e<sup>−3t</sup></li>

 <li>f<sub>4</sub>(t) = sin(2t) + cos<sup>2</sup>(t)</li>

 <li>f<sub>5</sub>(t) = e<sup>−t </sup>sin(5t + <sup>π</sup><sub>3</sub>) + t<sup>2</sup>e<sup>−2t</sup></li>

</ol>

f1 = [] f2 = [] f3 = [] f4 = [] f5 = []

f1 =      [] f2 =      [] f3 =      [] f4 =      [] f5 =      []

<h1>Question 3 (2 marks)</h1>

Use <strong>MATLAB </strong>to compute the Laplace transform of the functions defined in <em>Question 2</em>. Use <strong>simplify </strong>to simplify the symbolic expression if needed.

F1 = []

F2 = []

F3 = []

F4 = []

F5 = []

F1 =

[]

F2 =

[]

F3 =

[]

F4 =

[]

F5 =

[]

<h2>3.2. Computing inverse Laplace transforms</h2>

The function <strong>ilaplace </strong>computes the inverse Laplace transform. Consider the Laplace transform <strong>F </strong>computed earlier. We can compute the inverse Laplace transform (note that the <strong>t </strong>and <strong>s </strong>are already defined as symbols) Example

ilaplace(F, s, t);

<h1>Question 4 (2 marks)</h1>

Use <strong>MATLAB </strong>to calculate the inverse Laplace transform of the following expressions. Use <strong>simplify </strong>to simplify the symbolic expression if needed.

<ol>

 <li>G<sub>1</sub>(s) =</li>

 <li>G<sub>2</sub>(s) =</li>

 <li>G<sub>3</sub>(s) =</li>

 <li>G<sub>4</sub>(s) =</li>

 <li>G<sub>5</sub>(s) = 22(s+1)(s +24)</li>

</ol>

(s +4s+1)(s +9)

G1 = [];

G2 = [];

G3 = [];

G4 = []; G5 = [];

g1 = [] g2 = [] g3 = [] g4 = [] g5 = []

g1 =      [] g2 =      [] g3 =      [] g4 =      [] g5 =

[]