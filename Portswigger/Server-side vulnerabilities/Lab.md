# PATH TRAVERSAL LAB 1

When websites do not implement protection against path traversal or Directory traversal, we can modify the request to get things that should not a user get. Example is a image in the website, which requests it from lets say /var/www/images. By using ../../../ we can go to root, and then request /etc/passwd, which normally should not be accessed by a user.

../../../etc/passwd

![alt text](<Path Lab 1.1.png>)![alt text](<Path Lab 1.2.png>)

# ACCESS CONTROL LAB 1

Admin pages naturally cant be seen by users normally. But many hidden paths are written in robots.txt. We can use robots.txt to learn more about the website.

/robots.txt

![alt text](<Access 1.1.png>)![alt text](<Access 1.2.png>)![alt text](<Access 1.3.png>)

# ACCESS CONTROL LAB 2

Sometimes developers can hide admin panel with not predictable names or ways. But when it is not predictable, it must have some type of footprint in the code. We can examine the code carefully to find the admin panel!

![alt text](<Access 2.1.png>)![alt text](<Access 2.2.png>)![alt text](<Access 2.3.png>)

# ACCESS CONTROL LAB 3

Many times admin can be recognized with something such as cookies or simple true/false field, such as admin=true. If we can find it, we can change the value to send request as admin from user side, and perform admin level task.

![alt text](<Access 3.1.png>)![alt text](<Access 3.2.png>)![alt text](<Access 3.3.png>)![alt text](<Access 3.4.png>)

# ACCESS CONTROL LAB 4

We can access other users accounts too. Sometimes users are denoted by 1,2,3 etc, so just changing things like id=2,3 can give us access to other users. But what if the user id is non predictable and random? Well, even then user id may leave its trace in somewhere, like blogs, post etc. If we can discover the ID, we can do the next part easily.

![alt text](<Access 4.1.png>)![alt text](<Access 4.2.png>)![alt text](<Access 4.3.png>)

# ACCESS CONTROL LAB 5

We can use what we learned from user access and admin access together. We can access to admin page by chaning id=administrator, then use the inspect to find the password, because there is a password change option in that page. The rest is simple, just login using admin id and pass and we get the admin panel control!

![alt text](<Access 5.1.png>)![alt text](<Access 5.2.png>)![alt text](<Access 5.3.png>)![alt text](<Access 5.4.png>)

# AUTHENTICATION LAB 1

When website use password for authentication, it opens the path for bruteforcing. We can use Burpsuites intruder for bruteforcing. We can observe the webs response to find out which username and password is correct for the site, and which are not.

![alt text](<Auth 1.1.png>)![alt text](<Auth 1.2.png>)![alt text](<Auth 1.3.png>)![alt text](<Auth 1.4.png>)![alt text](<Auth 1.5.png>)

# AUTHENTICATION LAB 2

If 2FA is not implemented properly, sometimes it may not wait for the code verification at all. After we login, it then asks for the code. In the meantime, we are basically logged in. So we basically just ignore the code page and go to our account page or any page basically.

![alt text](<Auth 2.1.png>)![alt text](<Auth 2.2.png>)![alt text](<Auth 2.3.png>)

# SERVER-SIDE REQUEST FORGERY LAB 1

SSRF is a attack which uses the web server to attack internally or externally. Many times, request from the server itself dont go through the usual checks, which means, server request are trusted enough to them. We can use this to our advantage, such as using server for admin panel tasks.

![alt text](<SSRF 1.1.png>)![alt text](<SSRF 1.2.png>)![alt text](<SSRF 1.3.png>)![alt text](<SSRF 1.4.png>)![alt text](<SSRF 1.5.png>)

# SERVER-SIDE REQUEST FORGERY LAB 2

Even when some functionality are in different backend component, we can contact with them with ip addresses. We can find out which ip address it is by bruteforcing using intruder. After that, the rest is like before.

![alt text](<SSRF 2.1.png>)![alt text](<SSRF 2.2.png>)![alt text](<SSRF 2.3.png>)![alt text](<SSRF 2.4.png>)![alt text](<SSRF 2.5.png>)![alt text](<SSRF 2.6.png>)

# FILE UPLOAD VULNERABILITIES LAB 1

If websites dont implement file upload check, meaning they do not check what file we are uploading, we can upoload web shell, like a php file with command. After uploading, we can request the file again to run the command!

![alt text](<File 1.1.png>)![alt text](<File 1.2.png>)![alt text](<File 1.3.png>)![alt text](<File 1.4.png>)

# FILE UPLOAD VULNERABILITIES LAB 2

But there is usually some type of checking of the uploaded file to stop exploits. That can be thing such as checking specific type of file that website wants, like for image, Content-Type=image/png. When we upload php file, it changes the content type automatically. But if user can change this, we can easily change it to image/png, and it will be acceptable for the website.

![alt text](<File 2.1.png>)![alt text](<File 2.2.png>)![alt text](<File 2.3.png>)![alt text](<File 2.4.png>)![alt text](<File 2.5.png>)![alt text](<File 2.6.png>)

# OS COMMAND INJECTION LAB 1

Some websites can query using os commands. We can exploit it easily, by appending other commands with the existing command, using |

![alt text](<OS 1.1.png>)![alt text](<OS 1.2.png>)

# SQL INJECTION LAB 1

SQL Injection is a way to exploit database and find out information that is otherwise not visible. One such thing can be is finding out not released product yet. When we click category, it makes query about that specific category, and only released product. We can remove the constraint by modifying the request with '-- , where, -- means comment out the rest. We can also use OR 1=1, where 1=1 is always true, so it shows every released and unreleased product, not containing only specific category.

category=Gifts'+OR+1=1--

![alt text](<SQLI 1.1.png>)![alt text](<SQLI 1.2.png>)

# SQL INJECTION LAB 2

If there is not SQL injection check, we can exploit it even in logins. Lets say admin login with username and password, and it is checked using sql query. Like the previous lab, we can comment out the password entirely.

username=administrator'--&password=test

![alt text](<SQLI 2.1.png>)![alt text](<SQLI 2.2.png>)

# THAT IS THE END. THIS WAS A VERY BASIC LAB COVERING LOTS OF BASIC WEB EXPLOITATION, SO I LEARNED A LOT OF HOW WEB AND WEB EXPLOITATION WORKS. SOMETIMES I STUMBLED, BUT IT WAS A VERY REWARDING EXPERIENCE!

![alt text](<Server Side Complete.png>)
