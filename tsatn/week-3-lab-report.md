# CSE 15L Lab 2 (Week 3)

Teresa Tian

A16878664

# Part One
## Code for SearchEngine.java

    import java.io.IOException;
    import java.net.URI;
    import java.util.*;

    class Handler implements URLHandler {
        List<String> strList = new ArrayList<String>();
        public String handleRequest(URI url) {
            if (url.getPath().contains("/")) {
                if (url.getPath().contains("add")) {
                    String[] parameters = url.getQuery().split("=");
                    if (parameters[0].contains("s")) {
                        if (parameters[1].contains("anewstringtoadd")) {
                            strList = new ArrayList<String>();
                            return String.format("%s", strList);
                        } else {
                            strList.add(parameters[1]);
                            return String.format("%s", strList);
                        }
                    } else {
                        return "404 Not Found!";
                    }
                } else if (url.getPath().contains("search")) {
                    String[] parameters = url.getQuery().split("=");
                    List<String> found = new ArrayList<String>();

                    if (parameters[0].contains("s")) {

                        for (String str : strList) {
                            if (str.contains(parameters[1])) {
                                found.add(str);
                            }
                        }
                    }
                    return String.format("%s", found);
                } else {
                    return String.format("%s", strList);
                }
            }
            return "404 Not Found!";
        }
    }

        class NumberServer {
            public static void main(String[] args) throws IOException {
                if(args.length == 0){
                    System.out.println("Missing port number! Try any number between 1024 to 49151");
                    return;
                }

                int port = Integer.parseInt(args[0]);

                Server.start(port, new Handler());
            }
        }

## Terminal commands

> After having these code in the SearchEngine.java file, open a new terminal and execute the two commands below to compile and run the code. 
> This block of code determines that the number of the server. The random number 4020 that I typed in the terminal commands will later appear in my web server's path.
> 

            class NumberServer {
                public static void main(String[] args) throws IOException {
                    if(args.length == 0){
                        System.out.println("Missing port number! Try any number between 1024 to 49151");
                        return;
                    }

                    int port = Integer.parseInt(args[0]);

                    Server.start(port, new Handler());
                }
            }
> After seeing the message that the server has started, click on the link in the terminal. Once you see the website below, it means that you have successfully implemented a web server, which tracks the list of strings. 

> The code in the file SearchEngine.java shown above would support you to edit the path and add strings to an empty list.

<img width="859" alt="Screen Shot 2022-10-14 at 10 41 51 PM" src="https://user-images.githubusercontent.com/114328188/195971083-5209f055-9081-4dd0-be03-7ccdb7954bf4.png">

<img width="789" alt="Screen Shot 2022-10-14 at 10 42 27 PM" src="https://user-images.githubusercontent.com/114328188/195971085-ba8cc505-5eef-4b56-ab6a-9593edc26678.png">

<img width="788" alt="Screen Shot 2022-10-14 at 10 46 39 PM" src="https://user-images.githubusercontent.com/114328188/195971144-31b2934e-9e0f-4aab-8c7b-d61e6c6a042e.png">

<img width="789" alt="Screen Shot 2022-10-14 at 10 43 49 PM" src="https://user-images.githubusercontent.com/114328188/195971087-2eb9b627-fb9c-4ce1-ae1a-d3725263e284.png">

<img width="788" alt="Screen Shot 2022-10-14 at 10 44 27 PM" src="https://user-images.githubusercontent.com/114328188/195971091-41f2fa31-4f44-4020-aa7e-ea718ae3a054.png">

<img width="894" alt="Screen Shot 2022-10-14 at 10 58 43 PM" src="https://user-images.githubusercontent.com/114328188/195971528-db6c27c3-c9cd-4672-ba88-ede7e7d45b91.png">

---
# Part Two 
## Bugs and Symptoms



