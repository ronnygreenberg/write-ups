# intro
my opinion here

# Obedient Cat
download file and open

<!--picoCTF{s4n1ty_v3r1f13d_28e8376d}-->

# Python Wrangling
read the code to see how to use + debugged to understand you need to put the actual password not the filename

pyhon ende.py -d flag.txt.en dbd1bea4dbd1bea4dbd1bea4dbd1bea4

<!--picoCTF{r3j3ct_th3_du4l1ty_cca66bd3}-->

# Wave a flag
strings warm | grep flag

<!--picoCTF{b1scu1ts_4nd_gr4vy_18788aaa}-->

# Nice netcat...
In my nc folder (because cant do environment variable…) nc mercury.picoctf.net 22902

returns a bunch of things

nc mercury.picoctf.net 22902 > test.txt

seems like ASCII, first letter is 112, p in ASCII, flag also starts with p, makes sense

for nubmer in read_file_lines(r'D:\Downloads\test.txt'):    print(chr(int(nubmer)), end='')

read_file_lines is my function

<!--picoCTF{g00d_k1tty!_n1c3_k1tty!_d3dfd6df}-->

# Static ain't always noise
./ltdis.sh static

<!--picoCTF{d15a5m_t34s3r_ccb2b43e}-->

# Tab, Tab, Attack
manually extract and enter each folder and open binary with notepad++… will research tabcomplete later

<!--picoCTF{l3v3l_up!_t4k3_4_r35t!_d32e018c}-->

# PW Crack 1
read code, password is inside it

python3 level1.py level1.flag.txt.enc

<!--picoCTF{545h_r1ng1ng_fa343060}-->

# PW Crack 2
same^

open python

enter chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36), get de76

<!--picoCTF{tr45h_51ng1ng_489dea9a}-->

# strings it
strings strings | grep pico

<!--picoCTF{5tRIng5_1T_d66c7bb7}-->

# Lets Warm Up
open CMD > python

0x70, return 112

chr(112) = p

read hint that say you need to write picoCTF{p}



<!--picoCTF{p}-->

tags: python, hex

# Warmed up
same^



<!--picoCTF{61}-->

tags: python, hex

# Magikarp Ground Mission
copy ssh command

enter password when prompted

ls

loop:

cat flag file

cat instructions

follow instructions, cd to somewhere



<!--picoCTF{xxsh_0ut_0f_\/\/4t3r_21cac893}-->

Tags: linux

# 2 warm
write decimal to binary online (there's a manual calculation you can do but meah)

get 0000000000101010

enter: picoCTF{0000000000101010}

wrong

WTH?

remove padding 0000

works



<!--picoCTF{101010}-->

Tags: hex, binary, decimal

# what's a net cat?
(in a folder where nc.exe is found)

nc jupiter.challenges.picoctf.org 25103



<!--picoCTF{nEtCat_Mast3ry_d0c64587}-->

Tags: nc

# what's a net cat?
exactly the same^



<!--picoCTF{nEtCat_Mast3ry_d0c64587}-->

Tags: nc

# PW crack 3
You need to know Python / programming

change code, instead of user_pw loop through the password list and treat it as user_pw

cmd > python level3.py



<!--picoCTF{m45h_fl1ng1ng_cd6ed2eb}-->

Tags: python

# PW crack 4
same^



<!--picoCTF{fl45h_5pr1ng1ng_d770d48c}-->

Tags: python

# PW crack 5
same^

(this simulates a brute force attack)

run code, doesn’t work, WTH?

lesson, use: .read().split('\n') instead of readlines() which keeps the '\n' to every line 



<!--picoCTF{h45h_sl1ng1ng_40f26f81}-->

Tags: python

# ASCII Numbers
input = '0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x35 0x63 0x31 0x31 0x5f 0x6e 0x30 0x5f 0x71 0x75 0x33 0x35 0x37 0x31 0x30 0x6e 0x35 0x5f 0x31 0x6c 0x6c 0x5f 0x74 0x33 0x31 0x31 0x5f 0x79 0x33 0x5f 0x6e 0x30 0x5f 0x6c 0x31 0x33 0x35 0x5f 0x34 0x34 0x35 0x64 0x34 0x31 0x38 0x30 0x7d'

for part in input.split(' '):

    hex_2_decimal = int(part, 16)
    
    print(chr(hex_2_decimal), end='')



<!--picoCTF{45c11_n0_qu35710n5_1ll_t311_y3_n0_l135_445d4180}-->

Tags: hex, python

# based
run nc command given

first input, opened https://www.rapidtables.com/convert/number/binary-to-ascii.html, I explain some of the manual calculation in "some assembly required 2"

second input, didn’t get it was octal so I was stuck for a second, opened https://gchq.github.io/CyberChef/, put the "magic" recipe which auto-detects encoding and auto-decode, it detected the following:

octal

hex



<!--picoCTF{learning_about_converting_values_02167de8}-->

tags: hex, binary, nc

# special
ssh to server

a lot of התפסטנות, don’t get what's going on, btw I opened my WSL to experiment with a normal Linux shell to compare, להקים סביבת דמה in research is very important!

/bin/bash, /bin/dash/ or any absolute path are forbidden



ok so all of my linux knowledge has been worthwhile!

in linux you can run commands either with $(command) or `command` (thx F5 write-up)

this challenge reminded me of bandit32 so I looked there (I solved it by Googling so it kinda proves that Goolging the answer can teach you something after all!) and saw $0

`$0` opened another shell (a good indicator of it working - it'll be visually different, not always though) but I noticed I don’t see an output for my command unless an error pops up (this was by mistake purely by experimenting)

in linux we have two different output pipes, stdout and stderror, Googling:

`$0 1>&2`

1 - stdout

2 - stderror

if I can see stderr then let's pipe everything from stdout to stderr!



<!--picoCTF{5p311ch3ck_15_7h3_w0r57_f906e25a}-->

tags: linux, command injection

# specialer
ok so from various tests it seems everything we put is entered to  a bash command

man bash on Google to read the manual of a command

ok some התפסטנות, some commands work: cd, echo

tried all shells:

/bin/sh

/bin/cash

/bin/tcsh

/bin/ksh

/bin/ksh93

/bin/bash

/bin/zsh

/usr/bin/fish

source - https://phoenixnap.com/kb/linux-shells, nothing except /bin/bash works which we run already 



Googled "linux ls alternatives":

echo * (echo */* - only dirs with one level of depth in them */*/* and so on, echo * .* - hidden file) - works!

dir

find - doesn’t work

printf

grep - doesn’t work

stat

lsattr

getfacl

I list doesn’t work if I tried before the Google answer == was aware of it

tab completion also works

echo * .* echo */ .* - didn’t find any intesting hidden files



Googled "linux all commands to read file" (after התפסטנות with Google)

tried and doesn’t work: more, less, head, tail, nl, xxd, strings, od

also read - https://book.hacktricks.xyz/linux-hardening/bypass-bash-restrictions#common-limitations-bypasses

Also Google "bypass shell jail" (good Google-able term)

source - works! but semi-useless in this case, good for files with one lines of text



on the סף of reading a solution , say to myself: you're too close!

Google " use echo to read file"

answer: echo "$(<a.txt )"

works!



note - there's an adventure time reference! abra/cadaniel

<!--picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_838b49d1}-->

tags: linux, command injection

# flag_shop
read code, find logical vulnerability:

x - flag_count == x + flag_count if flag_count is negative but the if beforehand protects it



tried:

000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001, hoped %d will have some limitation



the printf before bid is the only print without \n



try to debug code locally, huge התפסטנות

to disable _CRT_SECURE_NO_WARNINGS > RMB on project > settings > https://stackoverflow.com/questions/22450423/how-to-use-crt-secure-no-warnings

the following methods are unsafe: fopen, scanf, setbuf



After all these leades^ flopped I experminted with another vector, buffer overflow, I entered inputs on different lengths (>200)

all returned -1, so I eventually cut it back more and more to see the max length of an input that actuall works, answer: 10

then I entered an input of 11 and it worked!  resulting in an "Integer Overflow", which is basically the logic from the first lead, turning flag_count a very large negative number.



knowing I solved the challenge but my knowledge in this field is not in depth I read the solution after solving (tip, do this), tips from https://dmfrsecurity.com/2021/04/19/picoctf-2019-flag_shop-writeup/:

"Since account_balance is signed, it may be possible to overflow this integer, making it into a negative number"

his first instinct was to enter 2147483647 (max int) which saves a lot of extermination!



ok after Leeat solved it flawlessly with a deep low-level knowledge I read more, https://github.com/VermillionBird/CTF-Writeups/blob/master/2019/picoCTF/General%20Skills/flag_shop/README.md:

We basically want to explain "Integer Overflow" in depth.

The code is written in C++ or C, Leeat says C++ contain C fully so it's basically the same.

int in C are signed int, in binary that means the MSB also represents a nubmer is positive (MSB - 0) or negative (MSB -1), if we use https://www.rapidtables.com/convert/number/binary-to-decimal.html

10000000 is -128 in two complacent but 128 in "regular" binary (don’t have a better term)

10000010, -126 and 130 accordingly^

11111111, -1 and 255 accordingly^

Notice that with every bit we turn on (1 instead of 0) the number gets close to 0.



2147483647 + 1 = -2147483647

we want the negative number to be as large, negatively as possible (e.g. -3 > -2 for our purposes). As we saw in the table above the more we add to the negative number the less negatively large it gets.

but we don’t do +1 we do x900 (*900, multiply 900) so 2147483647/900 = 2386092

2386092 is indeed (both on paper and I verified) the max value we can put without causing an integer overflow

that's why we'll want to put exactly 2386093 (2386092+1)



when I originally solevd this challenge I mistakenly treated int overflow like string overflow, taking only input length into account instead of it's value, for example 000000000000000000000000000000000000001 is still 1. Still it somehow worked for me.

99999999 works (8 9's) but 9999999 (one 9 less) doesn’t

dude in answer says you can overwrite account_balance with a large enough value but entering a huge number (999999999999999999999999999999999999999999999999 or something larger but in that style) doesn’t work,maybe he's mistaken



<!--picoCTF{m0n3y_bag5_68d16363}-->

tags: C programming language, logical vulnerability, PWN, overflow

# Big Zip
download zip

extract, ignore that it seems to abort at 56% (I התפסטנתי on it a bit)

grep -R pico (in my WSL)



<!--picoCTF{gr3p_15_m4g1c_ef8790dc}-->

Tags: linux, zip

# chrono
ssh -p 65137 picoplayer@saturn.picoctf.net - construct SSH command based on parameters given based on previous challenges where they gave you the full command

cd /etc/cron.d - thanks bandit challenges!

ok wrong, התפסטנות

Google "cron folders"

cat /etc/crontab



<!--picoCTF{Sch3DUL7NG_T45K3_L1NUX_7754e199}-->

Tags: linux

# First Find
download zip

(in wsl)

find .

manually search for it

cat full path (cat ./adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt)



<!--picoCTF{f1nd_15_f457_ab443fd1}-->

Tags:

# runme.py
download, either open with notepad (safer) or python runme.py



<!--picoCTF{run_s4n1ty_run}-->

Tags: 

# mus1c
what? skip

ok return after reading the challenge of 1_wanna_b3_a_r0ck5tar

copy lyrics into the website they give in this challenge^

get a bunch of decimals (you need experience to catch that just by sight, alternatively use cyberchef > magic)



input = [114,114,114,111,99,107,110,114,110,48,49,49,51,114]for number in input:    print(chr(number), end='')

1_wanna_b3_a_r0ck5tar

put that in the flag format:

<!-- picoCTF{rrrocknrn0113r} -->



Tags: decimal, python

# plumbing
nc jupiter.challenges.picoctf.org 14291 - lot's of text

nc jupiter.challenges.picoctf.org 14291 > a

then search the file



<!--picoCTF{digital_plumb3r_ea8bfec7}-->

Tags: OS

# 1_wanna_b3_a_r0ck5tar
tried various transpilers, the waybackmachine url is from 2019 so looked for something before that

ok so from reading the docs I saw listen is input() and shout is print()

so before listen I entered to the code:

shout a guitar - returns 136

shout music - returns 1970

to see the expected values

this again output a list of decimals I used just like mus1c



<!--picoCTF{BONJOVI}-->

Tags: 

# fixme1.py
download, run, see error:

IndentationError: unexpected indent

fix



<!--picoCTF{1nd3nt1ty_cr1515_09ee727a}-->

Tags: python

# HashingJobApp
use https://www.md5.cz/



<!--picoCTF{4ppl1c4710n_r3c31v3d_3eb82b73}-->

Tags: hash

# Glitch Cat
nc saturn.picoctf.net 55826

get text

in same cmd: python

enter text

it output it correctly



<!--picoCTF{gl17ch_m3_n07_9c42a45d}-->

Tags: python

# convertme.py
two ways to solve:

you have the code to deencrypt the flag right there, just put print(str_xor(flag_enc, 'enkidu')) near the top of the code, regardless of your input 

be a good boy:

run python file in either pycharm or from cmd (using python command), get a deimal number

open another python console in another cmd, write bin(number_you_got)

enter output of ^ without ''



<!--picoCTF{4ll_y0ur_b4535_722f6b39}-->

Tags: python, decimal, binary, hex

# Bases
looks like base64 (need experience to figure out / use cyberchef > magic)

base64 decode online



<!--picoCTF{l3arn_th3_r0p35}-->

Tags: base64

# First Grep
either grep or open in notepad and ctrl+f pico

Tags:

# fixme2.py
same as fixme1.py



<!--picoCTF{3qu4l1ty_n0t_4551gnm3nt_4863e11b}-->

Tags: python

# Codebook
python code.py



<!--picoCTF{c0d3b00k_455157_d9aa2df2}-->

Tags: python

# Serpentine
in pycharm:

put breakpoint

go to console

print_flag()



<!--picoCTF{7h3_r04d_l355_7r4v3l3d_8e47d128} -->

Tags: python

# money-ware
התפסטנות

read hints - ok you should seach Google



<!--picoCTF{Petya}-->

# repetitions
base64decode again and again until you see the flag



<!--picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_3f81f7be}-->

Tags: base64

# Permissions
have no clue

read hint, still

read solution, https://medium.com/@petemuiruri/permissions-writeup-picoctf-2023-be95c95f80a5, I'llexplain it because it doesn’t explain it well IMO

sudo -lU picoplayer to see which sudo commands we can run

enter password for picoplayer when prompted

we can use vi (aka vim)

sudo vi

:!/bin/bash

we have root!

ls -a to show hidden files

cat .flag.txt



<!--picoCTF{uS1ng_v1m_3dit0r_89e9cf1a}-->

Tags: linux, Privilege escalation

# useless
in mul was able to get -999999 given  large enough numbers to multiply

strings are treated as 0



מתפסטן

read tags in challenge, man, only challenge with this tag

man useless



<!--picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_6140}-->

Tags: linux

