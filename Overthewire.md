# **OverTheWire Bandit Walkthrough (Level 0 to Level 34)**  

This documentation provides step-by-step solutions for all levels (0–34) of the **Bandit** wargame on [OverTheWire](https://overthewire.org/wargames/bandit/). Each level introduces new Linux commands and security concepts, helping users learn cybersecurity and system administration basics.  

---

## **Table of Contents**  
1. [Level 0 → Level 1](#level-0--level-1)  
2. [Level 1 → Level 2](#level-1--level-2)  
3. [Level 2 → Level 3](#level-2--level-3)  
4. [Level 3 → Level 4](#level-3--level-4)  
5. [Level 4 → Level 5](#level-4--level-5)  
6. [Level 5 → Level 6](#level-5--level-6)  
7. [Level 6 → Level 7](#level-6--level-7)  
8. [Level 7 → Level 8](#level-7--level-8)  
9. [Level 8 → Level 9](#level-8--level-9)  
10. [Level 9 → Level 10](#level-9--level-10)  
11. [Level 10 → Level 11](#level-10--level-11)  
12. [Level 11 → Level 12](#level-11--level-12)  
13. [Level 12 → Level 13](#level-12--level-13)  
14. [Level 13 → Level 14](#level-13--level-14)  
15. [Level 14 → Level 15](#level-14--level-15)  
16. [Level 15 → Level 16](#level-15--level-16)  
17. [Level 16 → Level 17](#level-16--level-17)  
18. [Level 17 → Level 18](#level-17--level-18)  
19. [Level 18 → Level 19](#level-18--level-19)  
20. [Level 19 → Level 20](#level-19--level-20)  
21. [Level 20 → Level 21](#level-20--level-21)  
22. [Level 21 → Level 22](#level-21--level-22)  
23. [Level 22 → Level 23](#level-22--level-23)  
24. [Level 23 → Level 24](#level-23--level-24)  
25. [Level 24 → Level 25](#level-24--level-25)  
26. [Level 25 → Level 26](#level-25--level-26)  
27. [Level 26 → Level 27](#level-26--level-27)  
28. [Level 27 → Level 28](#level-27--level-28)  
29. [Level 28 → Level 29](#level-28--level-29)  
30. [Level 29 → Level 30](#level-29--level-30)  
31. [Level 30 → Level 31](#level-30--level-31)  
32. [Level 31 → Level 32](#level-31--level-32)  
33. [Level 32 → Level 33](#level-32--level-33)  
34. [Level 33 → Level 34](#level-33--level-34)  

---

## **Level 0 → Level 1**  
**Goal:** Log in via SSH.  
**Username:** `bandit0`  
**Password:** `bandit0`  

### **Solution:**  
```sh
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
Enter the password when prompted.  

### **Password for Level 1:**  
Check the `readme` file in the home directory:  
```sh
cat readme
```
**Password:** `NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL`  

---

## **Level 1 → Level 2**  
**Goal:** Read a file named `-` (hyphen).  

### **Solution:**  
Use `cat` with `./-` to avoid interpreting `-` as a command flag.  
```sh
cat ./-
```
**Password:** `rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi`  

---

## **Level 2 → Level 3**  
**Goal:** Read a file with spaces in its name.  

### **Solution:**  
Escape spaces with `\` or use quotes.  
```sh
cat "spaces in this filename"
```
**Password:** `aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG`  

---

## **Level 3 → Level 4**  
**Goal:** Find a hidden file in the `inhere` directory.  

### **Solution:**  
List all files (including hidden ones) and read the hidden file.  
```sh
cd inhere
ls -la
cat .hidden
```
**Password:** `2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe`  

---

## **Level 4 → Level 5**  
**Goal:** Find the only human-readable file in `inhere`.  

### **Solution:**  
Use `file` to check file types and `strings` to extract text.  
```sh
cd inhere
file ./-file*
strings ./-file07
```
**Password:** `lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR`  

---

## **Level 5 → Level 6**  
**Goal:** Find a file with specific properties (1033 bytes, non-executable).  

### **Solution:**  
Use `find` with size and permissions filters.  
```sh
find . -size 1033c ! -executable
cat ./maybehere07/.file2
```
**Password:** `P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU`  

---

## **Level 6 → Level 7**  
**Goal:** Find a file owned by `bandit7` with group `bandit6` (33 bytes).  

### **Solution:**  
Search system-wide with `find`.  
```sh
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
```
**Password:** `z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S`  

---

## **Level 7 → Level 8**  
**Goal:** Find the password next to the word `millionth` in `data.txt`.  

### **Solution:**  
Use `grep`.  
```sh
grep "millionth" data.txt
```
**Password:** `TESKZC0XvTetK0S9xNwm25STk5iWrBvP`  

---

## **Level 8 → Level 9**  
**Goal:** Find the only unique line in `data.txt`.  

### **Solution:**  
Sort and count lines, then find the unique one.  
```sh
sort data.txt | uniq -u
```
**Password:** `EN632PlfYiZbn3PhVK3XOGSlNInNE00t`  

---

## **Level 9 → Level 10**  
**Goal:** Find a human-readable string preceded by `=` in `data.txt`.  

### **Solution:**  
Use `strings` and `grep`.  
```sh
strings data.txt | grep "==="
```
**Password:** `G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s`  

---

## **Level 10 → Level 11**  
**Goal:** Decode a base64-encoded file.  

### **Solution:**  
Use `base64 -d`.  
```sh
cat data.txt | base64 -d
```
**Password:** `6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM`  

---

## **Level 11 → Level 12**  
**Goal:** Decode a ROT13-encoded file.  

### **Solution:**  
Use `tr` for ROT13.  
```sh
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
**Password:** `JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv`  

---

## **Level 12 → Level 13**  
**Goal:** Decompress a hexdump file.  

### **Solution:**  
1. Reverse the hexdump to binary.  
2. Decompress multiple times (gzip, tar, bzip2).  
```sh
xxd -r data.txt > data
file data  # Check file type and decompress accordingly
```
**Password:** `wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw`  

---

## **Level 13 → Level 14**  
**Goal:** Use an SSH private key to log into `bandit14`.  

### **Solution:**  
```sh
ssh -i sshkey.private bandit14@localhost
```
**Password:** Not needed; just read `/etc/bandit_pass/bandit14`.  

---

## **Level 14 → Level 15**  
**Goal:** Submit the current password to port 30000 on `localhost`.  

### **Solution:**  
Use `nc` (netcat).  
```sh
cat /etc/bandit_pass/bandit14 | nc localhost 30000
```
**Password:** `fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq`  

---

## **Level 15 → Level 16**  
**Goal:** Submit the password via SSL to port 30001.  

### **Solution:**  
Use `openssl s_client`.  
```sh
openssl s_client -connect localhost:30001
# Then paste the password
```
**Password:** `JQttfApK4SeyHwDlI9SXGR50qclOAil1`  

---

## **Level 16 → Level 17**  
**Goal:** Find a server listening on a port between 31000-32000 with an SSL certificate.  

### **Solution:**  
Scan ports and submit the password.  
```sh
nmap -p 31000-32000 localhost
openssl s_client -connect localhost:31790
# Copy the private key and use it to log into bandit17
```
**Password:** `-----BEGIN RSA PRIVATE KEY-----...`  

---

## **Level 17 → Level 18**  
**Goal:** Compare `passwords.old` and `passwords.new`.  

### **Solution:**  
Use `diff`.  
```sh
diff passwords.old passwords.new
```
**Password:** `hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg`  

---

## **Level 18 → Level 19**  
**Goal:** Log in with a modified `.bashrc`.  

### **Solution:**  
Use `ssh` with a command override.  
```sh
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
```
**Password:** `awhqfNnAbc1naukrpqDYcF95h7HoMTrC`  

---

## **Level 19 → Level 20**  
**Goal:** Exploit a SUID binary.  

### **Solution:**  
Run `./bandit20-do` to read the password.  
```sh
./bandit20-do cat /etc/bandit_pass/bandit20
```
**Password:** `VxCazJaVykI6W36BkBU0mJTCM8rR95XT`  

---

## **Level 20 → Level 21**  
**Goal:** Use a port-forwarding trick.  

### **Solution:**  
1. Set up a listener in one terminal:  
   ```sh
   echo "VxCazJaVykI6W36BkBU0mJTCM8rR95XT" | nc -lvnp 1234
   ```
2. Run the binary in another:  
   ```sh
   ./suconnect 1234
   ```
**Password:** `NvEJF7oVjkddltPSrdKEFOllh9V1IBcq`  

---

## **Level 21 → Level 22**  
**Goal:** Analyze a cron job.  

### **Solution:**  
Check `/etc/cron.d/` and read the script.  
```sh
cat /usr/bin/cronjob_bandit22.sh
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
**Password:** `WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff`  

---

## **Level 22 → Level 23**  
**Goal:** Understand cron job hashing.  

### **Solution:**  
Replicate the script’s logic.  
```sh
echo I am user bandit23 | md5sum | cut -d ' ' -f 1
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
```
**Password:** `QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G`  

---

## **Level 23 → Level 24**  
**Goal:** Exploit a cron job running every minute.  

### **Solution:**  
1. Create a script in `/var/spool/bandit24/`:  
   ```sh
   #!/bin/bash
   cat /etc/bandit_pass/bandit24 > /tmp/bandit24pass
   chmod 666 /tmp/bandit24pass
   ```
2. Wait for the cron job to execute.  
```sh
cat /tmp/bandit24pass
```
**Password:** `VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar`  

---

## **Level 24 → Level 25**  
**Goal:** Bruteforce a 4-digit PIN.  

### **Solution:**  
Write a script to try all combinations.  
```sh
for i in {0000..9999}; do
  echo "VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar $i" | nc localhost 30002
done
```
**Password:** `p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d`  

---

## **Level 25 → Level 26**  
**Goal:** Log in with a restricted shell.  

### **Solution:**  
Resize the terminal to bypass `more`.  
```sh
ssh -i bandit26.sshkey bandit26@localhost
# Then press 'v' to enter vim, and run:
:set shell=/bin/bash
:shell
```
**Password:** `c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1`  

---

## **Level 26 → Level 27**  
**Goal:** Exploit a SUID binary.  

### **Solution:**  
Run `./bandit27-do` to read the password.  
```sh
./bandit27-do cat /etc/bandit_pass/bandit27
```
**Password:** `YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS`  

---

## **Level 27 → Level 28**  
**Goal:** Clone a Git repo and find the password.  

### **Solution:**  
```sh
git clone ssh://bandit27-git@localhost/home/bandit27-git/repo
cat repo/README
```
**Password:** `AVanL161y9rsbcJIsFHuw35rjaOM19nR`  

---

## **Level 28 → Level 29**  
**Goal:** Analyze Git history.  

### **Solution:**  
Check Git logs and previous commits.  
```sh
git log -p
```
**Password:** `tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S`  

---

## **Level 29 → Level 30**  
**Goal:** Find hidden Git branches.  

### **Solution:**  
List all branches and check them.  
```sh
git branch -a
git checkout dev
cat README
```
**Password:** `xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS`  

---

## **Level 30 → Level 31**  
**Goal:** Find Git tags.  

### **Solution:**  
Check Git tags.  
```sh
git tag
git show secret
```
**Password:** `OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt`  

---

## **Level 31 → Level 32**  
**Goal:** Push a file to a Git repo.  

### **Solution:**  
1. Create `key.txt` with specific content.  
2. Push it to the repo.  
```sh
git push origin master
```
**Password:** `rmCBvG56y58BXzv98yZGdO7ATVL5dW8y`  

---

## **Level 32 → Level 33**  
**Goal:** Escape the "UPPERCASE shell".  

### **Solution:**  
Use `$0` to spawn a normal shell.  
```sh
$0
cat /etc/bandit_pass/bandit33
```
**Password:** `odHo63fHiFqcWWJG9rLiLDtPm45KzUKy`  

---

## **Level 33 → Level 34**  
**Goal:** Read the final password.  

### **Solution:**  
```sh
cat /etc/bandit_pass/bandit34
```
**Password:** `pIwrPrtPN36QITSp3EQaw936yaFoFgAB`  

---

## **Conclusion**  
This walkthrough covers all **Bandit** levels (0–34). Each level teaches important Linux and security concepts, making it a great resource for beginners in cybersecurity.  

