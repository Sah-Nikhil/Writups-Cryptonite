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
    > gpt advises to add a descriptor for standard error and and **/dev/null** to remove any files which  contain a standard error
    
#### More thoughts
>still unable to undestand how **/dev/null** works.


# Level 8

## Steps taken

- Since we are searching for a string here, we need to use the grep command.
  - `grep "millionth" data.txt`

  This gives an output that shows the line containing the word 'millionth' in the text file data.txt and provides the password for the next level.

# Level 9

## Steps taken

- The grep command does not give us any option of counting the occurrence of a particular line of text. Thus, looking at the given set of possible useful commands, uniq catches the eye. However, according to uniq's description, we can only filter adjacent matching lines using this command. Hence we need to sort the data first. This gives us the first possibility of our command: 
- `cat data.txt | sort | uniq`

  But this doesn't work because if we give no options with the uniq command, matching lines are merged to the first occurrence. Hence we use it along with the -u option which prints unique lines.
- `cat data.txt | sort | uniq -u`

  And we get our password!

# Level 10

## Steps taken

- We first need to find human-readable strings in the file. For this, we use the strings command, which can extract human-readable text. The string also needs to have '=' in it, so to search for '=' in a string, we use the grep command. Thus our final command will look like:
- `strings data.txt | grep "="`

  When we do this, we get a list of strings with '=' sign in them, and we can easily find the one that starts with multiple '=' signs, and that is our password.

# Level 11

## Steps taken

- The clue clearly mentions base64 encoded data, hence the first thing that strikes is the base64 decode command.
- We then use `cat data.txt | base64 -d` command to get the desired output.

# Level 12

## Steps taken

- This is a case of position rotation, more specifically the Rot 13 cipher, which is a special case of Caesar cipher. Hence we need to use the 'tr' command.
- The tr command is a UNIX command-line utility for translating or deleting characters.
- Hence we first cat out the file and then pipe it to the tr command, which does the cipher decoding.
- `cat data.txt | tr a-zA-Z n-za-mN-ZA-M`
Gives us the required output. Here a-z represents lowercase input, A-Z represents uppercase input, and n-za-m is the corresponding lowercase output [a+13 characters is n, and this is a symbolic way of writing all letters without actually having to list them individually. n-za-m means letters from n to z and then a to m].









