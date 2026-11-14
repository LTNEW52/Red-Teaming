# PATH TRAVERSAL LAB 1

If the websites dont have security implementation for path traversal, we can access to files in other places of the server. Lets say the images for the webpages are in /var/www/image, we can use ../../.. to go to the root, then /etc/passwd to find the user files easily.

../../../etc/passwd

![alt text](<path 1.1.png>)

# PATH TRAVERSAL LAB 2

Sometimes websites can deny ../ as a way for path traversal protection. In that situation, we can use absolute path like /etc/passwd.

/etc/passwd

![alt text](<path 2.1.png>)

# PATH TRAVERSAL LAB 3

Websites can implement defense against ../, which strips any ../ it finds. We can overcome this by writing ../ as ....//, so even if it strips, ../ remains.

....//....//....//etc/passwd

![alt text](<path 3.1.png>)

# PATH TRAVERSAL LAB 4

Websites can further improve defense by rejecting even the previous type of path traversal, stripping every ../ entirely. In that case we can go to encode. We can encode one, two or even multiple time to bypass the protection. Burp suite have encoding options in it.

![alt text](<path 4.1.png>)

# PATH TRAVERSAL LAB 5

Websites can be clever and require the exact directory when requesting the file or image. In that case, we can start with the required directory and then appened our exploit.

/var/www/image/../../../etc/passwd

![alt text](<path 5.1.png>)

# PATH TRAVERSAL LAB 6

Sometimes website may require the filepath to end with a specific file extension. clearly /etc/passwd dont have extension. In that case we can use null byte, \0 or %00. This will pass the check and also igonre when running as a command.

../../../etc/passwd%00.jpg

![alt text](<path 6.1.png>)

# THIS IS THE END OF PATH TRAVERSAL. I LEARNED A LOT OF NEW WAYS TO EXPLOIT PATH TRAVERSAL, WHICH WAS NOT SHOWN IN THE BASIC LAB OF SERVER SIDE VULNERABILITY. THE INVESTIGATION WAS FUN!

![alt text](<Path Traversal End.png>)
