# Project 1c: Email Address Parser 

Often times, you may be given a list of raw email addresses and be asked to generate meaningful information from such a list. This project involves parsing such a list and generating names and summary information from that list. 

The script, `address_master.py`, should: 

1.  Open the file specified as the first argument to the script (see below)
2.  Read the file one line at a time (i.e., for line in file--each line will be a separate email address) 
3.  Print (to the screen) a line that "interprets" the email address as described below 
4.  When finished, display the total number of email addresses and a count unique domain names 

Each email address will either be in the form "first.last@domain.ext" OR "ilast@domain.ext", where "first" and "last" are the first and last names of the person respectively, and "i" is the first initial. Each "line" (step 4) should contain the email address itself, the domain name of the email address, and the "full" name (either "Last, First" or "Last, I." where "I" is the first initial. The name components should be in "title case" (capitalize first letter of all words/initials). So for example, the following two email addresses in the input file: 
```
doe.deer@re.mi 
irobot@sneaker.net 
```
should result in the following printed to the screen: 
```
doe.deer@re.mi                     re.mi               Deer, Doe
irobot@sneaker.net                 sneaker.net         Robot, I.
```
Allow 35 characters for the email address, 20 characters for the domain name, and 25 characters for the full name for a total of 80 characters wide per line of output. All fields should be left aligned (that's the default for strings). 

## REQUIRED IMPLEMENTATION NOTES 

1.  You MUST abstract your most useful logic by creating a function named `email_parse` that takes an email address as a parameter and prints the line formatted as described above. This function should be "called" as your step 3 above, which will make the main script much cleaner. So to reiterate, the following function MUST be in your code: 
    ``` 
            def email_parse(address): 
                ... DO STUFF HERE ...
    ``` 

2.  You MUST use either the format() function or an f-string to format your lines of text. In other words, you __cannot__ use the center(), ljust() and rjust() methods. Those methods are okay, but don't use them here.

3.  You MUST modify emails.txt, and add your own email address at the bottom as first.last@augusta.edu. __JUST edit and save the file using VS code or another text editor. No Python code required here.__

4.  You MUST run your script against the file `emails.txt` and redirect the output to `parsed_emails.txt`. In other words, you should run `python address_master.py emails.txt > parsed_emails.txt`. This file should be in your final submission. __DO NOT WRITE TO A FILE INSIDE OF YOUR SCRIPT. ONLY READ AND PRINT. WRITING OCCURS HERE BY REDIRECTING OUTPUT.__ 

    *Note: If you do output redirection in Windows Powershell (the default shell for VS Code), it outputs writes the file using Unicode, which can cause issues. Use a standard Command Prompt (cmd.exe) if running this in Windows. Should not have any issues on Mac or Linux (and thus Mimir).*

When done, be sure to test the heck out of this and then submit the __project1 directory__ in Mimir.

## OPTIONAL CHALLENGES 

1.  Create a second version of the script, address_master_2.py. This version should import the email_parse function from first version (`from address_master import email_parse`). Instead of asking for a file name and reading the text from the file, instead read in the text line-by-line from `sys.stdin`. This should allow you to run it interactively AND to pipe in text from another command (e.g., `type emails.txt | python emailparser2.py`). 

2.  Improve the "logic" for `email_parse` to remove any numbers (digits) from the name before running your "rules." So for instance, `dcunningham12@rasa.net` would parse to a name of "Cunningham, D." (dropping the "12").

3.  Improve the logic of `email_parse` to ALSO capitalize the third letter of any name that starts with `Mc`. So for instance `Mcshady` whould become `McShady`.

## HINTS 

1.  The "arguments" to a python program are in the sys.argv list. The first element in the list is the name of the script and the rest are any additional words (arguments) added to the end. [See here for explanation](https://www.tutorialspoint.com/python/python_command_line_arguments.htm). The code needed may look as follows:
    ```
    import sys

    filename = sys.argv[1]
    ```
