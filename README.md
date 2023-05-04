Download Link: https://assignmentchef.com/product/solved-cs52-programming-assignment-2
<br>
Programming Assignment 2 (100 Points): C++ Strings, References &amp; Functions

Assignment Introduction:

Assignment 2 will extend the functionality from Assignment 1 and require that Assignment 1’s code be refactored to use functions with reference parameters. Refer to this handout for details about how to complete Assignment 2.

Refactoring and Adding Features to A1:

Use your code from Assignment 1 to write a program to encrypt and decrypt a plaintext (p) string of upper-case &amp; lower-case letters, the digits 0-9 and two special characters, @,$. The plaintext will not contain spaces or other characters (e.g.#,etc.). Refer to the codebook array for all the allowable characters.

Just like in Assignment 1, your program will accept command line arguments to allow the user to enter in a key value <em>k</em>, a plaintext string of characters just described (−<em>p</em>) or a ciphertext (−<em>C</em>) and exactly one of the options to encrypt (−<em>E</em>) or decrypt (−<em>D</em>). Refer to the example usage on page 3 for how to run the program using the command line arguments and the skeleton code on page 4 for a general outline of the code.

Program Description and Functionality: Provide the following in your source file:

<ol>

 <li>Comments at the top of your .cpp file.</li>

 <li>A main function with command line arguments main(int argc, char* argv[])</li>

 <li>Use only C++ headers that place all standard-library routines in namespace For C++ strings use #include &lt;string&gt;; for standard input and output use #include &lt;iostream&gt; to access std::cout;std::cin; and use #include &lt;cstring&gt; for C-style string functions like std::strcmp and std::strlen and if needed #include&lt;cstdlib&gt; for helper functions like std::atoi, etc.</li>

 <li>The use of command line arguments (int argc, char* argv[]) to get the plaintext (-p sometext) or cipher text (-C zvtl0l40), the shift amount −<em>k </em>7 and the options to encrypt (-E) or decrypt (-D).</li>

 <li>New for A2: The program needs to work for upper-case &amp; lower-case letters, digits 0-9, &amp; the symbols @ and $. Refer to the declaration of A1’s alphabet digits renamed to codebook for assignment 2:</li>

</ol>

char codebook[] =

{

’a’,’A’,’b’,’B’,’c’,’C’,’d’,’D’,’e’,’E’,’f’,’F’,’g’,’G’,’h’,’H’,’i’,’I’,

’j’,’J’,’k’,’K’,’l’,’L’,’m’,’M’,’n’,’N’,’o’,’O’,’p’,’P’,’q’,’Q’,’r’,’R’,

’s’,’S’,’t’,’T’,’u’,’U’,’v’,’V’,’w’,’W’,’x’,’X’,’y’,’Y’,’z’,’Z’,’0’,’1’,

’2’,’3’,’4’,’5’,’6’,’7’,’8’,’9’,’@’,’$’

};

<ol start="6">

 <li>New for A2: Write at least three functions, encrypt(), decrypt(), &amp; copy_string() with the following function prototypes:</li>

</ol>

<table width="630">

 <tbody>

  <tr>

   <td width="431">//</td>

   <td width="46"></td>

   <td width="37"></td>

   <td width="73"></td>

   <td width="43"></td>

  </tr>

  <tr>

   <td width="431">// where plaintext and k are the values parsed// and s is a reference to a string// void encrypt(std::string&amp; plaintext, int k);//</td>

   <td width="46">from</td>

   <td width="37">the</td>

   <td width="73">command</td>

   <td width="43">line</td>

  </tr>

  <tr>

   <td width="431">// where ciphertext and k are the values parsed// and s is a reference to a string// void decrypt(std::string&amp; ciphertext, int k);//// function to copy a cstring to a C++ string</td>

   <td width="46">from</td>

   <td width="37">the</td>

   <td width="73">command</td>

   <td width="43">line</td>

  </tr>

  <tr>

   <td width="431">// s is a reference to either the plaintext or// text is the command line cstring from argv// void copy_string(std::string&amp; s, char* text);</td>

   <td colspan="3" width="156">ciphertext string</td>

   <td width="43"></td>

  </tr>

 </tbody>

</table>

<ol start="7">

 <li>To encrypt a plaintext string use the following formula to compute an index <em>i </em>into the codebook with length #define CBL 64 //Code Book Length:</li>

</ol>

<em>C<sub>i </sub></em>= <em>E</em>(<em>p</em>) = (<em>p </em>+ <em>k</em>) mod <em>CBL,</em>

where <em>mod </em>is the modulus operator %, C is the ciphertext, <em>E </em>is the encryption function, <em>p </em>is the index of the plaintext character, <em>k </em>is the key shift, and <em>CBL </em>is the length of the codebook array.

<ol start="8">

 <li>To decrypt a ciphertext string use the following formula to compute an index <em>i </em>into the codebook array:</li>

</ol>

<em>p<sub>i </sub></em>= <em>D</em>(<em>C</em>) = (<em>C </em>− <em>k</em>) mod <em>CBL, </em>(<em>C </em>− <em>k</em>) <em>&gt;</em>= 0 <em>p<sub>i </sub></em>= <em>D</em>(<em>C</em>) = (((<em>C </em>− <em>k</em>) mod <em>CBL</em>)+ <em>CBL</em>) mod <em>CBL, </em>(<em>C </em>− <em>k</em>) <em>&lt; </em>0

where <em>mod </em>is the modulus operator %, C is the index of the ciphertext character, <em>D </em>is the decryption function, <em>p </em>is the plaintext, <em>k </em>is the key shift, and <em>CBL </em>is the length of the codebook array.

In C &amp; C++, mod, or remainder of division, is the % symbol. For negative <em>C </em>− <em>k </em>numbers refer to the references on page 4 for more details about the modulus operator in C++ with negative numbers.

Example usage:

<table width="446">

 <tbody>

  <tr>

   <td width="244">&gt;A02.exe -p @Bc -k 3 -EThe plaintext was: @Bc The ciphertext is: AdD enter any key to exit</td>

   <td width="202">//encrypt the string @Bc</td>

  </tr>

  <tr>

   <td width="244">&gt;A02.exe -C AdD -k 3 -DThe ciphertext was: AdD The plaintext is: @Bc enter any key to exit</td>

   <td width="202">//decrypt the string AdD</td>

  </tr>

  <tr>

   <td width="244">&gt;A02.exe -k 5 -p 7$9 -EThe plaintext was: 7$9 The ciphertext is: acb enter any key to exit</td>

   <td width="202">//encrypt the string 7$9</td>

  </tr>

  <tr>

   <td width="244">&gt;A02.exe -C acb -k 5 -DThe ciphertext was: acb The plaintext is: 7$9 enter any key to exit</td>

   <td width="202">//decrypt the string acb</td>

  </tr>

  <tr>

   <td width="244">&gt;A02.exe -p sometext -k 7 -EThe plaintext was: sometext The ciphertext is: VRPHWH1W enter any key to exit</td>

   <td width="202">//encrypt the string sometext</td>

  </tr>

  <tr>

   <td width="244">&gt;A02.exe -C VRPHWH1W -k 7 -DThe ciphertext was: VRPHWH1W The plaintext is: sometext enter any key to exit</td>

   <td width="202">//decrypt the string VRPHWH1W</td>

  </tr>

 </tbody>

</table>

&gt;A02.exe -k 9 -E -p tH1s1sv3ryYc00l //encrypt the string tH1s1sv3ryYc00l

The plaintext was: tH1s1sv3ryYc00l The ciphertext is: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="6a32072a3d">[email protected]</a>@WZaV56G99P enter any key to exit

&gt;A02.exe -C <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="095164495e">[email protected]</a>@WZaV56G99P -k 9 -D //decrypt the string <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="257d486572">[email protected]</a>@WZaV56G99P

The ciphertext was: <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="124a7f5245">[email protected]</a>@WZaV56G99P The plaintext is: tH1s1sv3ryYc00l enter any key to exit

Skeleton code

<table width="269">

 <tbody>

  <tr>

   <td width="241">//</td>

   <td width="28"></td>

  </tr>

  <tr>

   <td width="241">// Name: Your First Name &amp; Last// SSID: Student ID Number// Assignment #: 2// Submission Date: 10/3/2020</td>

   <td width="28">Name</td>

  </tr>

 </tbody>

</table>

//

// Description: A program to encrypt and decrypt a message using a shift cipher

// The plaintext message must only contain lowercase alpha and digits 0-9

//

// command line arguments

// -p theplaintextmessage1 – the plaintext (p) message to be encrypted

// -C 2qnyujrw2n62vn11jpna – the cipher (C) text to be decrypted

// -k 9                                                                       – the key (k) shift value

// -E                                                                         – the option to encrypt (E)

// -D                                                                         – the option to decrypt (D)

//

#include &lt;iostream&gt; //std::cout, std::cin, etc.

#include &lt;cstdlib&gt; //C++ version of stdlib.h

#include &lt;cstring&gt; //C++ version of string.h #include &lt;string&gt;

// Todo A2: encrypt using std::string void encrypt(std::string&amp; plaintext, int k);

// Todo A2: decrypt using std::string void decrypt(std::string&amp; ciphertext, int k);

// Todo A2: helper function to copy a cstring to an std::string

<table width="608">

 <tbody>

  <tr>

   <td width="31">void</td>

   <td width="578">copy_string(std::string&amp; s, char* text);</td>

  </tr>

  <tr>

   <td width="31">int{</td>

   <td width="578">main(int argc, char *argv[])// Example variables for A02int k = 0;                                                   // k shiftint msg_index = 0;        // msg_index of plaintext or ciphertext in argv std::string msg;           // string to hold the plaintext or ciphertext; bool do_encrypt = false; //True for encrypt or False for decrypt//// A1: process the command line arguments//// Todo A2: copy argv into msg using copy_string function</td>

  </tr>

 </tbody>

</table>

//

// Todo A2: call encrypt or decrypt functions

//

if (do_encrypt)                                     //encrypt plaintext

encrypt(msg, k);

else decrypt(msg, k);//decrypt ciphertext

//

// Todo A2:

// print the original message and the plaintext | ciphertext

//

return 0; }//main

Where to do the assignment

You can do this assignment on your own computer, or using the SMC Virtual labs with Citrix. In either case, ensure the code compiles and runs on Windows. Submit one .cpp file named A02.cpp. Do not use any other name or else points will be deducted.

Submitting the Assignment

Include your name, your student id, the assignment number, the submission date, and a program description in comments at the top of your files, and use the CS52 Programming Guide for coding style guidance. Submit the assignment on <a href="https://online.smc.edu/">Canvas</a> <a href="https://online.smc.edu/">(</a><a href="https://online.smc.edu/">https://online.smc.edu</a><a href="https://online.smc.edu/">)</a> by uploading your .cpp file to the Assignment 2 entry as an attachment. Do not cut-and-paste your program into a text window. Do not hand in a screenshot of your program’s output. Do not hand in a text file containing the output of your program.

Saving your work

Save your work often on a flash-drive or to the cloud (e.g., GoogleDrive, Microsoft OneDrive, Canvas, etc.). Always save a personal copy of your files (e.g. .cpp, .h, etc.). Do not store files on the virtual lab computers.

References:

<a href="https://docs.microsoft.com/en-us/cpp/cpp/cpp-language-reference">Microsoft C++ Language Reference</a>

<a href="https://isocpp.org/std/the-standard">ISO C++ Standard Library and other refs</a>

<em>’The modulus operator yields the remainder given by the following expression, where </em><em>e is the first operand and </em><em>e</em>2 <em>is the second: </em><em>e</em>1 − (<em>e</em>1<em>/e</em>2) ∗ <em>e</em>2<em>, where both operands are of integral types.’ </em><a href="https://docs.microsoft.com/en-us/cpp/cpp/multiplicative-operators-and-the-modulus-operator?view=vs-2019">Microsoft C++ Modulus &amp; Multiplication Operators</a>