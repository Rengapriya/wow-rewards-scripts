# wow-rewards-scripts

Login:
package sample;

import java.io.File;
import java.io.IOException;

import org.eclipse.jetty.server.Response.OutputType;
import org.openqa.selenium.By;
import org.openqa.selenium.TakesScreenshot;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.apache.commons.io.FileUtils;
//import com.sun.jna.platform.FileUtils;


public class Login_01 {

public static void main(String[] args) throws InterruptedException {
        
    	WebDriver driver= null;
    	 System.setProperty("webdriver.chrome.driver","D:\\chromedriver.exe");
       driver= new ChromeDriver();
       driver.get("https://uat-cms.woolworthsrewards.com.au");
       Thread.sleep(2000);
             		
       driver.findElement(By.xpath("//a[contains(@href,'/login.html')]")).click();
       Thread.sleep(1000);
        driver.findElement(By.name("username")).sendKeys("rg@w.com");
       driver.findElement(By.name("password")).sendKeys("rewardsrenga");
       driver.findElement(By.id("login-btn")).click();
        Thread.sleep(5000);
        driver.close();
      }
   }

#Join 

package sample;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;



public class Join_01 {

    public static void main(String[] args) throws InterruptedException {
        
       WebDriver driver= null;
       System.setProperty("webdriver.chrome.driver","D:\\chromedriver.exe");
       driver= new ChromeDriver();
       driver.get("https://uat-cms.woolworthsrewards.com.au/");
       
       Thread.sleep(2000);
             		
       driver.findElement(By.xpath("//a[contains(@href,'/register.html')]")).click();
       Thread.sleep(1000);
           
       Thread.sleep(5000);
       
       driver.findElement(By.id("firstname")).sendKeys("Rengapriya");
       driver.findElement(By.id("lastname")).sendKeys("Gopal");
       driver.findElement(By.id("email")).sendKeys("rgopalasubramanian@woolworths.com.au");
       driver.findElement(By.id("mobile")).sendKeys("0412365478");
       driver.findElement(By.id("password")).sendKeys("rgopal");
       driver.findElement(By.id("confirmpassword")).sendKeys("rgopal");
       driver.findElement(By.id("dateofbirth")).sendKeys("01012000");
       
       Select dropdown = new Select(driver.findElement(By.id("select-options-6768d9bf-b4d7-a86a-3433-da9f3f454f97")));
       dropdown.selectByValue("option2");
      
         Thread.sleep(5000);
       
       //driver.findElement(By.linkText("Login")).click();
          
       //driver.findElement(By.className("waves-effect waves-light")).click();
      
       driver.close();
       
}
}

Cards and accounts: 

package  sample;

import java.io.File;
import java.io.IOException;

import org.apache.commons.io.FileUtils;
import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.Keys;
import org.openqa.selenium.OutputType;
import org.openqa.selenium.TakesScreenshot;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

public class  CardAccounts_01  {
	
    public static void main(String[] args) throws InterruptedException, IOException {
            	
    	WebDriver driver= null;
    	   	
       System.setProperty("webdriver.chrome.driver","D:\\chromedriver.exe");
       driver= new ChromeDriver();
       WebDriverWait wait = new WebDriverWait(driver, 10);
       driver.get("https://uat-cms.woolworthsrewards.com.au");
       
       Thread.sleep(2000);
       driver.findElement(By.xpath("//a[contains(@href,'/login.html')]")).click();
       Thread.sleep(1000);
       driver.findElement(By.name("username")).sendKeys("rg@w.com");
       driver.findElement(By.name("password")).sendKeys("rewardsrenga");
       driver.findElement(By.id("login-btn")).click();

     //  Thread.sleep(2000); -- dont use this 
       wait.until(ExpectedConditions.elementToBeClickable(By.xpath("//*[text()='My account']")));
     
   //driver.findElement(By.xpath("//div[@class='nav-wrapper nav-desktop']/ul[@class='right']/li[7]")).click(); - working
       
       driver.findElement(By.xpath("//*[text()='My account']")).click();
       driver.findElement(By.linkText("Cards & accounts")).click();
       
  
       
   wait.until(ExpectedConditions.elementToBeClickable(By.xpath("//*[text()='Order a new card']")));
   driver.findElement(By.xpath("//*[text()='Order a new card']")).click();  
 //  driver.findElement(By.id("select-options-06e98fcd-00e6-eb94-b27e-99cba64a38d4")).click();
       
// driver.findElement(By.xpath("//a[contains(@text,'Have you lost your card, need a replacement or looking to order another card for a family member? Request a new one here, and you'll receive it within 7 days.']")).click();
       
   driver.findElement(By.xpath("//*[@id='ordercard_display']/form/div[1]/div/input")).click();
   driver.findElement(By.xpath("//*[@id='ordercard_display']/form/div[1]/div/input")).sendKeys(Keys.ARROW_DOWN); 
   driver.findElement(By.xpath("//*[@id='ordercard_display']/form/div[1]/div/input")).sendKeys(Keys.ENTER);   
   
   driver.findElement(By.xpath("//*[@id='ordercard_display']/form/div[2]/div[2]/div[1]/label")).click();
  // driver.findElement(By.id("replace_card_button")).click();
   
   JavascriptExecutor jse = (JavascriptExecutor)driver;
    jse.executeScript("window.scrollBy(0,350)", "");
   
   driver.findElement(By.xpath("//*[@id='replace_card_button_modal']")).click();
    
   
   Thread.sleep(2000);
   
   //WebElement element = driver.findElement(By.xpath("//*[text()='Great, your new card is on its way and should arrive within the next seven days.']")); 
   //String strng = element.getText();
   
   //Assert.assertEquals("Great, your new card is on its way and should arrive within the next seven days.", strng);
   
   String image="success";
	String schedule="D:";
	File screenshot=((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
	FileUtils.copyFile(screenshot,new File(schedule+"\\Screenshots\\"+image+".jpg"));

	   System.out.println("The order new card is  clicked successfully");
       Thread.sleep(5000);
       driver.close();

}
	
}

Cards and accounts 2: 

package  sample;


import java.io.File;
import java.io.IOException;

import org.eclipse.jetty.server.Response.OutputType;
import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.Keys;
import org.openqa.selenium.TakesScreenshot;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.apache.commons.io.FileUtils;


public class  CardAccounts_02 {
	
    public static void main(String[] args) throws InterruptedException {
        
    	
    	WebDriver driver= null;
    	
    	
       System.setProperty("webdriver.chrome.driver","D:\\chromedriver.exe");
       driver= new ChromeDriver();
       WebDriverWait wait = new WebDriverWait(driver, 10);
       driver.get("https://uat-cms.woolworthsrewards.com.au");
       
       Thread.sleep(2000);
       driver.findElement(By.xpath("//a[contains(@href,'/login.html')]")).click();
       Thread.sleep(1000);
       driver.findElement(By.name("username")).sendKeys("rg@w.com");
       driver.findElement(By.name("password")).sendKeys("rewardsrenga");
       driver.findElement(By.id("login-btn")).click();

     //  Thread.sleep(2000); -- dont use this 
       wait.until(ExpectedConditions.elementToBeClickable(By.xpath("//*[text()='My account']")));
     
   //driver.findElement(By.xpath("//div[@class='nav-wrapper nav-desktop']/ul[@class='right']/li[7]")).click(); - working
       
       driver.findElement(By.xpath("//*[text()='My account']")).click();
       driver.findElement(By.linkText("Cards & accounts")).click();
       
       
       wait.until(ExpectedConditions.elementToBeClickable(By.xpath("//*[text()='Link other Woolworths Rewards cards']")));
       driver.findElement(By.xpath("//*[text()='Link other Woolworths Rewards cards']")).click(); 
       
       driver.findElement(By.name("cardNumber")).sendKeys("987456321456");
              
              
    }
}
       


