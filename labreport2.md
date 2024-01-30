ChatServer code:

\ import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String groupChat = "";
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return groupChat;
        } else {
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                String[] getUser = parameters[1].split("&");
                    groupChat += (parameters[2] + ": " + getUser[0] + "\n");
                    return String.format(groupChat);          
            }
            else{
            return "404 Not Found!";
            }
        }
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("You don't have a port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);
        Server.start(port, new Handler());
    }
}
\
