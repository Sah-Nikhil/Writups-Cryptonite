# Writups-Cryptonite

<p>Writeup compilation for Bandit attempt</p>

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
4. FOund the password for the next level in the *./. hidden* file
5. Extracted the <a href='2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe'>password</a> using the **cat** *./.hidden* command

## Issues Faced

> none

> ### Mitigation steps