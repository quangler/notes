in an "if" statement:

- the first thing evaluated is the part in (normal brackets)
- if the value is true then the script is run

  

difference between foreach and foreach-object

- foreach loads everything into ram immediately | faster but uses more ram

foreach ($<item> in $<collection>){

<statement>

}

  

  
- foreach-object does everything one by one | slower but uses less ram

foreach-object {$_.<variable name>}

  
  
  

$condition = $true

if ($condition){

<code here>

}

  

**^ this will run**

  

$condition = $false

if ($condition){

<code here>

}

  

**^ this will not**

  

**Switch statement:** #important

  

$day = 3

Switch ($day){

0{$result = 'Sunday'}

1{$result = 'Monday'}

2{$result = 'Tuesday'}

3{$result = 'Wednesday'}

... etc.

default{'unknown'}

}

  

**you can also replace the integers with strings**

  

**Arrays:** #important

$roles = @('DHCP','ADDS','SQL','WebServer')

  
  

**For Loops:**

for (<init>; <condition>; <repeat>) {

<code>

}

  

ex.

for($count = 0; $count -le 5; $++){

$count

}

**^ this loop will go 5 times, since it is checking to see if the count is less than or equal to 5**

  

While is a pre-test loop - meaning it checks if the condition is true before running

  

Do-While and Do-Until are post-test loops - will run once before checking condition to see if its true

  

"break" will eject you from the current block