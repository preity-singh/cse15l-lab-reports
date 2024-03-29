# Code for `ChatServer.java`

    import java.io.IOException;
    import java.net.URI;

    class Handler implements URLHandler {
        // The one bit of state on the server: a number that will be manipulated by
        // various requests.
        String str = "";

        public String handleRequest(URI url) {
            if (url.getPath().equals("/")) {
                return str;
            } else {
                if (url.getPath().equals("/add-message")) { 
                    String queryString = url.getQuery();
                    String[] parameters = queryString.split("&"); //split string
                    String[] messageParam = parameters[0].split("=");
                    String[] userParam = parameters[1].split("=");
                    
                    if(messageParam[0].equals("s") && userParam[0].equals("user")){
                        str += userParam[1] + ": " + messageParam[1];
                        return str; 
                    }
                }
                return "Invalid argument"; 
            }
        }
    }

    class ChatServer {
        public static void main(String[] args) throws IOException {
            if(args.length == 0){
                System.out.println("Missing port number! Try any number between 1024 to 49151");
                return;
            }
    
            int port = Integer.parseInt(args[0]);
    
            Server.start(port, new Handler());
        }
    }

------------

# Part 1
![Image](RedoPic.png)
* Which methods in your code are called?
    - `String handleRequest(URI url)` method in the `Handler` class gets called.

* What are the relevant arguments to those methods, and the values of any relevant fields of the class?
    - The relevant argument would be `url` because it represents the URI of the request.
    - The relevant fields of this class would be `str` which is the string of the chat message displayed the server.

* How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
    - `url.getPath()` --> evaluates `/add-message`
    - `url.getQuery()` --> gets the query part of the url `s=Hello&user=jpolitz`
    - line starting with `String[] parameters` --> splits the query like this `["s=Hello", "user=jpolitz"]`
    - `String[] messageParam` & `String[] userParam` --> splits each parameter even further
    - inside the if statement that checks if the keys are correct, the new chat message gets appended to `str`
        - value of `str`:
    ```
      jpolitz: Hello
    ```

-----------
![Image](secondImage-lab2.png)
* Which methods in your code are called?
    - `String handleRequest(URI url)` method in the `Handler` class gets called.
    
* What are the relevant arguments to those methods, and the values of any relevant fields of the class?
    - The relevant argument would be `url` because it represents the URI of the request.
    - The relevant fields of this class would be `str` which is the string of the chat message displayed the server.
    
* How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
    - `url.getPath()` --> evaluates `/add-message`
    - `url.getQuery()` --> gets the query part of the url `s=How are you&user=yash`
    - line starting with `String[] parameters` --> splits the query like this `["s=How are you", "user=yash"]`
    - `String[] messageParam` & `String[] userParam` --> splits each parameter even further
    - the if statement that checks if the keys are correct, and since `str` is not empty, we add `\n` which creates a new line
    - after the new chat message gets appended, the value of `str`:
  ```
  jpolitz: Hello
  yash: How are you
  ```

# Part 2
![Image](absolutepath-lab2.png)
![Image](ls-lab2.png)
* /home/linux/ieng6/oce/8o/prs009/.ssh/id_rsa. **--> private**
* /home/linux/ieng6/oce/8o/prs009/.ssh/id_rsa.pub. **--> public**

----------
![Image](loginWithoutPassword.png)
* Screenshot of my terminal where I logged into my ieng6 account without being asked for a password.

# Part 3
*In a couple of sentences, describe something you learned from lab in week 2 or 3 that you didn't know before.*

* I honestly didn't know what servers were and how they worked. I liked the reference of how my individual computer is the client, while the computer in the basement that I am connected to is the server. A server is the central hub that helps connect devices and get what they want.
* Before this lab I was unaware of the concept of SSH keys: the pair of keys intended to hold a secure and private connection between the client and the server. A key pair has a private key that is stored away from the public on the client, while the public key is shared with the server.
