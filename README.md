# Writups-Cryptonite

Writeup compilation for Bandit attempt

<hr>

## Misc

### Resources used to brush up on topics
<a href='https://www.markdownguide.org/basic-syntax/'> Markdown </a>


# Level 0

## Steps taken
1. Booted into ParrotOS on a vm logged into parrotOS terminal
2. connected to Bandit server using <b>bandit0</b> username

## Issues Faced
> Connection issue as i used *v3sper@bandit.labs.overthewire.org -p 2220* to login initially

> ### Mitigation steps
> switched v3sper to bandit0 (server knows bandit0 username not my [v3sper] username)




# Level 1

## Steps taken
1. used commmand *ls* to find the readme file
2. used *cat readme* to oepn readme and extract password
3. logged out of bandit0 and logged into bandit1 using the given <a href='NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL'>password</a>

## Issues Faced
> none

> ### Mitigation steps



# Level 2

## Steps taken

1. Found the *-* file using the **ls** command
2. Extracted the <a href='rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi'>password</a> using **cat *./*-**

## Issues Faced

> unable to open the dash file using the **cat** command only

> ### Mitigation steps
> instead of using *cat -* used *cat **./**-*
> #### Reference taken from
> <a href='https://unix.stackexchange.com/questions/189251/how-to-read-dash-files'>Stackexchange</a>



# Level 3

## Steps taken

1. Logged in using the previous level's answer
2. Found the *spaces in this filename* file using the **ls** command
3. Extracted the <a href='aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG'>password</a> using **cat** command
    >I wrote cat and typed in sp and hit the **tab** key on the keyboard which led to the autofill of the filename [command = *cat spaces\ in\ this\ filename* ]

## Issues Faced

> none

> ### Mitigation steps



# Level 4

## Steps taken

1. Logged in using the previous level's answer
2. Found the *inhere* directory using the **ls** command, opened it using the **cd** command [ ***cd*** *inhere* ]
3. Used the find command to find the hidden file(s):
    > Found 2 files 
        >.
        > ./.hidden
4. Found the password for the next level in the *./. hidden* file
5. Extracted the <a href='2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe'>password</a> using the **cat** *./.hidden* command

## Issues Faced

> none

> ### Mitigation steps



# Level 5

## Steps taken

1. Logged in using the previous level's answer
2. Found the *inhere* directory using the **ls** command, opened it using the **cd** command [ ***cd*** *inhere* ]
3. Found 10 files 
    > -file00
    > -file01
    > -file02
    > -file03
    > -file04
    > -file05
    > -file06
    > -file07
    > -file08
    > -file09
4. Found the password for the next level in the *./-file07* file
5. Went through all the given files using the **cat** command
6. Extracted the <a href='lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR'>password</a> using the **cat** *./-file0x* command where x = file no. where the file was found [ 07 ]

## Issues Faced

> none

> ### Mitigation steps



# Level 6

## Steps taken

1. Logged in using the previous level's answer
2. Found the *inhere* directory using the **ls** command, opened it using the **cd** command [ ***cd*** *inhere* ]
3. Found 18 directories 
    > maybehere00
    > maybehere01
    > maybehere02
    > maybehere03
    > maybehere04
    > maybehere05
    > maybehere06
    > maybehere07
    > maybehere08
    > maybehere09
    > maybehere10
    > maybehere11
    > maybehere12
    > maybehere13
    > maybehere14
    > maybehere15
    > maybehere16
    > maybehere17
4. Used the **cd** command to scan through each directory
5. Found the password for the next level in the *maybehere07* file
> Went through all the given files using the **cat** command
> Tedious process
> Reffered to google and other sources to learn a different method to find the solution more efficiently.
6. Extracted the <a href='P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU'>password</a> using the **find ./ -type f -size 1033c ! -executable** command where x = file no. where the file was found [07]

## Issues Faced

> way too many directories need to be opened
    > need to find an efficient way to open multiple directories
    > this will save time and increase efficiency

> ### Mitigation steps
    >used **find /dir1 /dir2 -type f** command from <a href='https://www.cyberciti.biz/faq/how-to-search-multiple-directories-with-find-command/#:~:text=So%20you%20want%20to,directories%20but%20not%20all%20folders.&text=nixCraft%20is%20a%20one%2Dperson%20operation.'>cyberciti</a>
        >here */dir1 /dir2* are equal to *maybhere0x maybehere0(x+1)*
    >used **find ./ -type f -size 1033c ! -executable** which ultimately helped me find the password perfectly
        > learnt the method from <a href='https://mayadevbe.me/posts/overthewire/bandit/level6/'>mayadevbe</a> and <a href='https://medium.com/secttp/overthewire-bandit-level-5-f2df304da190'>medium</a>. 
    >***NOTE*:** Searching google for *how to find a specific file in a directory using unix/linux commands didnt work.
    


# Level 7

## Steps taken

1. Logged in using the previous level's answer
2. used **find -user bandit7 -group bandit6 -size 33c -executable** but didn't find any file
3. used **find / -user bandit7 -group bandit6 -size 33c 2>/dev/null** to locate directory with the file containing password

4. Extracted the <a z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S'>password</a> using the **cat** */var/lib/dpkg/info/bandit7.password* command.

## Issues Faced

> unable to locate file on server.

> ### Mitigation steps
>used chat gpt and <a href='https://exploreinformatica.com/how-to-exclude-all-permission-denied-messages-when-using-find-command/'>exploreinformatica</a> to find what am i missing in the command
   - gpt advises to add a descriptor for standard error and and **/dev/null** to remove any files which  contain a standard error
    
#### More thoughts
>still unable to undestand how **/dev/null** works.


# Level 8

## Steps taken

1. Since we are searching for a string here, we need to use the grep command.
    - `grep "millionth" data.txt`

2. output shows the line containing the word *millionth* in the text file ***data.txt*** and provides the <a href='TESKZC0XvTetK0S9xNwm25STk5iWrBvP'>password</a> for the next level.

## Issues Faced

### Mitigation steps



# Level 9

## Steps taken

1. used **uniq**
2. we can filter adjacent matching lines using this command.
3. Hence we sort the data first. 
4. command used: 
- `cat data.txt | sort | uniq`


## Issues faced
>grep does not give any option of counting the occurrence of a particular line of text.
>upon using `cat data.txt | sort | uniq` desired result isnt shown (buttload of results shown) because if no options are given with the uniq command, matching lines are merged to the first occurrence.

### Mitigation steps
>use **uniq** along with the *-u* option which prints unique lines.
- `cat data.txt | sort | uniq -u`

>This give the desired <a href='EN632PlfYiZbn3PhVK3XOGSlNInNE00t'> password</a>



# Level 10

## Steps taken

1. find human-readable strings in the file. 
2. use the **strings** command, which extracts human-readable text.
3. ##### The string also needs to have '=' in it
4. to search for '=' in a string use the **grep** command. 
5. final command = 
- `strings data.txt | grep "="`

6. upon execution of this command the result is a list of strings with '=' sign in them, 
7. one that starts with multiple '=' signs, is our <a href='G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s'>password</a>.

## Issues faced

### Mitigation steps



# Level 11

## Steps taken

1. As per clue -> data is base64 encoded. 
hence use **base64 decode** command.
2. Then use `cat data.txt | base64 -d` command to get the desired output:
` The password is **6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM** `

## Issues faced

### Mitigation steps



# Level 12

## Steps taken

1. **Position rotation**
2. first cat out the file and then pipe it to the tr command, which does the cipher decoding.
- `cat data.txt | tr a-zA-Z n-za-mN-ZA-M`
3. this gives the required output: `The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv`

***NOTE:***
a-z represents lowercase and A-Z represents uppercase input(s) respectively, and n-za-m is the corresponding lowercase output [a+13 characters is n, and this is a symbolic way of writing all letters without actually having to list them individually. n-za-m means letters from n to z and then a to m].

## Issues faced
> Understanding what is a Rot13 cipher -> a special case of Caesar cipher. 

### Mitigation steps
> used the 'tr' command.
    > The tr command is a UNIX command-line utility for translating or deleting characters.


# Level 12 → Level 13

## Steps Taken

1. Create a directory under /tmp: `mkdir /tmp/idk`.
2. Copy data.txt to the new directory: `cp data.txt /tmp/idk`.
3. Reverse the hexdump and save it as "bandit" using xxd: `xxd -r data.txt > bandit`.
4. Identify the compression method by checking the file type using the `file` command.
5. Decompress the file accordingly, changing extensions and using commands such as `mv`, `gunzip`, `bzip2`, and `tar -xf`.
6. Repeat until you reach the end and find the password.

## Passwords

The passwords found during the process are as follows:

- Level 13: The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL

# Level 13 → Level 14

## Steps Taken

1. Login to the machine.
2. Find and use the provided SSH private key to log in as bandit14.
3. Go to the /etc/bandit_pass/ directory.
4. Read the bandit14 file to get the next password.

## Passwords

- Level 14: The password is 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e

# Level 14 → Level 15

## Steps Taken

1. Connect to localhost on port 30000.
2. Submit the password for the current level (bandit14).
3. Receive the password for the next level.

## Passwords

- Level 15: The password is BfMYroe26WYalil77FoDi9qh59eK5xNr

# Level 15 → Level 16

## Steps Taken

1. Connect to localhost on port 30001 using SSL.
2. Submit the password for the current level (bandit15).
3. Receive the password for the next level.

## Passwords

- Level 16: The password is cluFn7wTiGryunymYOu4RcffSxQluehd

# Level 16 → Level 17

## Steps Taken

1. Use nmap to find which ports in the range 31000-32000 have a server listening on them.
2. Identify the server that speaks SSL and will provide the next credentials.
3. Connect to that server and submit the password for the current level (bandit16).
4. Receive the password for the next level.

## Passwords

- Level 17: The password is xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn

# Level 17 → Level 18

## Steps Taken

1. Check the configuration in /etc/cron.d/ for the cron job.
2. Identify the command executed by the cron job.
3. Run the command manually to retrieve the password.

## Passwords

- Level 18: The password is kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd

# Level 18 → Level 19

## Steps Taken

1. Attempt to log in as bandit18, but you'll be logged out immediately due to the .bashrc configuration.
2. Log in using SSH with the "-T" option to prevent being logged out immediately.
3. List the files in the home directory.
4. Locate the "readme" file and read it to obtain the password.

## Passwords

- Level 19: The password is IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x

# Level 19 → Level 20

## Steps Taken

1. Identify and execute the setuid binary in the home directory.
2. Learn how to use the setuid binary to retrieve the password.
3. Retrieve the password from the usual location (/etc/bandit_pass).

## Passwords

- Level 20: The password is GbKksEFF4yrVs6il55v6gwY5aVje5f0j
## Steps Taken

1. Identify and execute the setuid binary in the home directory.
2. Learn how to use the setuid binary to retrieve the password.
3. Retrieve the password from the usual location (/etc/bandit_pass).

## Passwords

- Level 20: The password is GbKksEFF4yrVs6il55v6gwY5aVje5f0j