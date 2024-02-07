".ps1" extension for PowerShell

\test.ps1 to run it (have to follow file path)

run by pressing F5

  
  

[CmdletBinding()]

param ( #important

[Parameter(Mandatory=$True)] - this makes the parameter ask for a value if there is none

[string]$computername, - this will ask the user for the value of $computername

[ValidateSet(2,3)] - this only allows 2 or 3 as the input for $drivetype

[int]$drivetype = 3

) - called a parameter block (parameterizing)

  

documentation is good - use <# .... text here .... #> to do a text block

  

input and output:

  

Read-Host "type something" - this writes "type something" to the user and waits for a response **| results are in a string**

if you want to make a dialogue box:

[void][System.Reflection.Assembly]::LoadWithPartialName('Microsoft.VisualBasic') - this initiates the box

  

[Microsoft.VisualBasic.Interaction]::Inputbox('Enter computer name','Computer name dialog box', 'text input')

  

Write-Host "colours!" -foreground yellow -background black - used for displaying output | -fore and -back are not needed

  

Write-Warning - gives a warning - has "WARNING:" text

Write-Verbose - gives extra info - has "VERBOSE:" text

Write-Debug - gives debug info - has "DEBUG:" text

Write-Error - gives error message

  

$var = "server-r2" - this is how to make a variable

  

${My Variable} - this makes a variable that has a space in it ( needs curly brackets )

to find what type a variable is:

"Server-R2" | GM or "server-r2".getType()

  

**single quotes are taken as literal text**

**double quotes allow variables to read what they contain**

**backtick skips 1 character**

  

$var = **'**what does $computer contain?**'**

what does $computer contain?

  

$var = **"**what does $computer contain?**"**

what does Server-R2 contain?

  

$var = "`$computername contains $computername"

$computername contains server-r2

  

**how to turn a string into an int:**

[int]$number = read-host "enter a number"

$number.getType()

TypeName: System.Int32

  

declaring variable types: **best practice for if your variable is going to be a specific type of type**

[int] - integer

[single] - float with 1 decimal places

[double] - float with 2 decimal places

[string] - string of characters

[char] - exactly 1 character

[xml] - xml document

[adsi]

  

removing variable:

Remove-Variable

  
  

declaring multiple objects in a single variable:

$computers = 'SERVER-R2','SERVER1','localhost'

$computers

SERVER-R2

SERVER1

localhost

  

^ this is an array

  

we can access specific elements of the array by using square brackets - **remember it starts at 0, you can use -1 for last, and -2 as second last**

ex.

$computers[1]

SERVER1

  

**using $_. to iterate:**

$computers | ForEach-Object { $_.ToLower() }

server-r2

client1

localhost

  

$computers | ForEach-Object { $_.ToUpper() }

SERVER-R2

CLIENT1

LOCALHOST

  

scopes:

- the shell itself is the top-level scope called "global scope"
- a script is called a "script scope"
- the script scope is considered a "child" of the global scope

  

**main PS rule for scope:** #important

trying to access a scope element

- PS checks to see if it exists within the current scope
- if it doesn't it checks the current scope's parent
- keeps going up until it gets to global scope

for ex.

**in scope.ps1**

$x

  

**in a normal PS window**

C:\scope.ps1

(output is nothing)

  

$x = 4

C:\scope.ps1

(output is:) 4 **this is because PS is going to the global scope (of the normal PS window)**

  

**however:**

**in scope.ps1**

$x = 10

$x

  

**normal PS window**

C:\scope.ps1

(output is:) 10

$x = 4

C:\scope.ps1

(output still:) 10 **this is because PS is going to the script scope, NOT the global scope**

  

**when making functions:**

you might run into name issues with PS functions having the same name

- prefix the function name with initials > Get-QPNetinfo

  

Function Get-QPNetinfo { - makes the function

code here￼}

  

Get-QPNetinfo - calls the function

  

you can pull another script into the one you're using:

.C:\commands.ps1 - this pulls commands.ps1 into the scope you are using

  

. .C:\commands.ps1 - this opens the commands.ps1 as its own scope