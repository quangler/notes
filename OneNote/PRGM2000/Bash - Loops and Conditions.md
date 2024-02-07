**General syntax for if:**

if command-list1

then

command-list2

fi

  

Or

  

if command-list1; then command-list2; fi

  

OR

  

Command1 && command2 - does the same as an if and then

  

Command1 || command2 - runs command2 if command1 is a success

  
  

Failed code uses an error code of 1-255, successful code returns 0

0 = True, 1-255 = False

  

Exit _n_ - will set the return value

  

"test" and "["/"]" - are essentially the same

- Evaluates conditions then exits with a status based on result

Test option filename - this is the syntax

ex. test -t 1; echo $? - 0 means no redirection of stdout

OR

[-r "$FILE"]; echo $? - 0 means file exists and readable

  

NAME=John

Test "$NAME" = Bill (IDK WHAT THIS DOES???)

  
  

**Testing integer Expressions:**

Same as powershell

-eq, -ne, -lt, -le, -gt, -ge

  

! = not

-a = and

-o = or

  

**Else statement:**

if command-list1

Then

Command-list2

Else

Command-list3

Fi

  

**Elif statement:**

If command-list1

Then

Command-list2

Elif command-list3

Then

Command-list4

Else

Command-list5

Fi

  

Indent for readability

  

**Case Statement: basically a switch**

Case word in

Pattern1) command-list

;;

Pattern2) command-list

;;

Pattern) command-list

;;

Esac

  

**FOR loop:**

for NAME in LIST

Do

Command-list

Done

  

Or

  

For NAME

Do

Command-list

Done

  

**WHILE loop:**

While command-list1

Do - command-list2 is run as long as command-list1 has an exit code of 0 (no errors)

Command-list2

Done

  

**UNTIL loop:**

Until command-list1

Do - command-list2 is run as long as command-list1 has an exit code NOT EQUAL to 0

Command-list2

Done

  

**IO redirection**

For NUMBER in 1 2 3 4

Do

Echo $NUMBER

Done > myfile.txt

  

While read LINE

Do

Echo $LINE

Done < myfile.txt

  

**BREAK / CONTINUE**

Break - kill loop

  

Continue - restart loop

  
  
  
  

**#CASE EXAMPLE**

#!/bin/bash

  

echo -n "Enter the name of a country: "

read COUNTRY

  

echo -n "The official language of $COUNTRY is "

  

case $COUNTRY in

  

Lithuania)

echo -n "Lithuanian"

;;

  

Romania | Moldova)

echo -n "Romanian"

;;

  

Italy | "San Marino" | Switzerland | "Vatican City")

echo -n "Italian"

;;

  

*)

echo -n "unknown"

;;

esac