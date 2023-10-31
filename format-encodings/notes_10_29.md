# COMP122 Lecture Notes: October 23, 2023

## Announcements:
   1. Assigment 24-bitwise-operations graded.
   1. Assigment 42-checksum graded.
      - Noted Items:
        1. large number of students (18) did not attempt
        1. scores greater than 90: 33 == 42%
        1. not following the process
           - Java --> Java Tac --> MIPS
        1. readability of code
           - direct correlation between   "working code <- and -> readable code"
           - check your tab versus spaces setting.

   1. Assignment 25-binary to be released.
      https://github.com/COMP122/binary-addition/blob/main/assignment.md

## Today's Agenda:
   1. Review from 10/25/2023

   1. Strings and Arrays

   1. [String Processing](https://docs.google.com/presentation/d/1fg9BuWtyZ9PARK0gDE5ZcbjOiudRSrVP2s1iuSIDYXw/edit#slide=id.g199d0a137fe_0_29)


   1. Macros for ASCII Chars (https://www.javatpoint.com/java-string-touppercase)

   1. Conversion ASCII -> Binary


## Questions from Last Lecture/Lab, etc.:
   * M/W @ 9:00 am

   * T/R @ 9:00 am


---
# Today's Lecture Material
  1. Arrays

  1. [String Processing](https://docs.google.com/presentation/d/1fg9BuWtyZ9PARK0gDE5ZcbjOiudRSrVP2s1iuSIDYXw/edit#slide=id.g199d0a137fe_0_29)


  1. String Processing

  1. Java Strings: three independent types
     1. A string is an object that contains an array of characters
     1. A string is an constant array of characters 
     1. A char[] is a fixed sized array of characters

     ```java
      String O = new String( "A string!"); // An object
      String S = "A string!";              // A constant array (+ stuff?)
      char[] A = S.toCharArray();          // An array 
      
      int l    = A.length;                 // A property: Computed or Stored?
      ```

   1. Generalized Structure of a String:
      - See the Drawing on the Board!


   1. MIPS Declaration of a String
      ```mips
             .data
      A:     .ascii "A str
      B:     .ascii "ing!"
             .asciiz "\n"
             .text
      ```


   1. Java: A.length  versus  C: strlen()
      - man strlen
      - man -k string | grep ^str

      ```java

      for(i=0; A[i]!='\0'; i++);
      
      return i;

      ```

   1. Array Indexing
      - x = A[imm]
        - load the address of A into a register
          - `la $t0, A`
        - "load" "byte" into the register
           - lbu x, imm($t0)
      - x = A[i]
        - load the address of A into a register
          - `la $t0, A`
        - modify the address to be A[i]'s address
          - add $t0, $t0, i
        - "load" "byte" into the register
           - lbu x, imm($t0)


   
   | TAC String Equations          | MIPS Instruction          |
   |-------------------------------|---------------------------|
   | `x = A[imm];`                 | `la p, A`                 |
   |                               | `lbu x, imm(p)`           |
   |                               |                           |
   | `x = A[v];`                   | `la p, A`                 |
   |                               | `add p, p, v`             |
   |                               | `lbu x, 0(p)`             |
   |                               |                           |
   | `A[imm] = x;`                 | `la p, A`                 |
   |                               | `sb x, imm(p)`            |
   |                               |                           |
   | `A[v] = x;`                   | `la p, A`                 |
   |                               | `add p, p, v`             |
   |                               | `sb x, 0(p)`              |
   |                               |                           |
   | `p = & A;`                    | `la p, A`                 |
   | `x = (* p);`                  | `lbu x, 0(p)`             |
   | `(* p) = x;`                  | `sb x, 0(p)`              |

  
 

  1. Practicum:  strchr()
     - Prototype: `char[] strchr(char[] A, int c);`
     - Description: locate a char in a string

  ```java
     match:  for(i=0; A[i]!='\0'; i++) {
               if (A[i] == c) {
                 break match;
               }
             }

  ```

                   

  ```java TAC
  ```

 
   1. Macros: for ASCII https://www.javatpoint.com/post/java-character
      - isLowerCase
      - isUpperCase
      - isDigit
      - isLetter
      - toUpperCase
      - toLowerCase

   1. Conversion ASCII -> Binary
      - man atoi
      - isHexDigit()




---
## Resources

      | TAC String Equations          | MIPS Instruction          |
      |-------------------------------|---------------------------|
      | `x = A[imm];`                 | `la p, A`                 |
      |                               | `lb x, imm(p)`            |
      |                               |                           |
      | `x = A[v];`                   | `la p, A`                 |
      |                               | `add p, p, v`             |
      |                               | `lb x, 0(p)`              |
      |                               |                           |
      | `A[imm] = x;`                 | `la p, A`                 |
      |                               | `sb x, imm(p)`            |
      |                               |                           |
      | `A[v] = x;`                   | `la p, A`                 |
      |                               |                           |
      |                               | `add p, p, v`             |
      |                               | `sb x, 0(a)`              |
      |                               |                           |
      | `x = & A;`                    | `la x, A`                 |
      | `x = (* p);`                  | `lb x, 0(p)`              |
      | `(* p) = x;`                  | `sb x, 0(p)`              |


---
<!-- This section for student's to place their own notes. -->
<!-- This section will not be updated by the Professor.   -->

## Notes  


