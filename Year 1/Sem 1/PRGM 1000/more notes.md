def main():

uInput = userInput()

IP = inputValidation(uInput)

validIP = ipCheck(IP)

returnStatement(validIP)

  
  

# Function for when an error has been detected. This function asks if you'd like to retry or not.

def errorDetected():

userAnswer = input("\nWould you like to go back to the main menu and try again? (y/n)\n")

if userAnswer.casefold() == 'y' or userAnswer.casefold() == 'yes':

main()

if userAnswer.casefold() == 'n' or userAnswer.casefold() == 'no':

print("Goodbye.")

exit()

else:

print("Invalid entry, try again.")

errorDetected()

  
  

# Function to check user input. This function checks to see if the user input 'q' or 'quit' and quits.

def userInput():

uInput = input("Please enter a valid IPv4 address (ex. 192.168.1.254), or type 'q' or 'quit' to exit.\n")

if uInput.casefold() == 'quit' or uInput.casefold() == 'q':

print("Goodbye. (user entered", uInput, ")\n")

exit()

else:

return uInput

  
  

# Function to check validation of user input. Checks for correct number of octets, and anything other than digits.

def inputValidation(uInput):

error = 0

IP = uInput.split(".")

if len(IP) != 4:

print("You have an incorrect number of octets. (ex. 1.2.3.4.5 or 1.2.3)")

error = 1

for octet in IP:

if not octet.isdigit():

print("You have an error in octet", IP.index(octet) + 1)

error = 1

if error == 1:

errorDetected()

else:

return IP

  
  

# Function to check if the IP address is valid. Checks for octet value between 0-255 (or 1-255 for first octet), and leading correct octet length.

def ipCheck(IP):

if not 1 <= int(IP[0]) <= 255:

print("Your first octet has an incorrect value. (value not between 1-255)")

errorDetected()

for octet in IP:

if int(octet) > 255 or int(octet) < 0:

print("Octet", IP.index(octet) + 1, "has an incorrect value. (value not between 0-255)")

errorDetected()

elif len(octet) < 1 or len(octet) > 3:

print("Octet", IP.index(octet) + 1, "is the incorrect length.")

errorDetected()

else:

validIP = IP

return validIP

  
  

# Function to give the return statement. Displays it as an IP address, IP class, and bits.

def returnStatement(validIP):

print(validIP, "Is a valid IP address!")

if int(validIP[0]) >= 1 <= 127:

print("This is a class A IP address.")

elif int(validIP[0]) >= 128 <= 191:

print("This is a class B IP address.")

elif int(validIP[0]) >= 192 <= 223:

print("This is a class C IP address.")

elif int(validIP[0]) >= 224 <= 239:

print("This is a class D IP address.")

elif int(validIP[0]) >= 240 <= 255:

print("This is a class E IP address.")

print("This is the value in binary:")

  

for x in validIP:

print("Octet", validIP.index(x) + 1, ":", bin(int(x)))

errorDetected()

  
  

main()