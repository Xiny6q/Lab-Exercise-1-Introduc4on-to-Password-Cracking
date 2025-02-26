Download link :https://programming.engineering/product/lab-exercise-1-introduc4on-to-password-cracking/


# Lab-Exercise-1-Introduc4on-to-Password-Cracking
Lab Exercise 1 – Introduc4on to Password Cracking
1. Overview

This lab exercise will provide some hands-on experience with password strength analysis using command-line tools in Linux.

2. Resources required

This exercise requires a Kali Linux VM running in the Virginia Cyber Range.

3. Ini4al Setup

From your Virginia Cyber Range course, select the Cyber Basics environment. Click “start” to start your environment and “join” to get to your Linux desktop login.

4. Tasks

Task 1: Introduc4on to password audi4ng.

On Linux systems, user accounts are stored in the /etc/passwd file (world-readable text file) and passwords are hashed and stored in /etc/shadow (a text file only readable by root). Click on the Terminal Emulator to open a command prompt. You will need to become an administrator on the system to see the shadow file. Type “sudo su -” and hit enter. You will no0ced your command prompt changed from a $ to a # and your user changed from student to root. Go ahead and “cat” those two password files to see what they look like.

Ques>on #1: What hash type is used by your Cyber Range version of Linux? How can you determine that by looking at the hashed passwords in /etc/shadow? (.5 point)



SHA512,



You can see that my password’s hash ID is 6, which is typically encrypted with SHA512.

Ques>on #2: What are two other hash IDs and their types that you may see in /etc/shadow? (.5 point)




Ques>on #3: What is password sal>ng and why is it important? (.5 point)





We’ll use a password audi0ng tool called John the Ripper (JTR), a very eﬀec0ve and widely known password cracker. JTR is available from www.openwall.com/john. JTR is already installed in the virtual environment so you won’t need to download it.

Task 2: Crack Linux passwords.

Create 2 new accounts, one with an easy to guess password (such as 1234) and one with a diﬃcult to guess password.

Ques0on #4: Cut and paste or screen capture the commands you used to create the accounts and set



the passwords. (.5 point)




2. Now let’s see which ones we can crack. Run john against the /etc/shadow file.

JTR will aoempt to crack the passwords and display any that it ‘cracks’ as it goes along. It starts in “single crack” mode, mangling username and other account informa0on. It then moves on to a dic0onary aoack using a default dic0onary, then with a hybrid aoack, then brute force where it will try every possibly combina0on of characters (leoers, numbers, and special characters) un0l it cracks them all. You may see several warnings about candidates buﬀered for the current salt and that is ok. You can ignore those warnings.

The account with the easy to guess password should be cracked rather quickly. Wait for a liole bit for it to crack the diﬃcult password, but don’t wait too long as it could take months or years to complete if your password is really strong! Press [CTRL]-[C] to stop execu0on if it doesn’t automa0cally complete and return to the command prompt.

Ques>on #5: Provide a screenshot of your JTR cracked passwords (.5 point)



Ques>on #6: Briefly describe how a dic>onary based password aXack works. (.75 point) A dic0onary aoack is aoempt to guess passwords by using well-known words or phrases.



Ques>on #7: Briefly describe how a brute force password aXack works. (.75 point)



A brute force aoack relies on guessing all possible combina0ons of a targeted password un0l the correct password is discovered.

John uses the following files to manage execu0on. Most are all stored in the /usr/share/john folder on your Kali virtual machine (john.pot is stored elsewhere as indicated):

password.lst is john’s default dic0onary. You can cat this file to look at it. You can specify another wordlist on the command line using the –wordlist= direc0ve (for example # john –wordlist=/usr/share/dict/american-english /etc/shadow

john.conf is read when JTR starts up and has rules for dic0onary mangling for the hybrid crack aoempt




– john.rec is used to record the status of the current password cracking aoempt. If john crashes, it will start where it let oﬀ instead of star0ng again from the beginning of the dic0onary.

/root/.john/john.pot lists passwords that have already been cracked. If you run john again on the same shadow file, it won’t show these cracked passwords unless you delete this file first using

rm /root/.john/john.pot.

Task 3. More password audit.

John the Ripper’s default dic0onary is a short list of common passwords. Some0mes a standard English dic0onary is a beoer op0on. In this exercise we will 1) download a Linux shadow file that contains a set of user accounts and hashed passwords, 2) download a diﬀerent dic0onary, and then 3) aoempt to determine the passwords using the default dic0onary and the new dic0onary.

Download the following file using the wget command:

artifacts.virginiacyberrange.net/gencyber/shadow

Run John against the newly downloaded shadow file. Let John run for a few minutes, then stop with [CTRL]-[C].

Ques>on #8: Which passwords are revealed? (cut and paste or screen capture) (.5 point)



Africa (user3)

Adams (user2)

Install a new dic0onary using the following command:

apt-get install wamerican

Clear the John cache from the previous run by dele0ng the /root/.john/john.pot file.

Next run John against the downloaded shadow file again but this 0me using the newly downloaded dic0onary by invoking the –wordlist direc0ve at the command line with the loca0on of the new dic0onary (–wordlist=/usr/share/dict/american-english)

Ques>on #9: Which passwords were revealed this >me? (cut and paste or screen capture) (.5 point)



Africa (user3)

Aachen (user1)

Adams (user2)

Alan (user4)

Ques>on #10: What is the diﬀerence between the two dic>onaries that made one aXempt more eﬀec>ve than the other? (1 point)



Words contained in the two dic0onaries are diﬀerent. Words contained in American-english dic0onary are closer to the passwords for users in shadow, so it is more eﬀec0ve than the default dic0onary.




Ques>on #11: What are two methods that will help provide more secure authen>ca>on and protect against password cracking? (1 point)



Use longer passwords

Use diﬀerent passwords for diﬀerent accounts

To close the exercise, just click the X on the terminal window to close it and click on the Log Out icon in the upper right hand corner of the screen to log out.

By submitting this assignment you are digitally signing the honor code, “I pledge that I have neither given nor received help on this assignment”.

END OF EXERCISE





