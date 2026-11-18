# CROSS-SITE REQUEST FORGERY LAB 1

Cross site request forgery exploit users by making request the user dont intend to do. It can be by giving url to the user, where user will click it and in background some request happens with the user cookie. Burp has a very nice functionality of generating csrf html which we can use and supply to victim.

![alt text](<csrf 1.1.png>)![alt text](<csrf 1.2.png>)![alt text](<csrf 1.3.png>)![alt text](<csrf 1.4.png>)![alt text](<csrf 1.5.png>)![alt text](<csrf 1.6.png>)![alt text](<csrf 1.7.png>)

# CROSS-SITE REQUEST FORGERY LAB 2

Website can use csrf token as a defence mechanism for csrf. Without producing the csrf token exactly, it is not possible to exploit using csrf. This can be bypassed many ways. Sometimes csrf is only implemented for POST request, but is not checked when it is GET request. In that case we can modify the actual request to GET request and produce html to exploit as csrf.

![alt text](<csrf 2.1.png>)![alt text](<csrf 2.2.png>)![alt text](<csrf 2.3.png>)

# CROSS-SITE REQUEST FORGERY LAB 3

Some website may only check if csrf token exists, else the check will never happen. So we can just remove the csrf token fully and construct csrf exploit for the new request.

![alt text](<csrf 3.1.png>)![alt text](<csrf 3.2.png>)![alt text](<csrf 3.3.png>)

# CROSS-SITE REQUEST FORGERY LAB 4

Some times csrf token are checked properly, but is not checked using the user session cookie. So basically we can open our own account, get our session cookie, then use the session cookie to construct csrf exploit for the victim account.

![alt text](<csrf 4.1.png>)![alt text](<csrf 4.2.png>)![alt text](<csrf 4.3.png>)![alt text](<csrf 4.4.png>)

# CROSS-SITE REQUEST FORGERY LAB 5
