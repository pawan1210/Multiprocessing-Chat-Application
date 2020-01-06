
import java.util.*;

public class Main
{   
    // The map used here is for storing initial queries.
    static HashMap<String,String>map=new HashMap<>();
    
    
     /* 
       In case the query entered by the user is not found in the first Hashmap. Then 'kewywords' map which is defined
       below is used.
       The structure of this map is as follows.
        
            -->query0
        key -->query1 
            -->query2
            ...........
            
       Here key is a ' String ' variable and the value of this key is an arraylist of queries.            
       The 'keywords' HashMap contains all the keywords of queries stored in the map used above.So every word 
       of the query entered by the user is searched in this map.
    
    */
    static HashMap<String,ArrayList<String>>keywords=new HashMap<>();
    
   
    
    
    
    // readyBot() function is used to store the initial queries for the bot. This can be altered easily.
    
    public static void readyBot1(){
        map.put("hi","Hello. I am a chatbot.I can try and answer some of your questions. For questions i cannot answer i will have to email a colleague at work.So, How can i help you?");
        map.put("what does finhawk do","We are going to bring about change in the Indian Financial and Fintech scene for the betterment of all participants.");
        map.put("where are you based","Gurgaon");
        map.put("how does your site work","We provide solutions regarding Education and Finance technology");
        map.put("okay","Thanks for visiting our site. Any more questions?");
        for(String key:map.keySet()){
            readyBot2(key);
        }
    }
    
    
    /* 
        readybot2() function is used to store the keywords in the 'keywords' map. 
        Firstly with readyBot1() function we store queries and then for every query
        we call the readyBot2()  function which splits the query into keywords and store
        them in the 'keywords' map with their respective queries.

    */
    public static void readyBot2(String str){
       
       String arr[]=str.split(" ");
       for(int i=0;i<arr.length;i++){
            if(keywords.containsKey(arr[i])){
               keywords.get(arr[i]).add(str);
            }
            else{
                ArrayList<String>tempList=new ArrayList<>();
                tempList.add(str);
               keywords.put(arr[i],tempList);
            }
       }
    }
   
    /*
    
        parseQuery() function is used to parse the query entered by the user.
        
        str.trim() --> Removes backspaces from beginning and end of the string.
        .toLowerCase()--> used to convert all the characters to lowercase.
        str.split() --> Splits the string into seperate words.
        
       - Firstly we trim the string and then convert it into lowercase as all the queries
         in the queries map are in lowercase.
       - Then we remove special characters from every word of that string. like "?".
       - Then we combine all the parsed words.(I used words here because we first divided the string into
          seperate words and then removed special characters from those words).
       
        
    */
    public static String parseQuery(String query){
        query=query.trim();
        query=query.toLowerCase();
        String output="";
        String arr[]=query.split(" ");
        for(int j=0;j<arr.length;j++)
        {
            String temp=arr[j];
            for (int i=0; i<temp.length();i++) 
            { 
                if (temp.charAt(i) < 'A' || temp.charAt(i) > 'Z' && temp.charAt(i) < 'a' || temp.charAt(i) > 'z')  
                {  
                    temp=temp.substring(0, i)+temp.substring(i + 1); 
                    i--; 
                } 
            }
            output+=temp+" ";
        }
        
        return output.substring(0,output.length()-1);
    }

    public static void human(Scanner s){
         
     System.out.println("My apologies.I will have to get help of my colleague to solve your query.Please enter just a keyword now.");
		 System.out.println("--------------------------------------------------------------------------------------------------------");           
		 System.out.print("                         ");
		 String newQuery=s.nextLine();          
		 boolean flag=false;
		
		 String arr[]=newQuery.split(" ");
		 System.out.println("--------------------------------------------------------------------------------------------------------");
		            for(int i=0;i<arr.length;i++){
		                if(keywords.containsKey(arr[i])){
		                    flag=true;          
		                    Random r=new Random();
		                    int randomIndex=r.nextInt(keywords.get(arr[i]).size());
		                    newQuery=keywords.get(arr[i]).get(randomIndex);
		                    System.out.println(map.get(newQuery));
		                    System.out.print("------------------------------------------------------------------------------------");
		                    System.out.println();
		               }
		            }
		            
		            if(flag==false){
		                 System.out.println("(--- Now as a human support enter the answer for query entered by the user. We need to assume that the user doesn't see this part.---)");
		                 String help=s.nextLine();
		                 ArrayList<String>tempList=new ArrayList<>();
		                 tempList.add(help);
		                 keywords.put(newQuery,tempList);
		                 System.out.print("------------------------------------------------------------------------------------");
		                 System.out.println();
		            }    
    
        
    }
	public static void main(String[] args) {
	    Scanner s=new Scanner(System.in);
	    readyBot1();
	    System.out.println("Hey there ..");
	    System.out.println("Let's get you started.Ask me a question regarding the site or the services we provide.");
		System.out.print("------------------------------------------------------------------------------------");
		System.out.println();
		int count=0;
		while(true){
		   System.out.print("                       ");
		    String query=s.nextLine();
		    if(query.equals("quit")){
		        return;
		    }
		    System.out.println("------------------------------------------------------------------------------------");
		    query=parseQuery(query);
		    
		    
		    /*
		      
		      The first if condition is executed when the query entered by the user matches
		      exactly with a query in the queries map.
		      We simply return the stored answer for that query.
		      
		    */
		    if(map.containsKey(query)){
		        String answer=map.get(query);
		        System.out.println(answer);
		        System.out.print("------------------------------------------------------------------------------------");
		        System.out.println();
		    }
		    
		    /*
		    
		        In this part we take human support to answer the query.
		        We use the human() function defined above.
		        The count variable is the key variable here.
		        Count can take 2 values.
		        
		        when value of count is 1-> We ask the user to ask his/her query again.
		        
		        when value of count is 2-> We split the query entered by the user and search in
		                                   the keywords map for every word. If we find a match
		                                   then we simply get the query associated with that word
		                                   and return answer for that query.
		                                   
		       *** Use of random function- After all we are implementing a bot here. So the bot can't 
		                                   simply predict what the user is asking. So it just find all
		                                   all the queries associated with that word and choose a random 
		                                   query from them and return the answer for that query.
		                                   
		      ** Now if we don't find the keyword in the keywords map. We take help from another person which will
		         help the bot now. So he will enter the answer and before returning it it will enter the keyword in
		         the keywords map so that it can be used in future also.
		    */
		    else{
		            count++;
		            if(count==1){
		                System.out.println("I am sorry. I don't have an answer for this. Please try again with more information.");
		                System.out.print("------------------------------------------------------------------------------------");
		                System.out.println();
		                continue;
		            }
		            
		            human(s);
		            count=0;
		       }
		    }
		}
	}
