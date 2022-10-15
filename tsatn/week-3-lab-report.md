# CSE 15L Lab 2
Teresa Tian

A16878664

## code for SearchEngine.java

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
<img width="593" alt="Screen Shot 2022-10-14 at 6 42 54 PM" src="https://user-images.githubusercontent.com/114328188/195963559-7ec209c5-4654-4660-8cb9-10213e4441e1.png">

<img width="1507" alt="Screen Shot 2022-10-14 at 6 43 49 PM" src="https://user-images.githubusercontent.com/114328188/195963543-cc9dd0be-3b2c-4df6-b8d9-42dc72b8ef34.png">

