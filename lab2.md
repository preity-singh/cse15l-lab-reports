Code for `ChatServer.java`

`import java.io.IOException;
import java.net.URI;
class Handler implements URLHandler {
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
}`

`class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }
        int port = Integer.parseInt(args[0]);
        Server.start(port, new Handler());
    }
}`