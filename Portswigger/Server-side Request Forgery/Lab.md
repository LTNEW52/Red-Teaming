# SERVER-SIDE REQUEST FORGERY LAB 1

Server side request forgery exploit the trust between server and backends. It can blindly trust the connection server makes. One such thing is admin panel. Usually user dont have admin panel access, and even if they can visit the page, there is nothing to do there. But as website trust server connections, we can exploit it and make delete request using the server.

![alt text](<ssrf 1.1.png>)![alt text](<ssrf 1.2.png>)![alt text](<ssrf 1.3.png>)![alt text](<ssrf 1.4.png>)![alt text](<ssrf 1.5.png>)

# SERVER-SIDE REQUEST FORGERY LAB 2

Many times functionalities can be in different backend servers. They can have different private IP address, so they are not accessable by normal user. We can use the server to communicate with these backend servers. If we can identify that other services use private address, we can user intruder to find the ip address by bruteforcing.

![alt text](<ssrf 2.1.png>)![alt text](<ssrf 2.2.png>)![alt text](<ssrf 2.3.png>)![alt text](<ssrf 2.4.png>)z

# SERVER-SIDE REQUEST FORGERY LAB 3

Wesbite can use blacklist as a defence, such as 127.0.0.1, localhost, admin etc. We can use various method to alter them such that it doesnt hit the blacklist, but also do the exploit. We can convert 127.0.0.1 to octal, binary, hexadecimal, and even 127.1. As for blacklisted word like admin, we can use uppercase lowercase like aDmIn or base64 encode.

http://127.1/aDmIn

![alt text](<ssrf 3.1.png>)![alt text](<ssrf 3.2.png>)![alt text](<ssrf 3.3.png>)

# SERVER-SIDE REQUEST FORGERY LAB 4

Websites can use whitelist too, which will allow only specific path or url. This is slightly harder, because without the allowed url, we cant use the server for ssrf exploit. What we can do is first find what open redirection the website allows. If we can find it, where url can be pasted, we can use it so that server will call our actual wanted url.

![alt text](<ssrf 4.1.png>)![alt text](<ssrf 4.2.png>)![alt text](<ssrf 4.3.png>)

# SERVER-SIDE REQUEST FORGERY LAB 5

There is another type of SSRF, which is called blind ssrf. In this type of ssrf, we cant see the reply in the frontend, so we cant see what is happening and further exploit it. But there are ways to confirm that server is doing outgoing connection. Burp collaborator gives us custom domain, which we can use in this lab to check how this server make connection. We can change the referer header to our collaborator domain, and can watch the connection made back from the lab server.

![alt text](<ssrf 5.1.png>)![alt text](<ssrf 5.2.png>)![alt text](<ssrf 5.3.png>)

# THIS IS THE END OF SERVER-SIDE REQUEST FORGERY!

![alt text](<SSRF END.png>)
