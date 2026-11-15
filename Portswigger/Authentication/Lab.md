# AUTHENTICATION VULNERABILITIES LAB 1

When guessing username and password, many website may accidently expose what is the correct username. When trying multiple username, for all of them it can say, username invalid, and for one it can sayy, invalid password. We can use that to guess the username. And then the rest is easy, finding the password by bruteforcing. Burpsuite intruder is very effective for this.

![alt text](<auth 1.1.png>)![alt text](<auth 1.2.png>)![alt text](<auth 1.3.png>)![alt text](<auth 1.4.png>)![alt text](<auth 1.5.png>)

# AUTHENTICATION VULNERABILITIES LAB 2

So this was hard. Unlike the previous one, it says both username and password is invalid. The only change is, the correct username dont have a (.) after the sentence. To find the changes, We can use grep extract from the settings of intruder to highlight the output, and find the difference. The rest is like before.

![alt text](<auth 2.1.png>)![alt text](<auth 2.2.png>)![alt text](<auth 2.3.png>)![alt text](<auth 2.4.png>)![alt text](<auth 2.5.png>)![alt text](<auth 2.6.png>)

# AUTHENTICATION VULNERABILITIES LAB 3

This was interesting. Some website can implement defence such that, only the accurate username will be checked for password, others are not. So naturally accurate username have some delay in them, as they have to check the password. We can make it more obvious by using a very long password. In this lab, there was a extra defence with IP block for bruteforcing. In this case, we can use the X-Forwarded-For. X-Forwarded-For keeps track of the actual ip the request came from in reverse proxy. We can edit this, and use different number, so it will treat them as different ip, bypassing the ip block.

![alt text](<auth 3.1.png>)![alt text](<auth 3.2.png>)![alt text](<auth 3.3.png>)![alt text](<auth 3.4.png>)![alt text](<auth 3.5.png>)![alt text](<auth 3.6.png>)

# AUTHENTICATION VULNERABILITIES LAB 4

Websites also can produce protection by locking ip when there are multiple incorrect login. But there can be a flaw, where the lock can be avoided by login in to own account. Lets say websites lock ip after 4 incorrect login. We can try 3 incorrect login, and correctly login in our own account in 4th try. This is a way to bypass failure based ip login. But in this case, we have to try one password at a time, so concurrent try should be 1.

![alt text](<auth 4.1.png>)![alt text](<auth 4.2.png>)![alt text](<auth 4.3.png>)![alt text](<auth 4.4.png>)![alt text](<auth 4.5.png>)

# AUTHENTICATION VULNERABILITIES LAB 5

A very effective defence is locking the ID itself. For finding the correct user, we can use bruteforcing username with specifc password tries, to trigger account locking. In this case, out of all users, one username triggered account locking after 3 incorrect passord tries. That is the username we are looking for. After getting the username, we can bruteforce password. Although it will trigger account lock, for the correct password it doesnt show any warning. That is our clue!

![alt text](<auth 5.1.png>)![alt text](<auth 5.2.png>)![alt text](<auth 5.3.png>)![alt text](<auth 5.4.png>)![alt text](<auth 5.5.png>)![alt text](<auth 5.6.png>)

# AUTHENTICATION VULNERABILITIES LAB 6

A good option is to use 2 factor authentication. But it is as strong as its implementation. Some website can introduce 2fa, but not implement well. Usually 2fa code is required after the log in, but the website may not check it at all. So while there is a page for 2fa code submission, we are already logged in, and we can just ignore the page completly.

![alt text](<auth 6.1.png>)![alt text](<auth 6.2.png>)

# AUTHENTICATION VULNERABILITIES LAB 7

Even if 2fa is implemented properly, after login, website may not check properly who is trying to do 2fa. They can implement verification by username as cookie, which ofcourse is editable. We can login in our account to understand how the 2fa works. In this lab, the username is used to generate 2fa. So we can just change the username to victim username to generate the 2fa for it. Then, we can change the verify to victim username and use intruder to bruteforce 2fa code to find which one is the correct code. After that we can use it to log in to the account.

![alt text](<auth 7.1.png>)![alt text](<auth 7.2.png>)![alt text](<auth 7.3.png>)![alt text](<auth 7.4.png>)![alt text](<auth 7.5.png>)![alt text](<auth 7.6.png>)

# AUTHENTICATION VULNERABILITIES LAB 8

Website can have options for keep logged in. This can be done by using a persistent cookie, which keeps track of the user. It can be as basic static option like username:password, which is exploitable. In this lab, when we logged in, we got the cookie, which after further investigated, appeared as Base 64(username:md5 of password). So we can do bruteforce customly using the payload processin to convert it like the existing cookie. Successful bruteforce will have slightly changed response, using that we can retrieve the actual password and log in ourselves.

![alt text](<auth 8.1.png>)![alt text](<auth 8.2.png>)![alt text](<auth 8.3.png>)![alt text](<auth 8.4.png>)![alt text](<auth 8.5.png>)![alt text](<auth 8.6.png>)![alt text](<auth 8.7.png>)

# AUTHENTICATION VULNERABILITIES LAB 9

This was fun. We can use xss (cross site scripting) to find valuable things. So xss use <\script> tag to exploit things. We were given a exploit server, which provides a redirectable site with exploit file. We just have to make a xss script, which will forward cookies to the exploit server. After we get the cookie of the victim, the rest are easy. The cookie follow Base 64(username:md5 of password) again, so we can search for similar md5 hash password. If we get it, we can access the account easily.

<\script>document.location=""+document.cookie</\script>

![alt text](<auth 9.1.png>)![alt text](<auth 9.2.png>)![alt text](<auth 9.3.png>)![alt text](<auth 9.4.png>)![alt text](<auth 9.5.png>)![alt text](<auth 9.6.png>)![alt text](<auth 9.7.png>)

# AUTHENTICATION VULNERABILITIES LAB 10

Reset password can be a way to compromise victim account. Websites can be clever to use random token for reset link, but may not check the token again when actually reseting password, and can have exposed user field when actually reseting password which we can change to victim username.

![alt text](<auth 10.1.png>)![alt text](<auth 10.2.png>)![alt text](<auth 10.3.png>)![alt text](<auth 10.4.png>)

# AUTHENTICATION VULNERABILITIES LAB 11

Website can produce dynamic token for reset link with not user field. In that case we can make use of man in the middle attack. From our account, we can request forget password for victim account. There is a option called X-Forwarded-For, which keeps track of actual header in reverse proxy. We can exploit it and give our exploit site link. Victim may click every link they see in email. If they do, our log will capture the reset link. From there the rest is easy, we just reset victims password and use it to access his account.

![alt text](<auth 11.1.png>)![alt text](<auth 11.2.png>)![alt text](<auth 11.3.png>)

# AUTHENTICATION VULNERABILITIES LAB 12

Traditional password reset have current password, new password and confirmed new password. We can use this in our advantage, by burteforcing this to find out correct password. So, when there is a wrong current password and different new passwords, it shows current password do not match. But when there is correct password but different new passwords, it shows new password do not match. That is a big hint of we found actual password.

![alt text](<auth 12.1.png>)![alt text](<auth 12.2.png>)![alt text](<auth 12.3.png>)![alt text](<auth 12.4.png>)

# THIS IS THE END OF AUTHENTICATION LAB. THIS WAS MUCH HARDER THAN PATH TRAVERSAL, BUT ALSO MUCH ENTERTAINING. I GOT TO LEARN LOTS OF WAYS TO EXPLOIT AUTHENTICATION TO COMPROMIZE A WEBSITE, AND HOW WEAK CODE CAN BRING IN VULNERABILITY EVEN IN THE ROBUST METHODS. ONE TAKEWAY, YOU HAVE TO BE VERY PATIENT AND TRY EVERYTHING THAT IS POSSIBLE. SADLY I AM NOT THAT GOOD CURRENTLY :(

![alt text](<Authentication End.png>)
