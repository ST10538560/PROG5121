import java.util.Scanner;
class Login {
    public String username;
    public String password;
    public String cellPhoneNumber;
    public String firstName;
    public String lastName;

    
    public boolean checkUserName() {
        return username.contains("_") && username.length() <= 5;
    }
    
    public boolean checkPasswordComplexity() {
        boolean hasCapital = false;
        boolean hasNumber = false;
        boolean hasSpecial = false;

        for (int i = 0; i < password.length(); i++) {
            char ch = password.charAt(i);
            hasCapital = hasCapital || Character.isUpperCase(ch);
            hasNumber = hasNumber || Character.isDigit(ch);
            hasSpecial = hasSpecial || !Character.isLetterOrDigit(ch);
        }

        return password.length() >= 8 && hasCapital && hasNumber && hasSpecial;
    }

    
    public boolean checkCellPhoneNumber() {
        return cellPhoneNumber.startsWith("+27") && cellPhoneNumber.length() == 12;
    }

    public String registerUser() {
        String userMsg = checkUserName() 
            ? "Username successfully captured." 
            : "Username is not correctly formatted; please ensure that your username contains an underscore and is no more than five characters in length.";

        String passMsg = checkPasswordComplexity() 
            ? "Password successfully captured." 
            : "Password is not correctly formatted; please ensure that the password contains at least eight characters, a capital letter, a number, and a special character.";

        String cellMsg = checkCellPhoneNumber() 
            ? "Cell phone number successfully added." 
            : "Cell phone number incorrectly formatted or does not contain international code.";

        return checkUserName() && checkPasswordComplexity() && checkCellPhoneNumber()
            ? userMsg + "\n" + passMsg + "\n" + cellMsg
            : (!checkUserName() ? userMsg : (!checkPasswordComplexity() ? passMsg : cellMsg));
    }

   
    public boolean loginUser(String enteredUsername, String enteredPassword) {
        return this.username.equals(enteredUsername) && this.password.equals(enteredPassword);
    }

    
    public String returnLoginStatus(boolean isLoggedIn) {
        return isLoggedIn 
            ? "Welcome " + firstName + " " + lastName + " it is great to see you again." 
            : "Username or password incorrect, please try again.";
    }
}

 
public class Main {
    public static void main(String[] args) {
        try (Scanner sc = new Scanner(System.in)) {
            Login user = new Login();
            
            System.out.print("Enter first name: ");
            user.firstName = sc.nextLine();
            
            System.out.print("Enter last name: ");
            user.lastName = sc.nextLine();
            
            System.out.print("Enter username: ");
            user.username = sc.nextLine();
            
            System.out.print("Enter password: ");
            user.password = sc.nextLine();
            
            System.out.print("Enter cell phone number: ");
            user.cellPhoneNumber = sc.nextLine();
            
   
            System.out.println(user.registerUser());
            
           
            System.out.println("\n--- Login ---");
            System.out.print("Enter username: ");
            String loginUser = sc.nextLine();
            
            System.out.print("Enter password: ");
            String loginPass = sc.nextLine();
            
            boolean isSuccess = user.loginUser(loginUser, loginPass);
            System.out.println(user.returnLoginStatus(isSuccess));
        }
    }
}





/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/UnitTests/JUnit5TestClass.java to edit this template
 */

import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.AfterAll;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

/**
 *
 * @author Student
 */
public class LoginTest {
    
    public LoginTest() {
    }
    
    @BeforeAll
    public static void setUpClass() {
    }
    
    @AfterAll
    public static void tearDownClass() {
    }
    
    @BeforeEach
    public void setUp() {
    }
    
    @AfterEach
    public void tearDown() {
    }

    /**
     * Test of checkUserName method, of class Login.
     */
    @Test
    public void testCheckUserName() {
        System.out.println("checkUserName");
        Login instance = new Login();
        instance.username="nono";
        boolean expResult = false;
        boolean result = instance.checkUserName();
        assertEquals(expResult, result);
       
    }
@Test
    public void testCheckUserNametrue() {
        System.out.println("checkUserName");
        Login instance = new Login();
        instance.username="nono_";
        boolean expResult = true;
        boolean result = instance.checkUserName();
        assertEquals(expResult, result);
       
    }

    /**
     * Test of checkPasswordComplexity method, of class Login.
     */
    @Test
    public void testCheckPasswordComplexity() {
        System.out.println("checkPasswordComplexity");
        Login instance = new Login();
        instance.password="ibaaa";
        boolean expResult = false;
        boolean result = instance.checkPasswordComplexity();
        assertEquals(expResult, result);
        
    }
    @Test
    public void testCheckPasswordComplexitytrue() {
        System.out.println("checkPasswordComplexity");
        Login instance = new Login();
        instance.password="Ibanathi@2";
        boolean expResult = true;
        boolean result = instance.checkPasswordComplexity();
        assertEquals(expResult, result);
        
    }

    /**
     * Test of checkCellPhoneNumber method, of class Login.
     */
    @Test
    public void testCheckCellPhoneNumber() {
        System.out.println("checkCellPhoneNumber");
        Login instance = new Login();
        instance.cellPhoneNumber="0823931115";
        boolean expResult = false;
        boolean result = instance.checkCellPhoneNumber();
        assertEquals(expResult, result);
        
    }
@Test
    public void testCheckCellPhoneNumbertrue() {
        System.out.println("checkCellPhoneNumber");
        Login instance = new Login();
        instance.cellPhoneNumber="+27823931115";
        boolean expResult = true;
        boolean result = instance.checkCellPhoneNumber();
        assertEquals(expResult, result);
        
    }
    /**
     * Test of registerUser method, of class Login.
     */
   
    /**
     * Test of returnLoginStatus method, of class Login.
     */
    @Test
    public void testReturnLoginStatus() {
        System.out.println("returnLoginStatus");
        boolean isLoggedIn = false;
        Login instance = new Login();
        String expResult = "Username or password incorrect, please try again.";
        String result = instance.returnLoginStatus(isLoggedIn);
        assertEquals(expResult, result);
       
    }
    
}

