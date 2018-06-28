
import java.util.Scanner;

public class AddDigits{

   
    public static boolean validateInput(int number1, int number2) //method that takes two numbers as input and returns true if the sum of digits is same else returns false

    {
        boolean result = false;       // initialize variable false initially
        if(number1 != 0 || number2 != 0 )  // except condition if one of the number is 0 because our logic to check length of numbers fails on input 0 because we can't take log of 0
        {
        int length1 = (int) (Math.log10(number1) + 1); //For the numbers represented in decimal form, if we take their log in base 10 and round it up then we’ll get the number of digits in that number
        int length2 = (int) (Math.log10(number2) + 1);

            if (length1 == length2) { // if lengths are same

                String num1 = String.valueOf(number1);   //convert the integer into String
                String num2 = String.valueOf(number2);
                result = true;                           //If length is same initially set result = true
                int sum = Character.digit(num1.charAt(0), 10) + Character.digit(num2.charAt(0), 10); // Get first character from string of num 1 and num2 and convert them to integers and add them 
                     
                for (int i = 0; i < num1.length(); i++) {  //loop of the length of num1 because we have checked that lengths are same 
                    int x = Character.digit(num1.charAt(i), 10); //get character from string of number 1 and convert to integer
                    int y = Character.digit(num2.charAt(i), 10);

                    if ((x+y) != sum) { // if at any case sum of two digits of a number is not same as the sum of first digits 
                        result = false;  // set result to false
                    }

                }

                //otherwise it will remain true and true will be printed
            }

            
        }
        else{ // if there was 0 in any number
            
            if(number1 == number2)  //if they both are 0 then there sum will also be same as 0
            {
                result = true;    //so set result to true
            }
            else{                 //else it will be false
                result = false;
            }
        }

        
        return result;    //at the end we return this result variable
    }
    
    public static void main(String[] args) {
        
        Scanner input = new Scanner(System.in);
        System.out.println("Please enter first number: "); //Take user inputs
        int number1 = input.nextInt();  
        System.out.println("Please enter first number: "); //Take user input
        int number2 = input.nextInt();
        boolean result = validateInput(number1,number2);   //Call method validateInput to validate the input numbers
        System.out.println("Result: "+result);
     
    }
    
}
