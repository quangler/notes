import sys # importing for command line arguments

import os # importing to manipulate files

import platform # importing to see operating system stats

import datetime # importing for time and date

  
  

def main(): # starts the code

initial_input()

  
  

def error_detected(): # function that gets called if there is an error

print("\nPlease run the program again with the correct arguments and try again.\n(Format: initial file path, output file path)")

quit()

  
  

def initial_input(): # function that checks for correct num of arguments

print("You have entered:", len(sys.argv) - 1, "argument(s).")

if len(sys.argv) != 3: # incorrect num of args

print("Expected arguments: 2")

error_detected()

elif len(sys.argv) == 3: # correct num of args

print("\nYou have input the correct number of arguments.")

initial_file_detector()

  
  

def initial_file_detector(): # function that checks if initial path exists (using first argument / second element)

if os.path.exists(sys.argv[1]):

print("\nYour initial path exists! (" + sys.argv[1] + ")")

second_file_checker()

elif not os.path.exists(sys.argv[1]):

print("Your initial path does not exist. (" + sys.argv[1] + ")")

error_detected()

  
  

def second_file_checker(): # function that checks if second file exists

if ".txt" not in sys.argv[2]: # adds ".txt" at the end of the file if it doesn't have it already

sys.argv[2] = sys.argv[2] + ".txt"

  

if os.path.exists(sys.argv[2]) and "\\" in sys.argv[2]: # file EXISTS in SPECIFIED path

print("\nOutput file already exists in this location.\n(" + sys.argv[2] + ")")

overwrite_file()

  

elif os.path.exists("C:\\PRGM1000\\" + sys.argv[2]): # file EXISTS in NON-SPECIFIED path

print("\nOutput file already exists in this location.\n")

sys.argv[2] = ("C:\\PRGM1000\\" + sys.argv[2]) # changes second argument to include path

overwrite_file()

  

elif not os.path.exists(sys.argv[2]) and "\\" in sys.argv[2]: # NEW file in SPECIFIED path

print("\nNo file with that name has been created in this location. Creating it now.")

temp_file = open(sys.argv[2], "w") # creates the file with the new name

temp_file.close()

file_process_header()

  

elif "\\" not in sys.argv[2]: # NEW file in NON-SPECIFIED path

print("\nNo second file path could be found. (Creating now at 'C:\PRGM1000\\" + sys.argv[2] + ")")

if not os.path.exists("C:\\PRGM1000\\"): # creates the C:\PRGM1000 folder if it doesn't exist

os.mkdir("C:\\PRGM1000\\")

sys.argv[2] = ("C:\\PRGM1000\\" + sys.argv[2])

temp_file = open(sys.argv[2], "w")

temp_file.close()

file_process_header()

  
  

def overwrite_file(): # function that overwrites file

overwrite_input = input("\nWould you like to overwrite this file? (Y/N)\n")

if overwrite_input.casefold() == "y" or overwrite_input.casefold() == "yes":

temp_file = open(sys.argv[2], "w") # overwrites file

temp_file.close()

file_process_header()

elif overwrite_input.casefold() == "n" or overwrite_input.casefold() == "no":

new_file()

  
  

def new_file(): # function that renames the file

new_file_name = input("\nPlease enter the name of the new file: ")

if ".txt" not in new_file_name: # user didn't put ".txt" at end of file

path_name = sys.argv[2].split("\\")

path_len = len(path_name)

path = "\\".join(path_name[0:path_len - 1]) + "\\"

sys.argv[2] = path + new_file_name + ".txt" # adds the path and ".txt" to the new file

if os.path.exists(sys.argv[2]):

print("Sorry, this file name has already been taken.")

new_file() # restarts the loop since name was taken

else:

temp_file = open(sys.argv[2], "w") # creates the file with the new name and path

temp_file.close()

file_process_header()

  

if ".txt" in new_file_name: # user put ".txt" at end of file

path_name = sys.argv[2].split("\\")

path_len = len(path_name)

path = "\\".join(path_name[0:path_len - 1]) + "\\"

sys.argv[2] = path + new_file_name # adds the path to the new file

if os.path.exists(sys.argv[2]):

print("Sorry, this file name has already been taken.")

new_file() # repeats loop since name was taken

else:

temp_file = open(sys.argv[2], "w") # creates the file with the new name and path

temp_file.close()

file_process_header()

  
  

def file_process_header(): # function that adds version, user, and time/date to top of file

date_and_time = datetime.datetime.now().strftime("%d/%m/%Y, %H:%M:%S:%f") # formatting date and time

os_info = ["Operating System:", platform.system(), platform.release(), "\nVersion:",

platform.platform()] # list of operating system info

sys_info = ["\n\nLogged-in user:", os.getlogin(), "\nTime and Date:",

date_and_time] # list of user info and time/date

  

with open(sys.argv[2], "w") as processing_file: # temporarily opens the destination file to write to it

processing_file.writelines(" ".join(os_info))

processing_file.writelines("\n".join(sys_info))

processing_file.writelines("\n\n") # enters the header info (OS, USER, TIME/DATE)

file_process_timestamp()

  
  

def file_process_timestamp(): # function that timestamps each line

date_and_time = datetime.datetime.now().strftime("%H:%M:%S:%f")

initial_file = open(sys.argv[1]).readlines()

  

with open(sys.argv[2], "a") as second_file: # temporarily opens the destination file to append to it

for lines in initial_file:

second_file.writelines(date_and_time + " " + lines)

second_file.writelines("\n") # adds timestamp before the line of text

  
  

main()