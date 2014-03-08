Start up java
Make class 
declare global variables
  set the scanner
  start method
  private static Zoo a[];
  private static Scanner in = new Scanner(System.in);
Make a while loop to repeat the question
    prompt user for what animal they want to choose
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
End method
Make new method for menu
 prompt user for animal
create an  exception for an unknown animal (not in text file), and display a not found message
ask user what info they want from the animal
allow the user to choose between either their nickname,weight,height,species,animal, or location
make a new method and ask the user if they want to update the info they have
If the answer is yes send them to the next part, if not end the program
  set exception for any input that does not make sense
user chooses what they want to update
End method

Make a method to //scan through the text file to retrieve info on each animal
set a loop to read through every line of the text file
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
End method
Make a new method to make a find method to post the info needed, when called for by the user
End method 
End program


