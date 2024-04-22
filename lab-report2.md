# Part 1
## Code for `ChatServer`
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> messageHistory = new ArrayList<>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("Append /add-message?s=<string>&user=<user> to the URL to add your" +
                    "message and user to the" + " simple " + " chat server\n");
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("&");
                String[] query1Strings = parameters[0].split("=");
                String[] query2Strings = parameters[1].split("=");
                if (query1Strings[0].equals("s") && (query2Strings[0].equals("user"))) {
                    createMessage(query2Strings[1], query1Strings[1]);
                }
                return String.format("%s", String.join("\n", messageHistory));
            }
            return "404 Not Found!";
        }
    }

    private String createMessage(String user, String message) {
        String userMessage = String.format("%s: %s", user, message);
        messageHistory.add(userMessage);
        return userMessage;
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if (args.length == 0) {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}

```

## Screenshot 1
![Screenshot of browser showing a message reading `jpolitz: Hello`](https://cdn.discordapp.com/attachments/1065014704986128404/1231819665055940608/image.png?ex=66385876&is=6625e376&hm=f9c77c8301a2c683ea00f17ca3827dd758119bf273986701d8da8a8673458fa9&)

The first method called is the `main()` method, which starts the server and creates a new object of the `Handler` class. There are
no relevant arguments to this method, nor are there any class fields in the `ChatServer` class that contains `main()`. No values
of relevant fields got changed as this method's purpose is to start the server.

The `Handler` uses the method `handleRequest` to read the URL to create a new message in the chat server. This method takes the
`URI` argument `url`, which is read by `handlerequest` to add new messages. `handleRequest` also uses the method `createMessage` to 
format the message that will be added to the `ArrayList` of messages. Using `createMessage` changes the value of the field 
`messageHistory` to add another message.

`createMessage` uses two String arguments: `user` and `message`. These arguments are used to format a new message, which is then
appended to the `ArrayList` class field `messageHistory` in the `Handler` class. In this case, there are currently no messages
in `messageHistory`, so the message from jpolitz saying "Hello" is the first message in `messageHistory`


## Screenshot 2
![Screenshot of browser showing a message reading `jpolitz: Hello \nYash: How Are you`](https://cdn.discordapp.com/attachments/1065014704986128404/1231819768869294081/image.png?ex=6638588f&is=6625e38f&hm=3c8aea0acf165bbe408c0e8763247784365275439d3224d89d0333c23fa5bbab&)

The first method called is the `main()` method, which starts the server and creates a new object of the `Handler` class. There are
no relevant arguments to this method, nor are there any class fields in the `ChatServer` class that contains `main()`. No values
of relevant fields got changed as this method's purpose is to start the server.

The `Handler` uses the method `handleRequest` to read the URL to create a new message in the chat server. This method takes the
`URI` argument `url`, which is read by `handlerequest` to add new messages. `handleRequest` also uses the method `createMessage` to 
format the message that will be added to the `ArrayList` of messages. Using `createMessage` changes the value of the field 
`messageHistory` to add another message.

`createMessage` uses two String arguments: `user` and `message`. These arguments are used to format a new message, which is then
appended to the `ArrayList` class field `messageHistory` in the `Handler` class. In this case, there is already a message in 
`messageHistory`, so the new message from yash saying "How are you" is appended at the end.

# Part 2
## Screenshot of running `ls` with absolute path to private key
![Screenshot of running ls with absolute path to private key](https://cdn.discordapp.com/attachments/1065014704986128404/1231825811279974411/image.png?ex=66273aaf&is=6625e92f&hm=3eab7582577b0698e40fc88f05d0e39fff67d2b50d0c819d878a8292f20f5a63&)

## Screenshot of running `ls` with absolute path to public key on `ieng6` machine
![](https://cdn.discordapp.com/attachments/1065014704986128404/1231831872452034560/image.png?ex=663863d4&is=6625eed4&hm=8859a3c69dd6a3f9d81023185f8e21fc7f099cafcf4377fa722af008d6be78e4&)

## Screenshot of logging into `ieng6` account without being asked for a password
![](https://cdn.discordapp.com/attachments/1065014704986128404/1231826081435357205/image.png?ex=66385e70&is=6625e970&hm=97d9b57ff1a8457ebccb60e72ba4b938298660e8804dd31a0fdb710920d5c7bf&)

# Part 3
Something I learned in this lab that I didn't know before was how to access my public key on the `ieng` machine. It took me a while
to figure out that there was an .ssh directory in the home directory that wasn't visible with just using `ls` on the home directory.
I had to directly use `ls ~/.ssh` to find the .ssh directory.

