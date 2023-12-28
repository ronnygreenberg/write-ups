# Intro
flag should (mostly) be censored with XXX and YYY but are hidden in the .md file itself :)

solved 26-27.December.2023

my review: I really liked bandit because for the most part it was very easy; you can finish it quickly and say "I finished OverTheWire's bandit" but I also learned a thing or two along the way. 10/10 would recommend 

#0
ssh -p 2220 bandit0@bandit.labs.overthewire.org (this is the command we'll run every time only with a different username)
Note - I got several warnings about the server so I removed the it's entry in .ssh/known_hosts and re-added it in the CMD, something must have changed about it

<!-- NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL (in the past, good for googling: boJ9jbbUNNfktd78OOpsqOltutMc3MY1) -->

# 1

the file is called - which messes up using cat so I did find | xargs cat:
find finds all files in this directory
xargs cat feed these file paths to cat so it's basically cat * but cat * doesn’t work
<!-- rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi -->

# 2
cat (press tab) and linux automatically will write: cat spaces\ in\ this\ filename
you can also do cat "spaces in this filename"
<!-- aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG -->

# 3
ls -la to list hidden files
cat inhere/.hidden
<!-- 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe -->

# 4
there are a lot of files and we don’t want to read them one by one so I sue the method from bandit1
find | xargs cat
it prints binary stuff but in the end also the password
<!-- lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR -->

# 5
they give a few clues, not sure about how to filter about the other two but I know how to filter on file size with ls -lR | grep 1033
but then I don’t know which folder… so I ran: ls -lR | grep 1033 -b50
-b50 show 50 lines before that
then I know the folder so cd to it, ls and find .file2
<!-- P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU -->

# 6
ls -lR / | grep 33 | grep bandit6 | grep bandit7
find /  -name "bandit7.password"
<!-- z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S -->

# 7
cat data.txt | grep millionth
<!-- TESKZC0XvTetK0S9xNwm25STk5iWrBvP -->

# 8
cat data.txt | sort | uniq -c | sort
<!-- EN632PlfYiZbn3PhVK3XOGSlNInNE00t -->

# 9
cat data.txt | grep -a == | grep -aP "\w*"
<!-- G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s -->

# 10
cat data.txt | base64 -d
<!-- 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM -->

# 11
This is ROT13 which is extremely popular for some reason
cat data.txt | tr a-zA-Z n-za-mN-ZA-M
https://www.tecmint.com/tr-command-examples-in-linux/
<!-- JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv -->

# 12
strings  command - print all printable characters in a binary file
magic number is a term that represents the file type based on it's first few bytes
cat data.txt
https://gist.github.com/leommoore/f9e57ba2aa4bf197ebc5: gzip format.gz1f 8b
BTW you can just use the file command

the file command will direct you the file type so you can use either of the following depending on the type:
xxd -r
gzip -d
bzip2 -d
tar -xvf

diagnostics:
gzip: 1: unknown suffix -- ignored
mv 1 1.gz
<!-- wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw -->

# 13
using chatGPT I saw you can specify which private key to use using -i so from the Natas13 connection I ran:
SSH -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
<!-- fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq -->

# 14
nc localhost 30000
enter XXX

note: not 100% get it but once you do nc localhost 30000 a connection is open, you just enter data and get a response
<!-- jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt -->

# 15
openssl s_client -connect <machine IP>:PORT
ignore all scary text
enter: XXX
<!-- JQttfApK4SeyHwDlI9SXGR50qclOAil1 -->

# 16
nmap localhost -p 31000-32000
I one by one did what we did in Bandit15 to each of the ~5 open ports, there probably a way to narrow them down but meah

mkdir /tmp/something
nano /tmp/something/key
chmod 600 /tmp/something/key
what we did in natas13 using ssh -i
<!-- hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg -->

# 17
diff passwords.new passwords.old
trying each of the diffs in ssh and finding the correct one:
<!-- awhqfNnAbc1naukrpqDYcF95h7HoMTrC -->

# 18
try to ssh and see bye bye, read in the clue you need to read natas19
google bashrc to read what it is
google ignore bashrc
seeing ssh XXX /bin/dash
do it
cat readme
<!-- VxcazJaVyk16W36BkBUømJTCN8rR95XT VxCazJaVykI6W36BkBU0mJTCM8rR95XT /? -->

# 19
find out how to run binary files by writing the exact path (e.g. ./bandit20-do)
התפסטנות קטנה (נכון בכל האתגרים לא תיארתי)
./bandit20-do cat /etc/bandit_pass/bandit20
<!-- NvEJF7oVjkddltPSrdKEFOllh9V1IBcq -->

# 20
This challenge seems bugged due the weird previous password misspelling, tried:
tmux
ctrl+shift+n or whatever way to create new pane in tmux
upper pane: ./whatever_exe_name 30000
lower pane: nc localhost 30000
in nc send the password like in bandit14
exit till everything is closed (tmux + ssh)
+
https://krusve.com/posts/wargames-bandit2/

didn’t work so took 21's password from google
<!-- WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff -->

# 21
cd /etc/cron.d/
cat cronjob_bandit22
cat /usr/bin/cronjob_bandit22.sh
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
note - mistook file name for password by mistake
<!-- This is commented out. -->
<!-- QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G -->

# 22
so doing same thing in 21 we read the script and understand the script does md5 hash on "echo I am user bandit23" and output it to the corresponding folder in /tmp
so I ran: echo I am user bandit23 | md5sum | cut -d ' ' -f 1 and got 8ca319486bfbbc3663ea0fbe81326349
ran /tmp/8ca319486bfbbc3663ea0fbe81326349
<!-- VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar (old password uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG) -->

# 23
same^
you can put any script in /var/spool/foo and it will run, seemingly every 90s and it'll delete after

in foo: nano a.sh
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/1.txt
(script works with https://www.shellcheck.net/)

save
wait (as long as you can cat the file it didn’t run)
cat /tmp/1.txt
<!-- p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d -->

# 24
nc localhost 30002 to see program behavior:
write https://realpython.com/python-sockets/#echo-client-and-server client that connects to 30002, for example the client should first receive data and only then send data, not vice versa like written in the guide. my Python code without \r\n because reasons:
import socketimport osimport jsonHOST = "127.0.0.1"  # The server's hostname or IP addressPORT = 30002  # The port used by the servertry:    os.mkdir('/tmp/1')except Exception as e:    pass #I  create the folder manually to run the .py file anywaywith socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:    s.connect((HOST, PORT))    data = ''    for i in range(10000):        padded = str(i).zfill(4)        response = f'{s.recv(1024)!r}' #have no idea what !r does        with open('/tmp/1/input_output.txt', 'a') as f:            f.write(json.dumps({'data': data, 'response': response}) + '\n')        data = f"XXX{padded}\n"        s.sendall(data.encode()))

then run:
cat input_output.txt | grep -v Wrong
{"data": "XXX9015\n", "response": "b'Correct!\\nThe password of user bandit25 is XXX\\n\\nExiting.\\n'"}

while it runs (it runs for a long time) I look at the answers, better way to do it:
for i in {0000..9999}; do echo “YYY $i”; done | nc localhost 30002

diagnostics:
I send one request and it hangs there for some reason. Solution: you need to send  \n at the end of the message!
<!-- c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1 -->

# 25
being comfortable in vim-like environments is recommended

OK this is a HUGE difficulty spike curve IMO, I used an answer from the internet after התפסטנות https://mayadevbe.me/posts/overthewire/bandit/level26/

-in our home directory there's a private key we can use to SSH into bandit26 (not from the server BTW, you'll get an error)
-I copied the text to a local file, used this https://superuser.com/questions/1296024/windows-ssh-permissions-for-private-key-are-too-open to fix it's permissions and ran ssh -i
-But we connect, see a print of bandit26 and it immediately closes… which might be related to various things such as .bashrc or whatever but amongst all of them to the default shell of bandit26:
-SSH again with bandit25 and cat /etc/passwd to see which default shell bandit26 uses, we see /usr/bin/showtext
cat /usr/bin/showtext
exec more ~/text.txt
~ is the homedirectory (of bandit26: /home/bandit26)
more is a command to show text similar to cat, funny quirk about more, if the text it shows has more lines than it fits to the window it will enter interactive more and you can enter commands, if it fits it just acts like a regular cat command.
We can't change the size of text.txt but we can change our window size!
So we again ssh -i into bandit26 but before pressing enter, making the CMD windows really small!
press enter, make the window larger
press v to enter vim
:set shell=/bin/bash to change the default shell of the user to regular bash
:shell open the default shell of the user
we're now in /bin/bash from user bandit26 and can run /etc/bandit_pass_bandit26~
<!-- YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS -->

# 26
in the same bash we opened in 25 ./bandit27-do cat /etc/bandit_pass/bandit27
<!-- AVanL161y9rsbcJIsFHuw35rjaOM19nR -->

# 27
learn how to construct git clone command
https://stackoverflow.com/questions/5767850/git-on-custom-ssh-port 
https://stackoverflow.com/questions/10054318/how-do-i-provide-a-username-and-password-when-running-git-clone-gitremote-git - this messed me up, if you try adding the password in the command itself the command wont work but if you don’t it will prompt you for it, enter it and it works

git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
grep -R password

Note:
run it from your PC because you don’t have write permissions on server as bandit27. WRONG
You can run mktemp -d and cd to it
if you do you may change bandit.labs.overthewire.org to localhost
<!-- tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S -->

# 28
same clone thing^
password is nonsense (bunch of xxx)
look in answers, saw git history, remembered about it! (another clue is to run -la in that folder to see the hidden .git folder)
git log - see commits
git log -p *specific commit ID* (I knew how based on my documentation :))
<!-- xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS -->

# 29
same clone thing^
git log --all -p to open the contents of all commits

better solution, https://mayadevbe.me/posts/overthewire/bandit/level30/:
git branch -a
git checkout dev
cat README.md
<!-- OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt -->

# 30
same clone thing^ (mktemp doesn’t work all of a sudden, can't cd to folder, so cd /tmp, mkdir 2, cd 2)
looked for a clue in the answers because had no clue https://mayadevbe.me/posts/overthewire/bandit/level31/
git log --all -p, see tag:  secret (depending on git version I believe)
git tag -n - list all tags and their contents
git show secret (secret - tag name)

Notes:
https://devdojo.com/guide/git/git-diff helped me understand diff --git a/README.md b/README.md can be ignored
cloning the repo on my machine messed up the challenge! (git show secret)
<!-- rmCBvG56y58BXzv98yZGdO7ATVL5dW8y -->


# 31
same clone thing^
cat README.md
nano key.txt
enter text May I come in?
save

git add key.txt
see warning and advice to use -f
git add key.txt -f
git commit -m "message doesn’t matter)
git push
fail but you get the password in the response
<!-- odHo63fHiFqcWWJG9rLiLDtPm45KzUKy -->

# 32
when I ran cat /etc/passwd earlier I saw:
bandit32:x:11032:11032:bandit level 32:/home/bandit32:/home/bandit32/uppershell

Lots of undocumented התפסטנות before looking at the answer
$0

(bookmark is waiting for me I believe to learn more)

Note:
ctrl+D to exit shell
$(s=/bin/bash; $s)

# 33
congratulations readme
new levels might come out in the future