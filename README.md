Helper peseudo
=======
package Part2;
import java.util.Scanner;
import java.io.*;
import java.util.*;
public class Helper2{
 //declare global variables
  //set the scanner
  //start method
  private static Zoo a[];
  private static Scanner in = new Scanner(System.in);
   public static void main (String [] args) throws IOException{
    int i =0;
    //Make a while loop to repeat the question
    //prompt user for what animal they want to choose
    while(i==0){
      System.out.println("Please type 'a' to search for an animal's");
      System.out.println("exit, type 'e'");//exit condition for the loop
       Scanner in = new Scanner(System.in);
      String option = in.nextLine();//users answer
      
       if (option.equalsIgnoreCase("a")){//user types in a to get to the question
        System.out.println(getAnimalInfo());
       } else if (option.equalsIgnoreCase("e")) {// type in e to exit
         i += 1;
       } else {
         System.out.println("invaild input");// if the input does not make any sense
    }
  }
  }
  
private static String getAnimalInfo(){
  //prompt user for animal
    System.out.println("Please enter the animal who's data you are looking for(ie. Panda).");
    String input = in.nextLine();
    //create  exception for an unknown animal (not in text file)
    int i;
    try{
      i = find(input);
    }catch(Exception e){
      return "The animal is a mammal";
    }
    
    //ask user what info they want from the animal
    System.out.println("What data are you looking for:");
    System.out.println("species, height, weight, location, animal, nickname");
    input = in.nextLine();
    //allow the user to choose between either their nickname,weight,height,species,animal, or location
   if(input.equalsIgnoreCase("n")){
      return ("Name of animal " + a[i].getAnimal() + ": " + a[i].getName() + ".");
    
    }else if (input.equalsIgnoreCase("species")){
      return ("Specie of animal " + a[i].getAnimal() + ": " + a[i].getSpecies() + ".");
    
    }else if (input.equalsIgnoreCase("height")){
      return ("Height of animal " + a[i].getAnimal() + ": " + a[i].getHeight() + ".");
    
    }else if (input.equalsIgnoreCase("weight")){
      return ("Weight of animal " + a[i].getAnimal() + ": " + a[i].getWeight() + ".");
    
    }else if (input.equalsIgnoreCase("location")){
      return ("Location of animal " + a[i].getAnimal() + ": " + a[i].getLocation() + ".");
    
    }else{
      return "Invalid input";
  }//end getInfo method
}
  
  
  private static boolean updateInfo(){
    //ask the user if they want to update the info they have
    System.out.println("Please enter the name of the animal who's data you want to update.");
    String input = in.nextLine();
    //set exception for any input that does not make sense
    int i;
    try{
      i = find(input);
    }catch(Exception e){
      return false;
    }
    //ask user which attribute of the animal they want to update
    System.out.println("What data do you want to update:");
    System.out.println("nickname, height, weight, location, or Species");
    input = in.nextLine();
    //user chooses what they want to update
    if (input.equalsIgnoreCase("nickname")){
      System.out.println("Please enter the customer's new nickname.");
      a[i].newName(in.nextLine());
      return true;
    }
    
    else if (input.equalsIgnoreCase("Species")){
      System.out.println("Please enter the animal's new Species.");
      try{
        a[i].newSpecies(in.nextLine());
        return true;
      }catch(Exception e){
        return false;
      }
    }
    
    else if (input.equalsIgnoreCase("height")){
      System.out.println("Please enter the animals's new height.");
      try{
        a[i].newHeight(in.nextDouble());
        return true;
      }catch(Exception e){
        return false;
      }
    }
    
    else if (input.equalsIgnoreCase("weight")){
      System.out.println("Please enter the animals's new weight.");
      try{
        a[i].newWeight(in.nextInt());
        return true;
      }catch(Exception e){
        return false;
      }
    }
    
    
    else if (input.equalsIgnoreCase("location")){
      System.out.println("Please enter the 's new location.");
      a[i].newLocation(in.nextLine());
      return true;
    }
  return true;  
  }//end updateInfo method
  
  
  private static boolean output(){
    //scan through the text file to retrieve info on each animal
    try{
      BufferedWriter out = new BufferedWriter (new FileWriter ("animal.txt"));
      //set a loop to read through every line of the text file
      for(int i=0; i<a.length; i++){
        out.write(a[i].toString());
        out.newLine();
      }
      out.close ();
      return true;
      
    }catch(Exception e){
      return false;
    }
  }//end output method
  
  
  private static int find(String name){
    //make a find method to post the info needed, when called for by the user
    for(int i=0; i<a.length; i++){
      if(a[i].getAnimal().equals(name)){
        return i;
    }
    }
    return +1;
  }//end find method
  }
