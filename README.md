package ConsolidatedFlow;

import java.io.IOException;
import java.util.ArrayList;
import java.util.List;

import org.apache.log4j.Logger;
import org.apache.log4j.PropertyConfigurator;
import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;

public class ConsolidatedFlow {

	public static void main(String[] args) throws InterruptedException, IOException {
		// TODO Auto-generated method stub

		//Logger Implementation
		
	    Logger logger = Logger.getLogger("ConsolidatedFlow");
		PropertyConfigurator.configure("Log4j.properties");

		//Open Chrome Browser
		   
		String exePath = "C:\\SeleniumDrivers\\chromedriver.exe";
		System.setProperty("webdriver.chrome.driver", exePath);
		WebDriver driver = new ChromeDriver();
		logger.info("Chrome Opened Successfully");
		
		//Maximize Chrome Browser
		
		driver.manage().window().maximize();
		logger.info("Chrome Maximized Successfully");
		
		//SIGNUP FLOW
		
		//Navigate Register Page
		
		    driver.get("https://panel.izooto.com/register");
		    logger.info("Register Page Opened Successfully");
		    
		    driver.findElement(By.xpath("/html//input[@id='name']")).sendKeys("Dummy Iz"); 
		    Thread.sleep(2000);
		    driver.findElement(By.xpath("/html//input[@id='email']")).sendKeys("dummyizsigningo0021@gmail.com");
		    Thread.sleep(2000);
		    driver.findElement(By.xpath("/html//input[@id='password']")).sendKeys("1234567");
		    Thread.sleep(2000);
		    driver.findElement(By.xpath("/html//input[@id='phone']")).sendKeys("9898723457");
		    Thread.sleep(2000);
		    driver.findElement(By.xpath("/html//input[@id='domain']")).sendKeys("http://dummyizsigninfo11111.com");
		    Thread.sleep(2000);
		    driver.findElement(By.xpath("/html//button[@id='form_button']")).click();
		    driver.findElement(By.xpath("/html//button[@id='form_button']")).click();
		    logger.info("Signed Up Successfully");
		    
		    Thread.sleep(6000);
		    
		    // click continue button
		    driver.findElement(By.xpath("//div[@id='onboarding-carousel']/div[@class='carousel-inner container pl-0']/div[1]/div[@class='col-md-7 pl-0 pr-0']//a[@href='javascript:void(0)']")).click();
		    
		    Thread.sleep(3000);
		  
		    // again continue button
		    driver.findElement(By.xpath("//div[@id='onboarding-carousel']/div[@class='carousel-inner container pl-0']/div[2]/div[@class='col-md-7 pl-0 pr-0']//a[@href='javascript:void(0)']")).click();
		    
		    Thread.sleep(3000);
		    driver.findElement(By.xpath("//div[@id='onboarding-carousel']/div[@class='carousel-inner container pl-0']/div[3]/div[@class='col-md-7 pl-0 pr-0']//div[@class='education-button']/a[2]")).click();
		   
		    // install izooto
		    Thread.sleep(3000);
		    driver.findElement(By.xpath("//div[@id='onboarding-carousel']/div[@class='carousel-inner container pl-0']/div[4]/div[@class='col-md-7 pl-0 pr-0']//a[@href='javascript:void(0)']")).click();
		    
		   //Navigate to Dashboard
		    Thread.sleep(3000);
		    driver.findElement(By.xpath("/html//a[@id='complete-integration']")).click();
		    logger.info("Dashboard Opened Successfully");
		    		
			         Thread.sleep(5000);	
			         
			         //Refresh Page
			         driver.navigate().refresh();
		    
		    //Logout so that we can login again
		    try
				       {	
					WebElement signout = driver.findElement(By.xpath("/html//a[@id='dropdownMenu2']"));
					signout.click();
					Thread.sleep(3000);
					WebElement signout1 = driver.findElement(By.xpath("//header[@id='mainheader']/div/div[3]/ul/li/div/ul[@class='media-list']//a[@href='https://panel.izooto.com/logout']"));
				        System.out.println("-----Logout Clicked-----\n------");
					signout1.click();
				        }
				    catch(Throwable e)
				        {
					System.out.println("Logged out successfully: "+e.getMessage());
				        }
				    
				    logger.info("Logged Out Successfully");
				    
				    Thread.sleep(3000);
				    
				  //Forgot Password Cases
				    
				  //Navigate Panel
					driver.get("https://panel.izooto.com");
					System.out.println("--------panel.izooto.com opened----\n-----");
					logger.info("Panel Navigated Successfully");
					
					Thread.sleep(2000);
					//Click Forgot Password
					driver.findElement(By.xpath("//form[@id='loginForm']/div[@class='form-group']//a[@href='https://panel.izooto.com/reset-password-view']")).click();
					logger.info("Forgot Password link clicked Successfully");
					
					//CASE 1 - When Email is blank  	            
					Thread.sleep(2000);
				    driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/validate-for-reset']/input[@value='Send New Password']")).click();
				    Thread.sleep(2000); 
				      String actualMsg1 = driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/validate-for-reset']/input[@value='Send New Password']")).getText();
				      System.out.println("Email ID Cannot be blank");
				      String errorMsg1= "Blank email id";

				    	 if(actualMsg1.equals(errorMsg1)) {
				    	  System.out.println("Test Case Passed");
				    	    		    }
				    	    		else
				    	    		{
				    	    		        System.out.println("Test Case Failed");
				    	    		    }
				    	  
				    	            logger.info("Case 1 - Passed successfuly - Email id is blank");
				    	            
				    	          //CASE 2 - When Email is wrong  	            
				    	    		Thread.sleep(2000);
				    	    		driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/validate-for-reset']//input[@name='email']")).sendKeys("neha@");
				    	    	    driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/validate-for-reset']/input[@value='Send New Password']")).click();
				    	    	    Thread.sleep(2000); 
				    	    	      String actualMsg11 = driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/validate-for-reset']/input[@value='Send New Password']")).getText();
				    	    	      System.out.println("Email ID is invalid");
				    	    	      String errorMsg11= "Invalid email id";

				    	    	    	 if(actualMsg11.equals(errorMsg11)) {
				    	    	    	  System.out.println("Test Case Passed");
				    	    	    	    		    }
				    	    	    	    		else
				    	    	    	    		{
				    	    	    	    		        System.out.println("Test Case Failed");
				    	    	    	    		    }
				    	    	    	//clear fields
						   		    		Thread.sleep(2000);
						   		    		driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/validate-for-reset']//input[@name='email']")).clear();
						   		    		
				    	    	    	  logger.info("Case 2 - Passed successfuly - Email id is invalid");
				    	    	    	  
				    	    	    	  //CASE 3 - When Email is wrong 
				    	    	    	  
				    	    	    	  Thread.sleep(2000);
				  	    	    		driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/validate-for-reset']//input[@name='email']")).sendKeys("neha@ hello/opt.com/lk");
				  	    	    	    driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/validate-for-reset']/input[@value='Send New Password']")).click();
				  	    	    	    Thread.sleep(2000); 
				  	    	    	      String actualMsg111 = driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/validate-for-reset']/input[@value='Send New Password']")).getText();
				  	    	    	      System.out.println("Email ID is invalid");
				  	    	    	      String errorMsg111= "Invalid email id";

				  	    	    	    	 if(actualMsg111.equals(errorMsg111)) {
				  	    	    	    	  System.out.println("Test Case Passed");
				  	    	    	    	    		    }
				  	    	    	    	    		else
				  	    	    	    	    		{
				  	    	    	    	    		        System.out.println("Test Case Failed");
				  	    	    	    	    		    }
				  	    	    	    	//clear fields
				  			   		    		Thread.sleep(2000);
				  			   		    		driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/validate-for-reset']//input[@name='email']")).clear();
				  			   		    		
				  	    	    	    	  logger.info("Case 3 - Passed successfuly - Email id is invalid");
				  	    	    	    	  
				  	    	    	    	  //CASE 4 - Enter Correct Email ID and send Reset Password Link
				  	    	    	    	  
				  	    	    	    	Thread.sleep(2000);
				  	    	    			driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/validate-for-reset']//input[@name='email']")).sendKeys("neha@datability.co");
				  	    	    			Thread.sleep(2000);
				  	    	    			driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/validate-for-reset']/input[@value='Send New Password']")).click();
				  	    	    			Thread.sleep(5000);
				  	    	    			logger.info("Reset Password Request Sent Successfully");
				  	    	    			
				  	    	    		//Open Gmail
				  	    	    			driver.get("https://accounts.google.com/signin/v2/identifier?flowName=GlifWebSignIn&flowEntry=ServiceLogin");
				  	    	    			Thread.sleep(2000);
				  	    	    			driver.findElement(By.xpath("/html//input[@id='identifierId']")).sendKeys("neha@datability.co");
				  	    	    			driver.findElement(By.xpath("//div[@id='identifierNext']/content[@class='CwaK9']")).click();
				  	    	    			Thread.sleep(3000);
				  	    	    			driver.findElement(By.xpath("/html//div[@id='password']//input[@name='password']")).sendKeys("Neha@1992");
				  	    	    			driver.findElement(By.xpath("//div[@id='passwordNext']//span[@class='RveJvd snByac']")).click();
				  	    	    			logger.info("Logged In to Gmail Successfully");
				  	    	    			
				  	    	    			Thread.sleep(2000);
				  	    	    			//Inbox Opened
				  	    	    			driver.get("https://mail.google.com/mail/u/0/?tab=km#inbox");
				  	    	    			logger.info("Inbox Opened Successfully");
				  	    	    			
				  	    	    			//Open Specific Reset Password Mail
				  	    	    			Thread.sleep(5000);
				  	    	    			List<WebElement> a = driver.findElements(By.xpath("//*[@class='yW']/span"));
				  	    	    			System.out.println(a.size());
				  	    	    			            for(int i=0;i<a.size();i++){
				  	    	    			                System.out.println(a.get(i).getText());
				  	    	    			                if(a.get(i).getText().equals("Support")){  // if u want to click on the specific mail then here u can pass it
				  	    	    			                    a.get(i).click();
				  	    	    			                }
				  	    	    			            }
				  	    	    			            logger.info("Reset Password Mail Opened Successfully");
				  	    	    			            
				  	    	    			            //Click on click here link received in mail
				  	    	    			            Thread.sleep(2000);
				  	    	    						 String oldTab = driver.getWindowHandle();
				  	    	    						    driver.findElement(By.linkText("click here")).click();
				  	    	    						    logger.info("Link Clicked Successfully");
				  	    	    						    
				  	    	    						   //Change focus to new tab
				  	    	    						    ArrayList<String> newTab = new ArrayList<String>(driver.getWindowHandles());
				  	    	    						    newTab.remove(oldTab);
				  	    	    						    driver.switchTo().window(newTab.get(0));
				  	    	    						    assertclickhere();
				  	    	    						  logger.info("Case 4 - Passed successfully - Email opened and link clicked successfully");
				  	    	    						 
				  	    	    						//CASE 5 - Leave Password and Re-Enter Password Blank
				  	    	    						    
				  	    	    						Thread.sleep(2000);
				  	    	    						driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/change-password-after-auth']/button[@type='submit']")).click();
				  	    	    						Thread.sleep(2000); 
				  	    	  	    	    	      String actualMsga= driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/change-password-after-auth']/button[@type='submit']")).getText();
				  	    	  	    	    	      System.out.println("Password and Re-Enter Password Blank");
				  	    		  	    	    	      String errorMsga= "Password and Re-Enter Password are Blank";

				  	    		  	    	    	    	 if(actualMsga.equals(errorMsga)) {
				  	    		  	    	    	    	  System.out.println("Test Case Passed");
				  	    		  	    	    	    	    		    }
				  	    		  	    	    	    	    		else
				  	    		  	    	    	    	    		{
				  	    		  	    	    	    	    		        System.out.println("Test Case Failed");
				  	    		  	    	    	    	    		    }
				  	    		  	    	    	    	
				  	    		  	    	    	    	  logger.info("Case 5 - Passed successfuly - Password and Re-Enter Password Blank");
				  	    		  	    	    	    	  
				  	    		  	    	    	    //CASE 6 - Leave Password Field Blank
				  	    		  	    	    	    	  
				  	  	    	    						Thread.sleep(2000);
				  	  	    	    					driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/change-password-after-auth']//input[@name='pwd2']")).sendKeys("123456");
				  	  	    						     Thread.sleep(2000);
				  	  	    	    						driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/change-password-after-auth']/button[@type='submit']")).click();
				  	  	    	    						Thread.sleep(2000); 
				  	  	    	  	    	    	      String actualMsga1= driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/change-password-after-auth']/button[@type='submit']")).getText();
				  	  	    	  	    	    	      System.out.println("Password is Blank");
				  	  	    		  	    	    	      String errorMsga1= "Password field is Blank";

				  	  	    		  	    	    	    	 if(actualMsga1.equals(errorMsga1)) {
				  	  	    		  	    	    	    	  System.out.println("Test Case Passed");
				  	  	    		  	    	    	    	    		    }
				  	  	    		  	    	    	    	    		else
				  	  	    		  	    	    	    	    		{
				  	  	    		  	    	    	    	    		        System.out.println("Test Case Failed");
				  	  	    		  	    	    	    	    		    }
				  	  	    		  	    	    	    	 
				  	  	    		  	    	    	           //clear fields
					  	    		  			   		    		Thread.sleep(2000);
					  	    		  			   		    		driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/change-password-after-auth']//input[@name='pwd2']")).clear();
					  	    		  			   		    		
				  	  	    		  	    	    	    	
				  	  	    		  	    	    	    	  logger.info("Case 6 - Passed successfuly - Password field is Blank");
				  	  	    		  	    	    	    	  
				  	  	    		  	    	    	    //CASE 7 - Leave Re-Enter Password Field Blank
					  	    		  	    	    	    	  
				  	  	  	    	    						Thread.sleep(2000);
				  	  	  	    	    					driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/change-password-after-auth']//input[@name='pwd1']")).sendKeys("123456");
				  	  	  	    						     Thread.sleep(2000);
				  	  	  	    	    						driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/change-password-after-auth']/button[@type='submit']")).click();
				  	  	  	    	    						Thread.sleep(2000); 
				  	  	  	    	  	    	    	      String actualMsga11= driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/change-password-after-auth']/button[@type='submit']")).getText();
				  	  	  	    	  	    	    	      System.out.println("Re-Enter Password is Blank");
				  	  	  	    		  	    	    	      String errorMsga11= "Re-Enter Password field is Blank";

				  	  	  	    		  	    	    	    	 if(actualMsga11.equals(errorMsga11)) {
				  	  	  	    		  	    	    	    	  System.out.println("Test Case Passed");
				  	  	  	    		  	    	    	    	    		    }
				  	  	  	    		  	    	    	    	    		else
				  	  	  	    		  	    	    	    	    		{
				  	  	  	    		  	    	    	    	    		        System.out.println("Test Case Failed");
				  	  	  	    		  	    	    	    	    		    }
				  	  	  	    		  	    	    	    	 
				  	  	  	    		  	    	    	           //clear fields
				  		  	    		  			   		    		Thread.sleep(2000);
				  		  	    		  			   		    		driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/change-password-after-auth']//input[@name='pwd1']")).clear();
				  		  	    		  			   		   
				  	  	  	    		  	    	    	    	  logger.info("Case 7 - Passed successfuly - Re-Enter Password field is Blank");
				  	  	  	    		  	    	    	    	  
				  	  	  	    		  	    	    	    	  //CASE 8 - Enter Password and Re-Enter Password both different
				  	  	  	    		  	    	    	    	  
				  	  	  	    		  	    	    	  driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/change-password-after-auth']//input[@name='pwd1']")).sendKeys("123456");
				  	  	  	    						      Thread.sleep(2000);
				  	  	  	    						      driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/change-password-after-auth']//input[@name='pwd2']")).sendKeys("1234");
				  	  	  	    						      Thread.sleep(2000);
				  	  	  	  	    	    						driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/change-password-after-auth']/button[@type='submit']")).click();
				  	  	  	  	    	    						Thread.sleep(2000); 
				  	  	  	  	    	  	    	    	      String actualMsga111= driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/change-password-after-auth']/button[@type='submit']")).getText();
				  	  	  	  	    	  	    	    	      System.out.println("Password and Re-Enter Password is different");
				  	  	  	  	    		  	    	    	      String errorMsga111= "Password and Re-Enter Password field are different";

				  	  	  	  	    		  	    	    	    	 if(actualMsga111.equals(errorMsga111)) {
				  	  	  	  	    		  	    	    	    	  System.out.println("Test Case Passed");
				  	  	  	  	    		  	    	    	    	    		    }
				  	  	  	  	    		  	    	    	    	    		else
				  	  	  	  	    		  	    	    	    	    		{
				  	  	  	  	    		  	    	    	    	    		        System.out.println("Test Case Failed");
				  	  	  	  	    		  	    	    	    	    		    }
				  	  	  	  	    		  	    	    	    	 
				  	  	  	  	    		  	    	    	           //clear fields
				  	  		  	    		  			   		    		Thread.sleep(2000);
				  	  		  	    		  			   		    		driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/change-password-after-auth']//input[@name='pwd1']")).clear();
				  	  		  	    		  			   		            Thread.sleep(2000);
			 		  	    		  			   		    		        driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/change-password-after-auth']//input[@name='pwd2']")).clear();
			 		  	    		  			   		    	
				  	  	  	  	    		  	    	    	    	  logger.info("Case 8 - Passed successfuly - Password and Re-Enter Password field are different");
				  	  	  	  	    		  	    	    	    	  
				  	  	  	  	    		  	    	    	    	  //CASE 9 - Enter Correct Password and Re-Enter Password
				  	  	  	  	    		  	    	    	    	  
				  	  	  	  	    		  	    	    	          Thread.sleep(2000);
				  	  	  	  	    		  	    	    	          driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/change-password-after-auth']//input[@name='pwd1']")).sendKeys("123456");
				  	  	  	  	    						              Thread.sleep(2000);
				  	  	  	  	    						              driver.findElement(By.xpath("//body/div[@class='user-page']/form[@action='https://panel.izooto.com/change-password-after-auth']//input[@name='pwd2']")).sendKeys("123456");
				  	  	  	  	    						              Thread.sleep(2000);
				  	  	  	  	    						              driver.findElement(By.xpath("//body//form[@action='https://panel.izooto.com/change-password-after-auth']/button[@type='submit']")).click();
				  	  	  	  	    						              logger.info("Password Reset Successfully");
				  	  	  	  	    						              
				  	  	  	  	    						      logger.info("Case 9 - Passed succesfully - password reset done successfully");
				  	  	  	  	    						              
				  	  	  	  	    						              //Login Testcases
				  	  	  	  	    						              
				  	  	  	  	    						              Thread.sleep(2000);
				  	  	  	  	    						              
				  	  	  	  	    						             //Navigate Panel
				  	  	  	  	  	    								driver.get("https://panel.izooto.com");
				  	  	  	  	  	    								
				  	  	  	  	    						   // CASE 10 - Both Email and Password Fields are blank.
				  	  	  	  	    							    
				  	  	  	  	    							    WebElement button = driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']"));
				  	  	  	  	    								button.click();
				  	  	  	  	    							    String actualMsg = driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).getText();
				  	  	  	  	    							    System.out.println("Email and Password Blank");
				  	  	  	  	    							    		String errorMsg= "Invalid username or password";

				  	  	  	  	    							    		if(actualMsg.equals(errorMsg)) {
				  	  	  	  	    							    		        System.out.println("Test Case Passed");
				  	  	  	  	    							    		    }
				  	  	  	  	    							    		else
				  	  	  	  	    							    		{
				  	  	  	  	    							    		        System.out.println("Test Case Failed");
				  	  	  	  	    							    		    }
				  	  	  	  	    							             
				  	  	  	  	    							    		Thread.sleep(3000);
				  	  	  	  	    							    		 //Refresh Page
				  	  	  	  	    							            driver.navigate().refresh();
				  	  	  	  	    							            Thread.sleep(3000);
				  	  	  	  	    							            
				  	  	  	  	    							            logger.info("Case 10 implemented - email and password field are blank");
				  	  	  	  	    							    		
				  	  	  	  	    							    		// CASE 11 - Email field is filled and Password field is blank
				  	  	  	  	    							            
				  	  	  	  	    							            driver.findElement(By.name("email")).sendKeys("neha@datability.co");
				  	  	  	  	    							            driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).click();
				  	  	  	  	    							    	    String actualMsg1111 = driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).getText();
				  	  	  	  	    							    	    System.out.println("Password Blank");
				  	  	  	  	    							    	    		String errorMsg1111= "Invalid username or password";

				  	  	  	  	    							    	    		if(actualMsg1111.equals(errorMsg1111)) {
				  	  	  	  	    							    	    		        System.out.println("Test Case Passed");
				  	  	  	  	    							    	    		    }
				  	  	  	  	    							    	    		else
				  	  	  	  	    							    	    		{
				  	  	  	  	    							    	    		        System.out.println("Test Case Failed");
				  	  	  	  	    							    	    		    }
				  	  	  	  	    							    	  
				  	  	  	  	    							    	    		Thread.sleep(3000);
				  	  	  	  	    							    	    		 //Refresh Page
				  	  	  	  	    							    	            driver.navigate().refresh();
				  	  	  	  	    							    	            Thread.sleep(3000);
				  	  	  	  	    							    	            
				  	  	  	  	    							    	            logger.info("Case 11 implemented - password field is blank");
				  	  	  	  	    								         
				  	  	  	  	    							      // CASE 12 - Email field is blank and Password field is filled
				  	  	  	  	    							    	            
				  	  	  	  	    							    	      driver.findElement(By.name("password")).sendKeys("neha1992");
				  	  	  	  	    							    	      driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).click();
				  	  	  	  	    							    	      String actualMsg11111 = driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).getText();
				  	  	  	  	    							    	      System.out.println("Email Blank");
				  	  	  	  	    							    	      String errorMsg11111= "Invalid username or password";

				  	  	  	  	    							    	    	 if(actualMsg11111.equals(errorMsg11111)) {
				  	  	  	  	    							    	    	  System.out.println("Test Case Passed");
				  	  	  	  	    							    	    	    		    }
				  	  	  	  	    							    	    	    		else
				  	  	  	  	    							    	    	    		{
				  	  	  	  	    							    	    	    		        System.out.println("Test Case Failed");
				  	  	  	  	    							    	    	    		    }
				  	  	  	  	    							    	    	  
				  	  	  	  	    							    	    	    		Thread.sleep(3000);
				  	  	  	  	    							    	    	    		 //Refresh Page
				  	  	  	  	    							    	    	            driver.navigate().refresh();
				  	  	  	  	    							    	    	            Thread.sleep(3000);   
				  	  	  	  	    							    	    	            
				  	  	  	  	    							    	    	            logger.info("Case 12 implemented - email field is blank");
				  	  	  	  	    							    	          
				  	  	  	  	    							    //CASE 13 - Email and Password are entered wrong     	            
				  	  	  	  	    						                              
				  	  	  	  	    							    	    	          driver.findElement(By.name("email")).sendKeys("neha@datability");  
				  	  	  	  	    							    	    	          driver.findElement(By.name("password")).sendKeys("neha");
				  	  	  	  	    							    	  	    	      driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).click();
				  	  	  	  	    							    	  	    	    Thread.sleep(2000); 
				  	  	  	  	    							    	  	    	      String actualMsgb = driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).getText();
				  	  	  	  	    							    	  	    	      System.out.println("Email and Password are wrong");
				  	  	  	  	    							    	  	    	      String errorMsgb= "Invalid username or password";

				  	  	  	  	    							    	  	    	    	 if(actualMsgb.equals(errorMsgb)) {
				  	  	  	  	    							    	  	    	    	  System.out.println("Test Case Passed");
				  	  	  	  	    							    	  	    	    	    		    }
				  	  	  	  	    							    	  	    	    	    		else
				  	  	  	  	    							    	  	    	    	    		{
				  	  	  	  	    							    	  	    	    	    		        System.out.println("Test Case Failed");
				  	  	  	  	    							    	  	    	    	    		    }
				  	  	  	  	    							    	  	    	    	  
				  	  	  	  	    							    	  	    	    	    		Thread.sleep(3000);
				  	  	  	  	    							    	  	    	    	    		
				  	  	  	  	    							    	  	    	    	    		 //Refresh Page
				  	  	  	  	    							    	  	    	    	            driver.navigate().refresh();
				  	  	  	  	    							    	  	    	    	            Thread.sleep(3000); 
				  	  	  	  	    							    	  	    	    	            
				  	  	  	  	    							    	  	    	    	          logger.info("Case 13 implemented - email and password entered are wrong");
				  	  	  	  	    							    	  	    	    	            
				  	  	  	  	    							    	  	 // CASE 14 - Email is wrong and Password is correct   	 
				  	  	  	  	    							    	  	    	   
				  	  	  	  	    							    	  	   driver.findElement(By.name("email")).sendKeys("neha@");  
				  	  	  	  	    							    		 driver.findElement(By.name("password")).sendKeys("neha1992");
				  	  	  	  	    							    		  driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).click();
				  	  	  	  	    							    		  Thread.sleep(2000); 
				  	  	  	  	    							    	      String actualMsg111111 = driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).getText();
				  	  	  	  	    							    		  System.out.println("Email is wrong");
				  	  	  	  	    							    		  String errorMsg111111= "Invalid username or password";
				  	  	  	  	    							    		    	  	    	    	 if(actualMsg111111.equals(errorMsg111111)) {
				  	  	  	  	    							    		    	  	    	    	  System.out.println("Test Case Passed");
				  	  	  	  	    							    		    	  	    	    	    		    }
				  	  	  	  	    							    		    	  	    	    	    		else
				  	  	  	  	    							    		    	  	    	    	    		{
				  	  	  	  	    							    		    	  	    	    	    		        System.out.println("Test Case Failed");
				  	  	  	  	    							    		    	  	    	    	    		    }
				  	  	  	  	    							    		    	  	    	    	  
				  	  	  	  	    							    		    	  	    	    	    		Thread.sleep(3000);
				  	  	  	  	    							    		    	  	    	    	    		 //Refresh Page
				  	  	  	  	    							    		    	  	    	    	            driver.navigate().refresh();
				  	  	  	  	    							    		    	  	    	    	            Thread.sleep(3000);    	    	            
				  	  	  	  	    								
				  	  	  	  	    							    		    	  	    	    	          logger.info("Case 14 implemented - email entered is wrong");		    	  	    	    	            
				  	  	  	  	    							    		    	  	    	    	            
				  	  	  	  	    							              //CASE 15 - Email is correct and Password is wrong  	
				  	  	  	  	    							    		    	  	    	    	          
				  	  	  	  	    							    		    	  	    	    	          driver.findElement(By.name("email")).sendKeys("neha@datability.co");  
				  	  	  	  	    							    		    	  	    		    		 driver.findElement(By.name("password")).sendKeys("neha");
				  	  	  	  	    							    		    	  	    		    		  driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).click();
				  	  	  	  	    							    		    	  	    		    		  Thread.sleep(2000); 
				  	  	  	  	    							    		    	  	    		    	      String actualMsg1111111 = driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).getText();
				  	  	  	  	    							    		    	  	    		    		  System.out.println("Password is wrong");
				  	  	  	  	    							    		    	  	    		    		  String errorMsg1111111= "Invalid username or password";
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	 if(actualMsg1111111.equals(errorMsg1111111)) {
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	  System.out.println("Test Case Passed");
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	    		    }
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	    		else
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	    		{
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	    		        System.out.println("Test Case Failed");
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	    		    }
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	  
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	    		Thread.sleep(3000);
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	    		 //Refresh Page
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	            driver.navigate().refresh();
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	            Thread.sleep(3000);
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	            
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	        logger.info("Case 15 implemented - password entered is wrong");
				  	  	  	  	    							    		    	  	    		    		    	  	    	    	            

				  	  	  	  	    						              
				  	  	  	  	    						              
				  	  	  	  	    						              //CASE 16 - Login with new password
				  	  	  	  	    						              
				  	  	  	  	    								driver.findElement(By.name("email")).sendKeys("dummyizizooto@gmail.com");
				  	  	  	  	    								driver.findElement(By.name("password")).sendKeys("123456");
				  	  	  	  	    								driver.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).click();
				  	  	  	  	    					            System.out.println("Logged In Successfully");
				  	  	  	  	    						        
				  	  	  	  	    					    //Change focus to new tab
						  	    	    						    ArrayList<String> newTab1 = new ArrayList<String>(driver.getWindowHandles());
						  	    	    						    newTab1.remove(oldTab);
						  	    	    						    driver.switchTo().window(newTab1.get(0));
						  	    	    						    assertclickhere();
						  	    	    						    
				  	  	  	  	    						         Thread.sleep(5000);	
				  	  	  	  	    						         
				  	  	  	  	    						         //Refresh Page
				  	  	  	  	    						         driver.navigate().refresh();
				  	  	  	  	    						         
				  	  	  	  	    						         logger.info("Case 16 - implemented - LoggedIn Successfully");
				  	  	  	  	    						         
				  	  	  	  	    						//Add Website Testcases (Negative)
				  	  	  	  	    							
				  	  	  	  	    					     //Case 17 - Leave website name and url both are blank
				  	  	  	  	    						
				  	  	  	  	    					     Thread.sleep(10000);
				  	  	  	  	    					     WebElement myoption = driver.findElement(By.xpath("/html//span[@id='selected']"));
				  	  	  	  	    					     myoption.click();
				  	  	  	  	    					     Thread.sleep(5000);
				  	  	  	  	    					     driver.findElement(By.xpath("//header[@id='mainheader']/div/div[2]/div/div/div[@class='add-new-website-cta']/a[@href='javascript:void(0)']/i[@class='fa fa-plus mr-10']")).click();
				  	  	  	  	    					     Thread.sleep(2000);
				  	  	  	  	    					       WebElement button1 = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    							button1.click();
				  	  	  	  	    						    String actualMsgc= driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    						    System.out.println("Website Title and Website name are blank");
				  	  	  	  	    						    		String errorMsgc= "Invalid website name or url";

				  	  	  	  	    						    		if(actualMsgc.equals(errorMsgc)) {
				  	  	  	  	    						    		        System.out.println("Test Case Passed");
				  	  	  	  	    						    		    }
				  	  	  	  	    						    		else
				  	  	  	  	    						    		{
				  	  	  	  	    						    		        System.out.println("Test Case Failed");
				  	  	  	  	    						    		    }
				  	  	  	  	    						    		logger.info("Case 17 : Implemented Successfully - when both website title and website url are blank");
				  	  	  	  	    						             
				  	  	  	  	    						    		
				  	  	  	  	    						    		 //Case 18 - Leave website title blank
				  	  	  	  	    						    		
				  	  	  	  	    						    		Thread.sleep(5000);
				  	  	  	  	    						    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("dummyizselenium19.com");
				  	  	  	  	    						   	     Thread.sleep(2000);
				  	  	  	  	    						   	       WebElement button11 = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    						   			button11.click();
				  	  	  	  	    						   		    String actualMsgd = driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    						   		    System.out.println("Website Title blank");
				  	  	  	  	    						   		    		String errorMsgd= "Blank website name";

				  	  	  	  	    						   		    		if(actualMsgd.equals(errorMsgd)) {
				  	  	  	  	    						   		    		        System.out.println("Test Case Passed");
				  	  	  	  	    						   		    		    }
				  	  	  	  	    						   		    		else
				  	  	  	  	    						   		    		{
				  	  	  	  	    						   		    		        System.out.println("Test Case Failed");
				  	  	  	  	    						   		    		    }

				  	  	  	  	    						   		    		//clear fields
				  	  	  	  	    						   		    		Thread.sleep(3000);
				  	  	  	  	    						   		    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).clear();
				  	  	  	  	    						   		    		Thread.sleep(3000);
				  	  	  	  	    						   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    						   		    		
				  	  	  	  	    						   		    		logger.info("Case 18 : Implemented Successfully - when website name is blank");
				  	  	  	  	    						   		    		
				  	  	  	  	    						   		    	//Case 19 - Leave Website Url Blank
				  	  	  	  	    						   		    		
				  	  	  	  	    						   		    		Thread.sleep(5000);
				  	  	  	  	    								    		driver.findElement(By.xpath("/html//input[@id='addSiteTitle']")).sendKeys("Test Website");
				  	  	  	  	    								   	     Thread.sleep(2000);
				  	  	  	  	    								   	       WebElement button111 = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    								   			button111.click();
				  	  	  	  	    								   		    String actualMsge = driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    								   		    System.out.println("Website Url blank");
				  	  	  	  	    								   		    		String errorMsge= "Blank website url";

				  	  	  	  	    								   		    		if(actualMsge.equals(errorMsge)) {
				  	  	  	  	    								   		    		        System.out.println("Test Case Passed");
				  	  	  	  	    								   		    		    }
				  	  	  	  	    								   		    		else
				  	  	  	  	    								   		    		{
				  	  	  	  	    								   		    		        System.out.println("Test Case Failed");
				  	  	  	  	    								   		    		    }

				  	  	  	  	    								   		    		//clear fields
				  	  	  	  	    								   		    		Thread.sleep(3000);
				  	  	  	  	    								   		    		driver.findElement(By.xpath("/html//input[@id='addSiteTitle']")).clear();
				  	  	  	  	    								   		    		
				  	  	  	  	    								   		    		logger.info("Case 19 : Implemented Successfully - when website url is blank");

				  	  	  	  	    								   		    	//Case 20 - Enter Invalid url(without .domain)
				  	  	  	  	    								   		    		
				  	  	  	  	    								   		    		Thread.sleep(5000);
				  	  	  	  	    								   		    		driver.findElement(By.xpath("/html//input[@id='addSiteTitle']")).sendKeys("Test Website");
				  	  	  	  	    											   	     Thread.sleep(2000);
				  	  	  	  	    										    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("dummyizselenium");
				  	  	  	  	    										   	     Thread.sleep(2000);
				  	  	  	  	    										   	       WebElement button1111 = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    										   			button1111.click();
				  	  	  	  	    										   		    String actualMsgf = driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    										   		    System.out.println("Invalid Website Url");
				  	  	  	  	    										   		    		String errorMsgf= "Website url is invalid";

				  	  	  	  	    										   		    		if(actualMsgf.equals(errorMsgf)) {
				  	  	  	  	    										   		    		        System.out.println("Test Case Passed");
				  	  	  	  	    										   		    		    }
				  	  	  	  	    										   		    		else
				  	  	  	  	    										   		    		{
				  	  	  	  	    										   		    		        System.out.println("Test Case Failed");
				  	  	  	  	    										   		    		    }

				  	  	  	  	    										   		    		//clear fields
				  	  	  	  	    										   		    		Thread.sleep(3000);
				  	  	  	  	    										   		    		driver.findElement(By.xpath("/html//input[@id='addSiteTitle']")).clear();
				  	  	  	  	    										   		    		Thread.sleep(3000);
				  	  	  	  	    										   		    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).clear();
				  	  	  	  	    										   		    		Thread.sleep(3000);
				  	  	  	  	    										   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    										   		    		
				  	  	  	  	    										   		    		logger.info("Case 20 : Implemented Successfully - invalid website url .domain is missing");

				  	  	  	  	    										   		    	//Case 21 - Enter Invalid url (with spaces)
				  	  	  	  	    										   		    		
				  	  	  	  	    										   		    		Thread.sleep(5000);
				  	  	  	  	    										   		    		driver.findElement(By.xpath("/html//input[@id='addSiteTitle']")).sendKeys("Test Website");
				  	  	  	  	    													   	     Thread.sleep(2000);
				  	  	  	  	    												    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("dummyizselenium 123.com");
				  	  	  	  	    												   	     Thread.sleep(2000);
				  	  	  	  	    												   	       WebElement buttonco = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    												   			buttonco.click();
				  	  	  	  	    												   		    String actualMsgg = driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    												   		    System.out.println("Invalid Website Url");
				  	  	  	  	    												   		    		String errorMsgg= "Website url is invalid";

				  	  	  	  	    												   		    		if(actualMsgg.equals(errorMsgg)) {
				  	  	  	  	    												   		    		        System.out.println("Test Case Passed");
				  	  	  	  	    												   		    		    }
				  	  	  	  	    												   		    		else
				  	  	  	  	    												   		    		{
				  	  	  	  	    												   		    		        System.out.println("Test Case Failed");
				  	  	  	  	    												   		    		    }

				  	  	  	  	    												   		    		//clear fields
				  	  	  	  	    												   		    		Thread.sleep(3000);
				  	  	  	  	    												   		    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).clear();
				  	  	  	  	    												   		    		Thread.sleep(3000);
				  	  	  	  	    												   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    												   		    		
				  	  	  	  	    												   		    		logger.info("Case 21 : Implemented Successfully - invalid website url with spaces");

				  	  	  	  	    												   		    	//Case 22 - Enter Invalid url (different language)
				  	  	  	  	    												   		    		
				  	  	  	  	    												   		    		Thread.sleep(5000);
				  	  	  	  	    														    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("页面的排版时.页面");
				  	  	  	  	    														   	     Thread.sleep(2000);
				  	  	  	  	    														   	       WebElement buttonop = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    														   			buttonop.click();
				  	  	  	  	    														   		    String actualMsgh = driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    														   		    System.out.println("Invalid Website Url ie. in different language");
				  	  	  	  	    														   		    		String errorMsgh= "Website url is invalid";

				  	  	  	  	    														   		    		if(actualMsgh.equals(errorMsgh)) {
				  	  	  	  	    														   		    		        System.out.println("Test Case Passed");
				  	  	  	  	    														   		    		    }
				  	  	  	  	    														   		    		else
				  	  	  	  	    														   		    		{
				  	  	  	  	    														   		    		        System.out.println("Test Case Failed");
				  	  	  	  	    														   		    		    }

				  	  	  	  	    														   		    		//clear fields
				  	  	  	  	    														   		    		Thread.sleep(3000);
				  	  	  	  	    														   		    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).clear();
				  	  	  	  	    														   		    		Thread.sleep(3000);
				  	  	  	  	    														   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    														   		    		
				  	  	  	  	    														   		    		logger.info("Case 22 : Implemented Successfully - invalid website url in different language");

				  	  	  	  	    														   		    	//Case 23 - Enter Invalid url (special characters)
				  	  	  	  	    														   		    		
				  	  	  	  	    														   		    		Thread.sleep(5000);
				  	  	  	  	    																    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("test(2$%&*&@@;@@;3.com/test#dkl");
				  	  	  	  	    																   	     Thread.sleep(2000);
				  	  	  	  	    																   	       WebElement buttonoo = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    																   			buttonoo.click();
				  	  	  	  	    																   		    String actualMsgi = driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    																   		    System.out.println("Invalid Website Url");
				  	  	  	  	    																   		    		String errorMsgi= "Website url is invalid";

				  	  	  	  	    																   		    		if(actualMsgi.equals(errorMsgi)) {
				  	  	  	  	    																   		    		        System.out.println("Test Case Passed");
				  	  	  	  	    																   		    		    }
				  	  	  	  	    																   		    		else
				  	  	  	  	    																   		    		{
				  	  	  	  	    																   		    		        System.out.println("Test Case Failed");
				  	  	  	  	    																   		    		    }

				  	  	  	  	    																   		    		//clear fields
				  	  	  	  	    																   		    		Thread.sleep(3000);
				  	  	  	  	    																   		    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).clear();
				  	  	  	  	    																   		    		Thread.sleep(3000);
				  	  	  	  	    																   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    																   		    		
				  	  	  	  	    																   		    		logger.info("Case 23 : Implemented Successfully - invalid website url with special characters");

				  	  	  	  	    																   		    	//Case 24 - Remove Subdomain
				  	  	  	  	    																   		    		
				  	  	  	  	    																   		    		Thread.sleep(5000);
				  	  	  	  	    																		    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("dummyizselenium22.com");
				  	  	  	  	    																		    		Thread.sleep(3000);
				  	  	  	  	    																   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    																   		    	 Thread.sleep(2000);
				  	  	  	  	    																		   	        WebElement buttona = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    																		   			buttona.click();
				  	  	  	  	    																		   		    String actualMsga1111 = driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    																		   		    System.out.println("Subdomain is empty");
				  	  	  	  	    																		   		    		String errorMsga1111= "Subdomain is invalid";

				  	  	  	  	    																		   		    		if(actualMsga1111.equals(errorMsga1111)) {
				  	  	  	  	    																		   		    		        System.out.println("Test Case Passed");
				  	  	  	  	    																		   		    		    }
				  	  	  	  	    																		   		    		else
				  	  	  	  	    																		   		    		{
				  	  	  	  	    																		   		    		        System.out.println("Test Case Failed");
				  	  	  	  	    																		   		    		    }

				  	  	  	  	    																		   		    		//clear fields
				  	  	  	  	    																		   		    		Thread.sleep(3000);
				  	  	  	  	    																		   		    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).clear();
				  	  	  	  	    																		   		    		
				  	  	  	  	    																		   		    		logger.info("Case 24 : Implemented Successfully - subdomain is blank");
				  	  	  	  	    																		   		    
				  	  	  	  	    																		   		    	//Case 25 - Enter Invalid Subdomain
				  	  	  	  	    																		   		    		
				  	  	  	  	    																		   		    		Thread.sleep(5000);
				  	  	  	  	    																				    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("dummyizselenium22.com");
				  	  	  	  	    																				    		Thread.sleep(3000);
				  	  	  	  	    																		   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    																		   		    		Thread.sleep(2000);
				  	  	  	  	    																		   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).sendKeys("dummmy@kk");
				  	  	  	  	    																		   		    	 Thread.sleep(2000);
				  	  	  	  	    																				   	        WebElement buttona1 = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    																				   			buttona1.click();
				  	  	  	  	    																				   		    String actualMsga11111 = driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    																				   		    System.out.println("Subdomain is invalid");
				  	  	  	  	    																				   		    		String errorMsga11111= "Subdomain is invalid";

				  	  	  	  	    																				   		    		if(actualMsga11111.equals(errorMsga11111)) {
				  	  	  	  	    																				   		    		        System.out.println("Test Case Passed");
				  	  	  	  	    																				   		    		    }
				  	  	  	  	    																				   		    		else
				  	  	  	  	    																				   		    		{
				  	  	  	  	    																				   		    		        System.out.println("Test Case Failed");
				  	  	  	  	    																				   		    		    }

				  	  	  	  	    																				   		    		//clear fields
				  	  	  	  	    																				   		    		Thread.sleep(3000);
				  	  	  	  	    																				   		    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).clear();
				  	  	  	  	    																				   		    		Thread.sleep(3000);
				  	  	  	  	    																				   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    																				   		    		
				  	  	  	  	    																				   		    		logger.info("Case 25 : Implemented Successfully - invalid subdomain");

				  	  	  	  	    																				   		    	//Case 26 - Enter Invalid Subdomain(different language)
				  	  	  	  	    																				   		    		
				  	  	  	  	    																				   		    		Thread.sleep(5000);
				  	  	  	  	    																						    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("dummyizselenium22.com");
				  	  	  	  	    																						    		Thread.sleep(3000);
				  	  	  	  	    																				   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    																				   		    		Thread.sleep(2000);
				  	  	  	  	    																				   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).sendKeys("页面的排版");
				  	  	  	  	    																				   		    	 Thread.sleep(2000);
				  	  	  	  	    																						   	        WebElement buttona11 = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    																						   			buttona11.click();
				  	  	  	  	    																						   		    String actualMsga111111 = driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    																						   		    System.out.println("Subdomain is invalid");
				  	  	  	  	    																						   		    		String errorMsga111111= "Subdomain is invalid";

				  	  	  	  	    																						   		    		if(actualMsga111111.equals(errorMsga111111)) {
				  	  	  	  	    																						   		    		        System.out.println("Test Case Passed");
				  	  	  	  	    																						   		    		    }
				  	  	  	  	    																						   		    		else
				  	  	  	  	    																						   		    		{
				  	  	  	  	    																						   		    		        System.out.println("Test Case Failed");
				  	  	  	  	    																						   		    		    }

				  	  	  	  	    																						   		    		//clear fields
				  	  	  	  	    																						   		    		Thread.sleep(3000);
				  	  	  	  	    																						   		    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).clear();
				  	  	  	  	    																						   		    		Thread.sleep(3000);
				  	  	  	  	    																						   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    																						   		    		
				  	  	  	  	    																						   		    		logger.info("Case 26 : Implemented Successfully - invalid subdomain in different language");

				  	  	  	  	    																						   		    	//Case 27 - Enter Invalid Subdomain(special characters)
				  	  	  	  	    																						   		    		
				  	  	  	  	    																						   		    		Thread.sleep(5000);
				  	  	  	  	    																								    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("dummyizselenium22.com");
				  	  	  	  	    																								    		Thread.sleep(3000);
				  	  	  	  	    																						   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    																						   		    		Thread.sleep(2000);
				  	  	  	  	    																						   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).sendKeys("test(2$%&*&@@;@@;3.");
				  	  	  	  	    																						   		    	 Thread.sleep(2000);
				  	  	  	  	    																								   	        WebElement buttona111 = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    																								   			buttona111.click();
				  	  	  	  	    																								   		    String actualMsgaa = driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    																								   		    System.out.println("Subdomain is invalid");
				  	  	  	  	    																								   		    		String errorMsgaa= "Subdomain is invalid";

				  	  	  	  	    																								   		    		if(actualMsgaa.equals(errorMsgaa)) {
				  	  	  	  	    																								   		    		        System.out.println("Test Case Passed");
				  	  	  	  	    																								   		    		    }
				  	  	  	  	    																								   		    		else
				  	  	  	  	    																								   		    		{
				  	  	  	  	    																								   		    		        System.out.println("Test Case Failed");
				  	  	  	  	    																								   		    		    }

				  	  	  	  	    																								   		    		//clear fields
				  	  	  	  	    																								   		    		Thread.sleep(3000);
				  	  	  	  	    																								   		    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).clear();
				  	  	  	  	    																								   		    		Thread.sleep(3000);
				  	  	  	  	    																								   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    																								   		    		
				  	  	  	  	    																								   		    		logger.info("Case 27 : Implemented Successfully - subdomain with special characters");

				  	  	  	  	    																								   		    	//Case 28 - Already existing Subdomain
				  	  	  	  	    																								   		    		
				  	  	  	  	    																								   		    		Thread.sleep(5000);
				  	  	  	  	    																										    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("dummyizselenium25.com");
				  	  	  	  	    																										   	     Thread.sleep(2000);
				  	  	  	  	    																										   	  driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    																							   		    		Thread.sleep(2000);
				  	  	  	  	    																							   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).sendKeys("dummyiz");
				  	  	  	  	    																							   		    	 Thread.sleep(2000);
				  	  	  	  	    																										   	       WebElement buttonb = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    																										   			buttonb.click();
				  	  	  	  	    																										   		    String actualMsgk = driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    																										   		    System.out.println("Subdomain Already Exists");
				  	  	  	  	    																										   		    		String errorMsgk= "Subdomain already exists";

				  	  	  	  	    																										   		    		if(actualMsgk.equals(errorMsgk)) {
				  	  	  	  	    																										   		    		        System.out.println("Test Case Passed");
				  	  	  	  	    																										   		    		    }
				  	  	  	  	    																										   		    		else
				  	  	  	  	    																										   		    		{
				  	  	  	  	    																										   		    		        System.out.println("Test Case Failed");
				  	  	  	  	    																										   		    		    }

				  	  	  	  	    																										   		    		//clear fields
				  	  	  	  	    																										   		    		Thread.sleep(3000);
				  	  	  	  	    																										   		    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).clear();
				  	  	  	  	    																										   		    		Thread.sleep(3000);
				  	  	  	  	    																										   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();
				  	  	  	  	    																										   		    		
				  	  	  	  	    																										   		    		logger.info("Case 28 : Implemented Successfully - subdomain already exits");
				  	  	  	  	    																										   		    		
				  	  	  	  	    																										   		    	//Case 29 - Already existing website
				  	  	  	  	    																										   		    		
				  	  	  	  	    																										   		    		Thread.sleep(5000);
				  	  	  	  	    																												    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("dummyizselenium.com");
				  	  	  	  	    																												   	     Thread.sleep(2000);
				  	  	  	  	    																												   	       WebElement buttonb1 = driver.findElement(By.xpath("/html//button[@id='actionButton']"));
				  	  	  	  	    																												   			buttonb1.click();
				  	  	  	  	    																												   		    String actualMsgb1 = driver.findElement(By.xpath("/html//button[@id='actionButton']")).getText();
				  	  	  	  	    																												   		    System.out.println("Website url Already Exists");
				  	  	  	  	    																												   		    		String errorMsgb1= "website url already exists";

				  	  	  	  	    																												   		    		if(actualMsgb1.equals(errorMsgb1)) {
				  	  	  	  	    																												   		    		        System.out.println("Test Case Passed");
				  	  	  	  	    																												   		    		    }
				  	  	  	  	    																												   		    		else
				  	  	  	  	    																												   		    		{
				  	  	  	  	    																												   		    		        System.out.println("Test Case Failed");
				  	  	  	  	    																												   		    		    }

				  	  	  	  	    																												   		    		//clear fields
				  	  	  	  	    																												   		    		Thread.sleep(3000);
				  	  	  	  	    																												   		    		driver.findElement(By.xpath("/html//input[@id='addSiteTitle']")).clear();
				  	  	  	  	    																												   		    		Thread.sleep(3000);
				  	  	  	  	    																												   		    		driver.findElement(By.xpath("/html//input[@id='siteUrl']")).clear();
				  	  	  	  	    																												   		    		Thread.sleep(3000);
				  	  	  	  	    																												   		    		driver.findElement(By.xpath("/html//input[@id='subdomain_name']")).clear();

				  	  	  	  	    																												   		    		logger.info("Case 29 : Implemented Successfully - Domain already exists");
				  	  	  	  	    																												   		    		
				  	  	  	  	    																												   		    		Thread.sleep(3000);
				  	  	  	  	    																												   		    		
				  	  	  	  	    																												   		    		//Close Add Website Modal
				  	  	  	  	    																												   		    		
				  	  	  	  	    																												   		    	 driver.findElement(By.xpath("//div[@id='onboarding']//div[@role='document']//div[@class='modal-header pb-0 pt-30']/button[@type='button']/span[.='×']")).click();
				  	  	  	  	    																												   		    		
				  	  	  	  	    																												   		    	//Case 30 - Add HTTP Website 
				  	  	  	  	    																												   		    	 
				  	  	  	  	    																												   		        Thread.sleep(3000);
				  	  	  	  	    																												   			     WebElement myoption1 = driver.findElement(By.xpath("/html//span[@id='selected']"));
				  	  	  	  	    																												   			     myoption1.click();
				  	  	  	  	    																												   			     Thread.sleep(5000);
				  	  	  	  	    																												   			     driver.findElement(By.xpath("//header[@id='mainheader']/div/div[2]/div/div/div[@class='add-new-website-cta']/a[@href='javascript:void(0)']/i[@class='fa fa-plus mr-10']")).click();
				  	  	  	  	    																												   			     Thread.sleep(2000);
				  	  	  	  	    																												   			     driver.findElement(By.xpath("/html//input[@id='addSiteTitle']")).sendKeys("Test Website 1");
				  	  	  	  	    																												   			     Thread.sleep(2000);
				  	  	  	  	    																												   			     driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("dummyizseleniumgo728.com");
				  	  	  	  	    																												   			     Thread.sleep(2000);
				  	  	  	  	    																												   			     driver.findElement(By.xpath("/html//button[@id='actionButton']")).click();
				  	  	  	  	    																												   			     Thread.sleep(10000);
				  	  	  	  	    																												   			     driver.findElement(By.xpath("/html//input[@id='emailsToSend']")).sendKeys("neha@datability.co");
				  	  	  	  	    																												   			     Thread.sleep(2000);
				  	  	  	  	    																												   			     driver.findElement(By.xpath("//div[@id='onboarding']/div[@class='vertical-alignment-helper']/div[@role='document']/div[@class='modal-content']/div[2]/div[2]/div[@class='fs-12']/div[2]/div[2]/span[2]/button[@type='button']")).click();
				  	  	  	  	    																												   			     Thread.sleep(5000);
				  	  	  	  	    																												   			     driver.findElement(By.xpath("/html//button[@id='actionButton']")).click();
				  	  	  	  	    																												   			  Thread.sleep(2000);
				  	  	  	  	    																												   			    
				  	  	  	  	    																												   			  logger.info("Case 30 : Implemented Successfully - HTTP Website Added Successfully");
				  	  	  	  	    																												   			     
				  	  	  	  	    																												   			  //Case 31 - Add HTTPS Website 
				  	  	  	  	    																												   			  
				  	  	  	  	    																												   			WebElement myoption11 = driver.findElement(By.xpath("/html//span[@id='selected']"));
				  	  	  	  	    																														     myoption11.click();
				  	  	  	  	    																														     Thread.sleep(5000);
				  	  	  	  	    																														   driver.findElement(By.xpath("//header[@id='mainheader']/div/div[2]/div/div/div[@class='add-new-website-cta']/a[@href='javascript:void(0)']/i[@class='fa fa-plus mr-10']")).click();
				  	  	  	  	    																													     Thread.sleep(3000);
				  	  	  	  	    																													     driver.findElement(By.xpath("/html//span[@id='highlightProtocol']")).click();
				  	  	  	  	    																													     Thread.sleep(3000);
				  	  	  	  	    																													     driver.findElement(By.xpath("//div[@id='onboarding']/div[@class='vertical-alignment-helper']/div[@role='document']/div/div[2]/div[1]//div[@class='input-group iz_inp_grp']/span/div/div/div[2]/ul/li[2]/a[@href='javascript:void(0)']")).click();
				  	  	  	  	    																													     Thread.sleep(2000);
				  	  	  	  	    																													     driver.findElement(By.xpath("/html//input[@id='addSiteTitle']")).sendKeys("Test Website 2");
				  	  	  	  	    																													     Thread.sleep(2000);
				  	  	  	  	    																													     driver.findElement(By.xpath("/html//input[@id='siteUrl']")).sendKeys("dummyizseleniumgo23U.com");
				  	  	  	  	    																													     Thread.sleep(2000);
				  	  	  	  	    																													     driver.findElement(By.xpath("/html//button[@id='actionButton']")).click();
				  	  	  	  	    																													     Thread.sleep(10000);
				  	  	  	  	    																													     driver.findElement(By.xpath("/html//input[@id='emailsToSend']")).sendKeys("neha@datability.co");
				  	  	  	  	    																													     Thread.sleep(2000);
				  	  	  	  	    																													     driver.findElement(By.xpath("//div[@id='onboarding']/div[@class='vertical-alignment-helper']/div[@role='document']/div[@class='modal-content']/div[2]/div[2]/div[@class='fs-12']/div[2]/div[2]/span[2]/button[@type='button']")).click();
				  	  	  	  	    																													     Thread.sleep(5000);
				  	  	  	  	    																													     driver.findElement(By.xpath("/html//button[@id='actionButton']")).click();
				  	  	  	  	    																													     
				  	  	  	  	    																													     logger.info("Case 31 : Implemented Successfully - HTTPS Website Added Successfully");
				  	  	  	  	    																													     
				  	  	  	  	    																													     Thread.sleep(6000);
				  	  	  	  	    																													     
				  	  	  	  	    																													     //Push Notification
				  	  	  	  	    																													     
				  	  	  	  	    																												//Click Send Notification
				  	  	  	  	    																													
				  	  	  	  	    																													driver.findElement(By.xpath("//li[@id='create-campaign']//span[@class='sidebar-title']")).click();
				  	  	  	  	    																													logger.info("Send Notification Page Opened Successfully");
				  	  	  	  	    																													
				  	  	  	  	    																													Thread.sleep(2000);	
				  	  	  	  	    																											        driver.findElement(By.name("campname")).sendKeys("THIS IS A TEST NOTIFICATION");
				  	  	  	  	    																											        Thread.sleep(2000);	
				  	  	  	  	    																													driver.findElement(By.xpath("//form[@id='camp_form']/div[1]/div[@class='col-md-12']//div[@class='widget-body']/div[2]//input[@class='emoji-wysiwyg-editor form-control input_wid_camp iz_color_input no-line-break titleDiv']")).sendKeys("THIS IS TEST TITLE");
				  	  	  	  	    																													Thread.sleep(2000);	
				  	  	  	  	    																													driver.findElement(By.xpath("//form[@id='camp_form']/div[1]/div[@class='col-md-12']//div[@class='form-group mb-0']//input[@placeholder='Notification Message']")).sendKeys("THIS IS TEST MESSAGE");
				  	  	  	  	    																													Thread.sleep(2000);	
				  	  	  	  	    																													driver.findElement(By.name("landurl")).sendKeys("www.izooto.com");
				  	  	  	  	    																													Thread.sleep(2000);	
				  	  	  	  	    																													logger.info("Campaign Name, Tilte, Message and URL Entered");
				  	  	  	  	    																													
				  	  	  	  	    																													//Upload Icon
				  	  	  	  	    																													driver.findElement(By.xpath("//form[@id='camp_form']/div[1]/div[@class='col-md-12']/div[@class='col-md-7 mobile-padng']//div[@class='noti-icon-container']/div[2]/div//center[.='Upload Icon']")).click();
				  	  	  	  	    																													Thread.sleep(5000);
				  	  	  	  	    																													driver.findElement(By.xpath("//div[@id='iconLibraryModal']/div[@class='modal-dialog']//div[@class='modal-header']/a[@href='javascript:void(0)']")).click();
				  	  	  	  	    																													Thread.sleep(5000);
				  	  	  	  	    																													Runtime.getRuntime().exec("C:\\Users\\hp\\Desktop\\AutoIT\\ImageUpload.exe"); 
				  	  	  	  	    																													Thread.sleep(2000);	
				  	  	  	  	    																													driver.findElement(By.xpath("/html//div[@id='img-container']//a[.='OK']")).click();
				  	  	  	  	    																													Thread.sleep(5000);
				  	  	  	  	    																													driver.findElement(By.xpath("/html//img[@id='last_image']")).click();
				  	  	  	  	    																													Thread.sleep(5000);
				  	  	  	  	    																													driver.findElement(By.xpath("//div[@id='iconLibraryModal']//div[@class='modal-footer']/a[@href='javascript:void(0)']")).click();
				  	  	  	  	    																													logger.info("Icon Uploaded Successfully");
				  	  	  	  	    																													
				  	  	  	  	    																													Thread.sleep(3000);
				  	  	  	  	    																													
				  	  	  	  	    																													//Scroll to Middle of the page
				  	  	  	  	    																													JavascriptExecutor js11 = (JavascriptExecutor) driver;
				  	  	  	  	    																													js11.executeScript("window.scrollBy(0,200)");
				  	  	  	  	    																													
				  	  	  	  	    																													//Banner Image Upload
				  	  	  	  	    																													driver.findElement(By.xpath("//form[@id='camp_form']/div[2]/div[@class='col-md-12']/div[@class='col-md-7 mobile-padng']//span[@class='switch-label']")).click();
				  	  	  	  	    																													Thread.sleep(3000);
				  	  	  	  	    																													driver.findElement(By.xpath("//div[@id='showNotiImage']//div[@class='col-md-12 pl-0 pr-0']//div[@class='uploadImageLib']/div//center[.='Upload Large Image']")).click();
				  	  	  	  	    																													Thread.sleep(3000);
				  	  	  	  	    																													Runtime.getRuntime().exec("C:\\Users\\hp\\Desktop\\AutoIT\\BannerUpload.exe"); 
				  	  	  	  	    																													Thread.sleep(5000);
				  	  	  	  	    																													driver.findElement(By.xpath("/html//div[@id='img-container']//a[.='OK']")).click();
				  	  	  	  	    																													logger.info("Banner Uploaded Successfully");
				  	  	  	  	    																													
				  	  	  	  	    																													Thread.sleep(5000);
				  	  	  	  	    																													
				  	  	  	  	    																													//Add Buttons
				  	  	  	  	    																													driver.findElement(By.xpath("//form[@id='camp_form']/div[3]/div[@class='col-md-12']/div[@class='col-md-7 mobile-padng']//span[@class='switch-label']")).click();
				  	  	  	  	    																													Thread.sleep(3000);
				  	  	  	  	    																													driver.findElement(By.xpath("//form[@id='camp_form']/div[3]/div[@class='col-md-12']/div[@class='col-md-7 mobile-padng']/div/div[2]//input[@name='button1name']")).sendKeys("CTA 1 Added");
				  	  	  	  	    																													Thread.sleep(2000);	
				  	  	  	  	    																													driver.findElement(By.xpath("//form[@id='camp_form']/div[3]/div[@class='col-md-12']/div[@class='col-md-7 mobile-padng']/div/div[2]//input[@name='button1link']")).sendKeys("www.izooto.com");
				  	  	  	  	    																													Thread.sleep(2000);	
				  	  	  	  	    																													driver.findElement(By.xpath("/html//button[@id='addBtn2']")).click();
				  	  	  	  	    																													Thread.sleep(2000);	
				  	  	  	  	    																													driver.findElement(By.xpath("//div[@id='btn2']/div[@class='col-md-4']//input[@name='button2name']")).sendKeys("CTA 2 Added");
				  	  	  	  	    																													Thread.sleep(2000);	
				  	  	  	  	    																													driver.findElement(By.xpath("//div[@id='btn2']/div[@class='col-md-7 plr-0 pr-0']//input[@name='button2link']")).sendKeys("www.izooto.com");
				  	  	  	  	    																													logger.info("Button Added Successfully");
				  	  	  	  	    																													
				  	  	  	  	    																													Thread.sleep(2000);
				  	  	  	  	    																													
				  	  	  	  	    																													//Click Push It Now
				  	  	  	  	    																													driver.findElement(By.name("push_now")).click();
				  	  	  	  	    																												
				  	  	  	  	    																													Thread.sleep(2000);	
				  	  	  	  	    																												    driver.findElement(By.xpath("/html//input[@id='push_btn']")).click();
				  	  	  	  	    																													
				  	  	  	  	    																												    logger.info("Campaign Pushed Successfully");
				  	  	  	  	    																												    
				  	  	  	  	    																											Thread.sleep(5000);
				  	  	  	  	    																											
				  	  	  	  	    																											//Audience Builder
				  	  	  	  	    																											
				  	  	  	  	    																									//Open Audience Builder Page
				  	  	  	  	    																								       
				  	  	  	  	    																									driver.findElement(By.xpath("//li[@id='view-audience']//span[@class='sidebar-title']")).click();
				  	  	  	  	    																									Thread.sleep(2000);	
				  	  	  	  	    																									driver.findElement(By.xpath("//body/section[@class='page-container']/div[1]//button[@type='button']")).click();
				  	  	  	  	    																									Thread.sleep(2000);	
				  	  	  	  	    																									
				  	  	  	  	    																									//Case 1 - When no filters are selected, and audience is saved
				  	  	  	  	    																									
				  	  	  	  	    																									driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).click();
				  	  	  	  	    																									
				  	  	  	  	    																									String actualMsg1o = driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).getText();
				  	  	  	  	    																								      System.out.println("Atleast select one filter");
				  	  	  	  	    																								      String errorMsg1o= "No filter selected";

				  	  	  	  	    																								    	 if(actualMsg1o.equals(errorMsg1o)) {
				  	  	  	  	    																								    	  System.out.println("Test Case Passed");
				  	  	  	  	    																								    	    		    }
				  	  	  	  	    																								    	    		else
				  	  	  	  	    																								    	    		{
				  	  	  	  	    																								    	    		        System.out.println("Test Case Failed");
				  	  	  	  	    																								    	    		    }
				  	  	  	  	    																								    	  
				  	  	  	  	    																								    	    		Thread.sleep(5000);
				  	  	  	  	    																								    	          logger.info("Case 1 - implemented - No filter was selected");
				  	  	  	  	    																								   
				  	  	  	  	    																									//Case 2 - Select a segment and don't select the property and save
				  	  	  	  	    																								    	          
				  	  	  	  	    																								    	          driver.findElement(By.xpath("//body/section/div[2]/div/div[@class='panel panel-default']/div[@class='panel-body']/div[3]/div[@class='panel-heading']/h3[@class='panel-title']")).click();
				  	  	  	  	    																								    	          Thread.sleep(2000); 
				  	  	  	  	    																								    	          Select select = new Select(driver.findElement(By.xpath("//div[@id='uc1']//select")));
				  	  	  	  	    																													Thread.sleep(2000);	
				  	  	  	  	    																													select.selectByVisibleText("Device");
				  	  	  	  	    																													Thread.sleep(2000); 
				  	  	  	  	    																								    	          driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).click();
				  	  	  	  	    																								    	          String actualMsg1f = driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).getText();
				  	  	  	  	    																								    		      System.out.println("Atleast select one segment");
				  	  	  	  	    																								    		      String errorMsg1f= "No segment selected";

				  	  	  	  	    																								    		    	 if(actualMsg1f.equals(errorMsg1f)) {
				  	  	  	  	    																								    		    	  System.out.println("Test Case Passed");
				  	  	  	  	    																								    		    	    		    }
				  	  	  	  	    																								    		    	    		else
				  	  	  	  	    																								    		    	    		{
				  	  	  	  	    																								    		    	    		        System.out.println("Test Case Failed");
				  	  	  	  	    																								    		    	    		    }
				  	  	  	  	    																								    		    	  
				  	  	  	  	    																								    		    	    		Thread.sleep(5000);
				  	  	  	  	    																								    		    	          logger.info("Case 2 - implemented - No property under device was selected");
				  	  	  	  	    																								    	          
				  	  	  	  	    																								    		    	        //Case 3 -  Open events and don't select any and save  
				  	  	  	  	    																								    		    	        
				  	  	  	  	    																								    		    	         driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[@class='panel panel-default']/div[@class='panel-heading']")).click();
				  	  	  	  	    																								    		    	         Thread.sleep(2000); 
				  	  	  	  	    																								    		    	         driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).click();
				  	  	  	  	    																								    		    	         String actualMsg1q = driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).getText();
				  	  	  	  	    																								    		    		      System.out.println("Atleast select one segment");
				  	  	  	  	    																								    		    		      String errorMsg1q= "No segment selected";

				  	  	  	  	    																								    		    		    	 if(actualMsg1q.equals(errorMsg1q)) {
				  	  	  	  	    																								    		    		    	  System.out.println("Test Case Passed");
				  	  	  	  	    																								    		    		    	    		    }
				  	  	  	  	    																								    		    		    	    		else
				  	  	  	  	    																								    		    		    	    		{
				  	  	  	  	    																								    		    		    	    		        System.out.println("Test Case Failed");
				  	  	  	  	    																								    		    		    	    		    }
				  	  	  	  	    																								    		    		    	  
				  	  	  	  	    																								    		    		    	    		Thread.sleep(5000);
				  	  	  	  	    																								    		    		    	          logger.info("Case 3 - implemented - No event was selected");
				  	  	  	  	    																								    		    		    	          
				  	  	  	  	    																								    		    		    	          driver.navigate().refresh();
				  	  	  	  	    																								    		    		    	      	  
				  	  	  	  	    																								    		    		    	        //Scroll to center of the page
				  	  	  	  	    																								    										WebElement element = driver.findElement(By.xpath("//body/section//div[.='Note: Type all inputs in English']"));
				  	  	  	  	    																								    								        String scrollElementIntoMiddle = "var viewPortHeight = Math.max(document.documentElement.clientHeight, window.innerHeight || 0);"
				  	  	  	  	    																								    										                                            + "var elementTop = arguments[0].getBoundingClientRect().top;"
				  	  	  	  	    																								    										                                            + "window.scrollBy(0, elementTop-(viewPortHeight/2));";
				  	  	  	  	    																								    								         ((JavascriptExecutor) driver).executeScript(scrollElementIntoMiddle, element);
				  	  	  	  	    																								    										
				  	  	  	  	    																								    		    		    	          
				  	  	  	  	    																								    		    		    	        //Case 4 - When Audience Name is more than 32 characters
				  	  	  	  	    																								    		    		    	        
				  	  	  	  	    																								    										driver.findElement(By.xpath("//body/section/div[2]/div/div[@class='panel panel-default']/div[@class='panel-body']/div[@class='panel panel-default']/div[@class='panel-heading']/h3[@class='panel-title']")).click();
				  	  	  	  	    																								    										Thread.sleep(2000);
				  	  	  	  	    																								    										driver.findElement(By.xpath("//div[@id='showAdvancedFilter']/div[@class='panel panel-default']//button[@class='btn btn-primary btn-sm']")).click();
				  	  	  	  	    																								    										Thread.sleep(2000);	
				  	  	  	  	    																								    										driver.findElement(By.xpath("//div[@id='and_or_event_main']/div[1]/div[1]/select")).click();
				  	  	  	  	    																								    										Thread.sleep(2000);	
				  	  	  	  	    																								    										driver.findElement(By.xpath("//*[@id=\"and_or_event_main\"]/div[1]/div[1]/select/option[4]")).click();
				  	  	  	  	    																								    										Thread.sleep(2000);	
				  	  	  	  	    																								    										driver.findElement(By.xpath("//div[@id='and_or_event_main']/div[1]/a[@href='javascript:void(0)']")).click();
				  	  	  	  	    																								    										Thread.sleep(2000);	
				  	  	  	  	    																								    										Select select11 = new Select(driver.findElement(By.xpath("//div[@id='and_or_event_main']/div[1]/div[3]//span[@class='event_custom_prop']/select")));
				  	  	  	  	    																								    										Thread.sleep(2000);	
				  	  	  	  	    																								    										select11.selectByVisibleText("product_title");
				  	  	  	  	    																								    										Thread.sleep(2000);	
				  	  	  	  	    																								    										driver.findElement(By.xpath("//div[@id='event_multi_sel_string1_chosen']/ul[@class='chosen-choices']//input[@value='Search']")).click();
				  	  	  	  	    																								    										Thread.sleep(2000);	
				  	  	  	  	    																								    										driver.findElement(By.xpath("//*[@id=\"event_multi_sel_string1_chosen\"]/div/ul/li")).click();
				  	  	  	  	    																								    										Thread.sleep(2000);
				  	  	  	  	    																								    										driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).click();
				  	  	  	  	    																								    										Thread.sleep(5000);
				  	  	  	  	    																								    										driver.findElement(By.xpath("/html//input[@id='audience_name']")).sendKeys("This Audience is created with Events and Event properties to use it to send notifications");
				  	  	  	  	    																								    										Thread.sleep(2000);
				  	  	  	  	    																								    										driver.findElement(By.xpath("/html//button[@id='save_aud_btn']")).click();
				  	  	  	  	    																								    			    		    	         String actualMsg11111111 = driver.findElement(By.xpath("/html//button[@id='save_aud_btn']")).getText();
				  	  	  	  	    																								    			    		    		      System.out.println("Audience Name should be less than 64 characters");
				  	  	  	  	    																								    			    		    		      String errorMsg11111111= "Audience Name should be less than 64 characters";

				  	  	  	  	    																								    			    		    		    	 if(actualMsg11111111.equals(errorMsg11111111)) {
				  	  	  	  	    																								    			    		    		    	  System.out.println("Test Case Passed");
				  	  	  	  	    																								    			    		    		    	    		    }
				  	  	  	  	    																								    			    		    		    	    		else
				  	  	  	  	    																								    			    		    		    	    		{
				  	  	  	  	    																								    			    		    		    	    		        System.out.println("Test Case Failed");
				  	  	  	  	    																								    			    		    		    	    		    }
				  	  	  	  	    																								    			    		    		    	  
				  	  	  	  	    																								    			    		    		    	    		Thread.sleep(7000);
				  	  	  	  	    																								    			    		    		    	          logger.info("Case 4 - Audience Name should be less than 64 characters");
				  	  	  	  	    																								    			    		    		    	          driver.findElement(By.xpath("/html/body/section/div[3]/div/div/div[3]/button[2]")).click();
				  	  	  	  	    																								    			    		    		    	          Thread.sleep(2000);
				  	  	  	  	    																								    			    		    		    	          driver.navigate().refresh();
				  	  	  	  	    																								    			    		    		    	          

				  	  	  	  	    																								    			    										//Scroll to center of the page
				  	  	  	  	    																								    			    										WebElement element1 = driver.findElement(By.xpath("//body/section/div[2]/div/div[@class='panel panel-default']/div[@class='panel-body']"));
				  	  	  	  	    																								    			    								        String scrollElementIntoMiddle1 = "var viewPortHeight = Math.max(document.documentElement.clientHeight, window.innerHeight || 0);"
				  	  	  	  	    																								    			    										                                            + "var elementTop = arguments[0].getBoundingClientRect().top;"
				  	  	  	  	    																								    			    										                                            + "window.scrollBy(0, elementTop-(viewPortHeight/2));";
				  	  	  	  	    																								    			    								         ((JavascriptExecutor) driver).executeScript(scrollElementIntoMiddle1, element1);
				  	  	  	  	    																								    			    										
				  	  	  	  	    																								    			    		    		    	          
				  	  	  	  	    																								    			    		    		    	        //Case 5 - Select Device and type Desktop and Create Audience
				  	  	  	  	    																								    			    		    		    	          
				  	  	  	  	    																								    			    		    		    	          Thread.sleep(5000);
				  	  	  	  	    																								    			    		    					        driver.findElement(By.xpath("//body/section/div[2]/div/div[@class='panel panel-default']/div[@class='panel-body']/div[3]/div[@class='panel-heading']/h3[@class='panel-title']")).click();
				  	  	  	  	    																								    			    		    					        Thread.sleep(3000);	
				  	  	  	  	    																								    			    		    							Select select1 = new Select(driver.findElement(By.xpath("//div[@id='uc1']//select")));
				  	  	  	  	    																								    			    		    							Thread.sleep(2000);	
				  	  	  	  	    																								    			    		    							select1.selectByVisibleText("Device");
				  	  	  	  	    																								    			    		    							Thread.sleep(5000);	
				  	  	  	  	    																								    			    		    						    driver.findElement(By.xpath("//div[@id='device_option_sel2_chosen']/ul[@class='chosen-choices']")).click();
				  	  	  	  	    																								    			    		    						    Thread.sleep(2000);
				  	  	  	  	    																								    			    		    						    driver.findElement(By.xpath("//*[@id='device_option_sel2_chosen']/div/ul/li[1]")).click();
				  	  	  	  	    																								    			    		    						    logger.info("Device and Desktop selected Successfully");
				  	  	  	  	    																								    			    		    						    driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).click();
				  	  	  	  	    																								    			    		    							Thread.sleep(5000);
				  	  	  	  	    																								    			    		    							driver.findElement(By.xpath("/html//input[@id='audience_name']")).sendKeys("Desktop Audience");
				  	  	  	  	    																								    			    		    							Thread.sleep(2000);
				  	  	  	  	    																								    			    		    							driver.findElement(By.xpath("/html//button[@id='save_aud_btn']")).click();
				  	  	  	  	    																								    			    		    							Thread.sleep(3000);
				  	  	  	  	    																								    			    		    							logger.info("Case 5 - Implemented - Desktop Audience Created Successfully");
				  	  	  	  	    																								    			    		    							
				  	  	  	  	    																								    			    		    							//Case 6 - Select Device and all 3 types and Create Audience
				  	  	  	  	    																								    			    		    							
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//li[@id='view-audience']//span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//body/section[@class='page-container']/div[1]//button[@type='button']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//body/section/div[2]/div/div[@class='panel panel-default']/div[@class='panel-body']/div[3]/div[@class='panel-heading']/h3[@class='panel-title']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(3000);	
				  	  	  	  	    																								    			    										Select selecta = new Select(driver.findElement(By.xpath("//div[@id='uc1']//select")));
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										selecta.selectByVisibleText("Device");
				  	  	  	  	    																								    			    										Thread.sleep(5000);	
				  	  	  	  	    																								    			    									    driver.findElement(By.xpath("//div[@id='device_option_sel2_chosen']/ul[@class='chosen-choices']")).click();
				  	  	  	  	    																								    			    									    Thread.sleep(2000);
				  	  	  	  	    																								    			    									    driver.findElement(By.xpath("//*[@id='device_option_sel2_chosen']/div/ul/li[1]")).click();
				  	  	  	  	    																								    			    									    Thread.sleep(2000);
				  	  	  	  	    																								    			    									    driver.findElement(By.xpath("//div[@id='device_option_sel2_chosen']/ul[@class='chosen-choices']")).click();
				  	  	  	  	    																								    			    									    Thread.sleep(2000);
				  	  	  	  	    																								    			    									    driver.findElement(By.xpath("//*[@id=\'device_option_sel2_chosen\']/div/ul/li[2]")).click();
				  	  	  	  	    																								    			    									    Thread.sleep(2000);
				  	  	  	  	    																								    			    									    driver.findElement(By.xpath("//div[@id='device_option_sel2_chosen']/ul[@class='chosen-choices']")).click();
				  	  	  	  	    																								    			    									    Thread.sleep(2000);
				  	  	  	  	    																								    			    									    driver.findElement(By.xpath("//*[@id=\'device_option_sel2_chosen\']/div/ul/li[3]")).click();
				  	  	  	  	    																								    			    									    Thread.sleep(5000);
				  	  	  	  	    																								    			    									    logger.info("Device and all 3 selected Successfully");
				  	  	  	  	    																								    			    									    driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(5000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("/html//input[@id='audience_name']")).sendKeys("Device Audience");
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("/html//button[@id='save_aud_btn']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										logger.info("Case 6 - Implemented - Device Audience Created Successfully");
				  	  	  	  	    																								    			    										
				  	  	  	  	    																								    			    										//Case 7 - Create Audience with Event
				  	  	  	  	    																								    			    									       
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//li[@id='view-audience']//span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//body/section[@class='page-container']/div[1]//button[@type='button']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//body/section/div[2]/div/div[@class='panel panel-default']/div[@class='panel-body']/div[@class='panel panel-default']/div[@class='panel-heading']/h3[@class='panel-title']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//div[@id='showAdvancedFilter']/div[@class='panel panel-default']//button[@class='btn btn-primary btn-sm']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//div[@id='and_or_event_main']/div[1]/div[1]/select")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//*[@id=\"and_or_event_main\"]/div[1]/div[1]/select/option[4]")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//div[@id='and_or_event_main']/div[1]/a[@href='javascript:void(0)']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										Select selectb = new Select(driver.findElement(By.xpath("//div[@id='and_or_event_main']/div[1]/div[3]//span[@class='event_custom_prop']/select")));
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										selectb.selectByVisibleText("product_title");
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//div[@id='event_multi_sel_string1_chosen']/ul[@class='chosen-choices']//input[@value='Search']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//*[@id=\"event_multi_sel_string1_chosen\"]/div/ul/li")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(5000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("/html//input[@id='audience_name']")).sendKeys("Event Audience");
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("/html//button[@id='save_aud_btn']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										logger.info("Case 7 - Implemented - Event Audience Created Successfully");
				  	  	  	  	    																								    			    										
				  	  	  	  	    																								    			    										 //Case 8 - Create Audience with Event did and didn't event filter
				  	  	  	  	    																								    			    									       
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//li[@id='view-audience']//span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//body/section[@class='page-container']/div[1]//button[@type='button']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//body/section/div[2]/div/div[@class='panel panel-default']/div[@class='panel-body']/div[@class='panel panel-default']/div[@class='panel-heading']/h3[@class='panel-title']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//div[@id='showAdvancedFilter']/div[@class='panel panel-default']//button[@class='btn btn-primary btn-sm']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//div[@id='and_or_event_main']/div[1]/div[1]/select")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//*[@id=\"and_or_event_main\"]/div[1]/div[1]/select/option[4]")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//div[@id='and_or_event_main']/div[1]/a[@href='javascript:void(0)']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										Select select111 = new Select(driver.findElement(By.xpath("//div[@id='and_or_event_main']/div[1]/div[3]//span[@class='event_custom_prop']/select")));
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										select111.selectByVisibleText("product_title");
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//div[@id='event_multi_sel_string1_chosen']/ul[@class='chosen-choices']//input[@value='Search']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//*[@id=\"event_multi_sel_string1_chosen\"]/div/ul/li")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										
				  	  	  	  	    																								    			    										//Scroll to center of the page
				  	  	  	  	    																								    			    										WebElement element11 = driver.findElement(By.xpath("//div[@id='showAdvancedFilter']//div[@class='panel-body who_did_not_events']"));
				  	  	  	  	    																								    			    								        String scrollElementIntoMiddle11 = "var viewPortHeight = Math.max(document.documentElement.clientHeight, window.innerHeight || 0);"
				  	  	  	  	    																								    			    										                                            + "var elementTop = arguments[0].getBoundingClientRect().top;"
				  	  	  	  	    																								    			    										                                            + "window.scrollBy(0, elementTop-(viewPortHeight/2));";
				  	  	  	  	    																								    			    								         ((JavascriptExecutor) driver).executeScript(scrollElementIntoMiddle11, element11);
				  	  	  	  	    																								    			    										
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//div[@id='showAdvancedFilter']/div[3]//button[@class='btn btn-primary btn-sm mt-20']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//div[@id='and_event_main']/div[1]/div[1]/select")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//*[@id=\"and_event_main\"]/div[1]/div[1]/select/option[2]")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//div[@id='and_event_main']/div[1]/a[@href='javascript:void(0)']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										Select select1111 = new Select(driver.findElement(By.xpath("//div[@id='and_event_main']/div[1]/div[3]//span[@class='event_custom_prop']/select")));
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										select1111.selectByVisibleText("item_type");
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//*[@id=\"event_multi_sel_string2_chosen\"]/ul")).click();
				  	  	  	  	    																								    			    								        Thread.sleep(2000);	
				  	  	  	  	    																								    			    								        driver.findElement(By.xpath("//*[@id='event_multi_sel_string2_chosen']/div/ul/li")).click();
				  	  	  	  	    																								    			    								        Thread.sleep(2000);	
				  	  	  	  	    																								    			    								        driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(5000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("/html//input[@id='audience_name']")).sendKeys("Event Audience with did and didnot");
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("/html//button[@id='save_aud_btn']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										logger.info("Case 8 - Implemented - Event Audience Created with did and didn't filter Successfully");
				  	  	  	  	    																								    			    										
				  	  	  	  	    																								    			    										//Case 9 - Select User Property and create audience
				  	  	  	  	    																								    			    										
				  	  	  	  	    																								    			    										Thread.sleep(3000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//li[@id='view-audience']//span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//body/section[@class='page-container']/div[1]//button[@type='button']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//body/section/div[2]/div/div[@class='panel panel-default']/div[@class='panel-body']/div[3]/div[@class='panel-heading']/h3[@class='panel-title']")).click();
				  	  	  	  	    																								    			    								        Thread.sleep(3000);	
				  	  	  	  	    																								    			    										Select select11111 = new Select(driver.findElement(By.xpath("//div[@id='uc1']//select")));
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										select11111.selectByVisibleText("User Properties");
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//*[@id=\"uc1sel2_chosen\"]")).click();
				  	  	  	  	    																								    			    										Thread.sleep(5000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//*[@id=\"uc1sel2_chosen\"]/div/div/input")).sendKeys("gender");
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//*[@id=\"uc1sel2_chosen\"]/div/ul")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//*[@id=\"multi_sel_string1_chosen\"]/ul/li")).click();
				  	  	  	  	    																								    			    										Thread.sleep(3000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//*[@id=\"multi_sel_string1_chosen\"]/div/ul/li")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    									    driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).click();
				  	  	  	  	    																								    			    									    Thread.sleep(5000);
				  	  	  	  	    																								    			    									    driver.findElement(By.xpath("/html//input[@id='audience_name']")).sendKeys("User Property");
				  	  	  	  	    																								    			    									    Thread.sleep(2000);
				  	  	  	  	    																								    			    									    driver.findElement(By.xpath("/html//button[@id='save_aud_btn']")).click();
				  	  	  	  	    																								    			    									    Thread.sleep(2000);
				  	  	  	  	    																								    			    									    logger.info("Case 9 - Implemented - Audience Created with User Property Successfully");
				  	  	  	  	    																								    			    				
				  	  	  	  	    																								    			    									  //Case 10 - Create Audience with Location
				  	  	  	  	    																								    			    										
				  	  	  	  	    																								    			    									    driver.findElement(By.xpath("//li[@id='view-audience']//span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//body/section[@class='page-container']/div[1]//button[@type='button']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										 driver.findElement(By.xpath("//body/section/div[2]/div/div[@class='panel panel-default']/div[@class='panel-body']/div[3]/div[@class='panel-heading']/h3[@class='panel-title']")).click();
				  	  	  	  	    																								    			    									        Thread.sleep(3000);	
				  	  	  	  	    																								    			    											Select selecta1 = new Select(driver.findElement(By.xpath("//div[@id='uc1']//select")));
				  	  	  	  	    																								    			    											Thread.sleep(2000);	
				  	  	  	  	    																								    			    											selecta1.selectByVisibleText("Location");
				  	  	  	  	    																								    			    											Thread.sleep(3000);	
				  	  	  	  	    																								    			    											
				  	  	  	  	    																								    			    										    //select country
				  	  	  	  	    																								    			    											driver.findElement(By.xpath("/html//input[@id='country_1']")).sendKeys("in");
				  	  	  	  	    																								    			    											Thread.sleep(5000);
				  	  	  	  	    																								    			    											List<WebElement> suggestion = driver.findElements(By.className("ui-menu-item"));	
				  	  	  	  	    																								    			    												
				  	  	  	  	    																								    			    											for (WebElement suggest : suggestion) {
				  	  	  	  	    																								    			    												System.out.println(suggest.getText());
				  	  	  	  	    																								    			    												if(suggest.getText().equalsIgnoreCase("india"))
				  	  	  	  	    																								    			    													suggest.click();
				  	  	  	  	    																								    			    											}
				  	  	  	  	    																								    			    											Thread.sleep(5000);	
				  	  	  	  	    																								    			    											
				  	  	  	  	    																								    			    											//select state
				  	  	  	  	    																								    			    											driver.findElement(By.xpath("/html//input[@id='state_1']")).sendKeys("ut");
				  	  	  	  	    																								    			    											Thread.sleep(5000);
				  	  	  	  	    																								    			    											List<WebElement> suggestion1 = driver.findElements(By.className("ui-menu-item"));	
				  	  	  	  	    																								    			    												
				  	  	  	  	    																								    			    											for (WebElement suggest : suggestion1) {
				  	  	  	  	    																								    			    												System.out.println(suggest.getText());
				  	  	  	  	    																								    			    												if(suggest.getText().equalsIgnoreCase("uttar pradesh"))
				  	  	  	  	    																								    			    													suggest.click();
				  	  	  	  	    																								    			    											}
				  	  	  	  	    																								    			    												Thread.sleep(5000);	
				  	  	  	  	    																								    			    												
				  	  	  	  	    																								    			    												//select city
				  	  	  	  	    																								    			    												driver.findElement(By.xpath("/html//input[@id='city_1']")).sendKeys("n");
				  	  	  	  	    																								    			    												Thread.sleep(5000);
				  	  	  	  	    																								    			    												List<WebElement> suggestion11 = driver.findElements(By.className("ui-menu-item"));	
				  	  	  	  	    																								    			    													
				  	  	  	  	    																								    			    												for (WebElement suggest : suggestion11) {
				  	  	  	  	    																								    			    													System.out.println(suggest.getText());
				  	  	  	  	    																								    			    													if(suggest.getText().equalsIgnoreCase("noida"))
				  	  	  	  	    																								    			    														suggest.click();
				  	  	  	  	    																								    			    												}
				  	  	  	  	    																								    			    									  
				  	  	  	  	    																								    			    												Thread.sleep(2000);	
				  	  	  	  	    																								    			    											    driver.findElement(By.xpath("//body/section/div[2]/div[@class='row']/div/div[@class='panel-body']/div[4]/span[2]/button[@type='button']")).click();
				  	  	  	  	    																								    			    											    Thread.sleep(5000);
				  	  	  	  	    																								    			    											    driver.findElement(By.xpath("/html//input[@id='audience_name']")).sendKeys("Location");
				  	  	  	  	    																								    			    											    Thread.sleep(2000);
				  	  	  	  	    																								    			    											    driver.findElement(By.xpath("/html//button[@id='save_aud_btn']")).click();
				  	  	  	  	    																								    			    											    Thread.sleep(2000);
				  	  	  	  	    																								    			    											    logger.info("Case 10 - Implemented - Audience Created with Location Successfully");
				  	  	  	  	    																								    			    				
				  	  	  	  	    																								    			    						
				  	  	  	  	    																								    			    										
				  	  	  	  	    																								    			    										//Show Count
				  	  	  	  	    																								    			    										Thread.sleep(5000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("/html//table[@id='mainTable']/tbody[1]/tr[1]/td[2]/div[@class='action_btn']/a[@href='javascript:void(0)']")).click();
				  	  	  	  	    																								    			    										
				  	  	  	  	    																								    			    										//Push with Audience
				  	  	  	  	    																								    			    										logger.info("Push with Audience");
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//li[@id='create-campaign']//span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    								        driver.findElement(By.name("campname")).sendKeys("THIS IS A TEST NOTIFICATION");
				  	  	  	  	    																								    			    								        Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//form[@id='camp_form']/div[1]/div[@class='col-md-12']//div[@class='widget-body']/div[2]//input[@class='emoji-wysiwyg-editor form-control input_wid_camp iz_color_input no-line-break titleDiv']")).sendKeys("THIS IS TEST TITLE");
				  	  	  	  	    																								    			    										Thread.sleep(2000);	
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//form[@id='camp_form']/div[1]/div[@class='col-md-12']//div[@class='form-group mb-0']//input[@placeholder='Notification Message']")).sendKeys("THIS IS TEST MESSAGE");
				  	  	  	  	    																								    			    										driver.findElement(By.name("landurl")).sendKeys("www.izooto.com");
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("/html//select[@id='populateAudience']")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										driver.findElement(By.xpath("//*[@id=\"populateAudience\"]/option[15]")).click();
				  	  	  	  	    																								    			    										Thread.sleep(2000);
				  	  	  	  	    																								    			    										driver.findElement(By.name("push_now")).click();
				  	  	  	  	    																								    			    									    Thread.sleep(2000);	
				  	  	  	  	    																								    			    									    driver.findElement(By.xpath("/html//input[@id='push_btn']")).click();
				  	  	  	  	    																								    			    									    logger.info("Pushed with Audience Successfully");
				  	  	  	  	    																								
				  	  	  	  	    																								    			    								        Thread.sleep(2000);	
				  	  	  	  	    																								    			    								        driver.close();
				  	  	  	  	    																								    			    								        
				  	  	  	  	    																								    			    								        //API Request
				  	  	  	  	    																								    			    								        
				  	  	  	  	    																								    			    								//Open Chrome Browser
				  	  	  	  	    																								    			    								String exePath1 = "C:\\SeleniumDrivers\\chromedriver.exe";
				  	  	  	  	    																								    			    								System.setProperty("webdriver.chrome.driver", exePath1);
				  	  	  	  	    																								    			    								WebDriver driver1 = new ChromeDriver();
				  	  	  	  	    																								    			    								logger.info("Chrome Opened Successfully");
				  	  	  	  	    																								    			    								
				  	  	  	  	    																								    			    								//Maximize Chrome Browser
				  	  	  	  	    																								    			    								driver1.manage().window().maximize();
				  	  	  	  	    																								    			    								logger.info("Browser Maximised Successfully");
				  	  	  	  	    																								    			    								
				  	  	  	  	    																								    			    								//Panel Login 
				  	  	  	  	    																								    			    								
				  	  	  	  	    																								    			    								driver1.get("https://panel.izooto.com/logout");
				  	  	  	  	    																								    			    							    driver1.findElement(By.name("email")).sendKeys("dummyizgobble@gmail.com");
				  	  	  	  	    																								    			    								driver1.findElement(By.name("password")).sendKeys("123456");
				  	  	  	  	    																								    			    								driver1.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).click();
				  	  	  	  	    																								    			    								logger.info("Logged In Successfully");
				  	  	  	  	    																								    			    								
				  	  	  	  	    																								    			    								Thread.sleep(5000);
				  	  	  	  	    																								    			    								
				  	  	  	  	    																								    			    			
				  	  	  	  	    																								    			    	//Refresh Page
				  	  	  	  	    																								    					driver1.navigate().refresh();
				  	  	  	  	    																								    					
				  	  	  	  	    																								    					//Click on Setting Dropdown
				  	  	  	  	    																								    					
				  	  	  	  	    																								    			        Thread.sleep(2000);
				  	  	  	  	    																								    			        driver1.findElement(By.xpath("//a[@id='settingsA']/span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    			        logger.info("Setting dropdown expanded successfully");
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    			        Thread.sleep(2000);    
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    			      //Click on Get API Key
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    			        driver1.findElement(By.xpath("/html//a[@id='api-credentials']")).click();
				  	  	  	  	    																								    			        Thread.sleep(2000);    
				  	  	  	  	    																								    			        logger.info("Get API Request page opened successfully");
				  	  	  	  	    																								    			        Thread.sleep(2000);
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    			       //Click on Request for API Key
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    			        driver1.findElement(By.xpath("/html//button[@id='requestnewbtn']")).click();
				  	  	  	  	    																								    			        logger.info("API Request submitted successfully");
				  	  	  	  	    																								    			        Thread.sleep(5000);
				  	  	  	  	    																								    					
				  	  	  	  	    																								    			    
				  	  	  	  	    																								    			        //Click logout
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    					WebElement signout1 = driver1.findElement(By.xpath("/html//a[@id='dropdownMenu2']"));
				  	  	  	  	    																								    					signout1.click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    				    driver1.findElement(By.xpath("//header[@id='mainheader']/div/div[3]/ul/li/div/ul[@class='media-list']//a[@href='https://panel.izooto.com/logout']")).click();
				  	  	  	  	    																								    				    logger.info("Logged Out Successfully");
				  	  	  	  	    																								    				    
				  	  	  	  	    																								    				    //Login to admin account
				  	  	  	  	    																								    				    
				  	  	  	  	    																								    				    Thread.sleep(4000);
				  	  	  	  	    																								    				    driver1.findElement(By.name("email")).sendKeys("vipin@datability.co");
				  	  	  	  	    																								    					driver1.findElement(By.name("password")).sendKeys("123456");
				  	  	  	  	    																								    					driver1.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).click();
				  	  	  	  	    																								    					logger.info("Logged In to admin account Successfully");
				  	  	  	  	    																								    					
				  	  	  	  	    																								    					//Goto Tars
				  	  	  	  	    																								    				    
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1.findElement(By.xpath("/html//a[@id='dropdownMenu2']")).click();
				  	  	  	  	    																								    					Thread.sleep(2000);    
				  	  	  	  	    																								    					driver1.findElement(By.xpath("//*[@id=\"mainheader\"]/div/div[3]/ul/li/div/ul/li[7]")).click();
				  	  	  	  	    																								    					Thread.sleep(2000);
				  	  	  	  	    																								    					logger.info("Tars Opened Successfully");
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    					//Go to API Key Generation
				  	  	  	  	    																								    					
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1.findElement(By.xpath("//div[@id='example-manipulation']//ul[@role='tablist']//a[@href='#example-manipulation-h-9']")).click();
				  	  	  	  	    																								    					Thread.sleep(2000);    
				  	  	  	  	    																								    					driver1.findElement(By.xpath("//*[@id=\"apiKeysTable\"]/thead/tr/th[3]/input")).sendKeys("dummyizgobble17");
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1.findElement(By.cssSelector(".btn-primary.btn-sm")).click(); 
				  	  	  	  	    																								    					Thread.sleep(2000); 
				  	  	  	  	    																								    					logger.info("API Key generated Successfully");
				  	  	  	  	    																								    					
				  	  	  	  	    																								    					driver1.close();
				  	  	  	  	    																								    					
				  	  	  	  	    																								    					//Open Chrome Browser
				  	  	  	  	    																								    					String exePath11 = "C:\\SeleniumDrivers\\chromedriver.exe";
				  	  	  	  	    																								    					System.setProperty("webdriver.chrome.driver", exePath11);
				  	  	  	  	    																								    					WebDriver driver11 = new ChromeDriver();
				  	  	  	  	    																								    					logger.info("Chrome Opened Successfully");
				  	  	  	  	    																								    					Thread.sleep(2000);
				  	  	  	  	    																								    					driver11.manage().window().maximize();
				  	  	  	  	    																								    					
				  	  	  	  	    																								    					//Go to Panel API Request page
				  	  	  	  	    																								    					
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver11.get("https://panel.izooto.com/logout");
				  	  	  	  	    																								    					Thread.sleep(2000); 
				  	  	  	  	    																								    					driver11.findElement(By.name("email")).sendKeys("dummyizgobble@gmail.com");
				  	  	  	  	    																								    				    driver11.findElement(By.name("password")).sendKeys("123456");
				  	  	  	  	    																								    				    driver11.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).click();
				  	  	  	  	    																								    					logger.info("Logged In Successfully");
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					
				  	  	  	  	    																								    			       //Click on Setting Dropdown
				  	  	  	  	    																								    					
				  	  	  	  	    																								    			        driver11.findElement(By.xpath("//a[@id='settingsA']/span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    			        logger.info("Setting dropdown expanded successfully");
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    			        Thread.sleep(2000);    
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    			      //Click on Get API Key
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    			        driver11.findElement(By.xpath("/html//a[@id='api-credentials']")).click();
				  	  	  	  	    																								    			        Thread.sleep(2000);    
				  	  	  	  	    																								    			        logger.info("API Generated successfully");
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    			        driver11.close();
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    			        //Welcome Notification
				  	  	  	  	    																								    			        
				  	  	  	  	    																								    			//Logger Implementation
				  	  	  	  	    																								    			
				  	  	  	  	    																								    		    Logger logger1 = Logger.getLogger("SignupLoginAddWebsitePushAudienceApi");
				  	  	  	  	    																								    			PropertyConfigurator.configure("Log4j.properties");

				  	  	  	  	    																								    			//Open Chrome Browser
				  	  	  	  	    																								    		
				  	  	  	  	    																								    			String exePath111 = "C:\\SeleniumDrivers\\chromedriver.exe";
				  	  	  	  	    																								    			System.setProperty("webdriver.chrome.driver", exePath111);
				  	  	  	  	    																								    			WebDriver driver111 = new ChromeDriver();
				  	  	  	  	    																								    			logger1.info("Chrome Opened Successfully");
				  	  	  	  	    																								    			
				  	  	  	  	    																								    			//Maximize Chrome Browser
				  	  	  	  	    																								    			
				  	  	  	  	    																								    		    driver111.manage().window().maximize();
				  	  	  	  	    																								    			logger1.info("Chrome Maximized Successfully");
				  	  	  	  	    																								    			
				  	  	  	  	    																								    		    //Login Panel
				  	  	  	  	    																								    			
				  	  	  	  	    																								    			driver111.get("https://panel.izooto.com");
				  	  	  	  	    																								    			driver111.findElement(By.name("email")).sendKeys("dummyizautomate@gmail.com");
				  	  	  	  	    																								    			driver111.findElement(By.name("password")).sendKeys("123456");
				  	  	  	  	    																								    			driver111.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).click();
				  	  	  	  	    																								    			logger1.info("Panel logged in successfully");
				  	  	  	  	    																								    			Thread.sleep(5000);	

				  	  	  	  	    																								    			//Refresh dashboard
				  	  	  	  	    																								    			
				  	  	  	  	    																								    			driver111.navigate().refresh();

				  	  	  	  	    																								    			//Open Welcome Notification page
				  	  	  	  	    																								    			
				  	  	  	  	    																								    			Thread.sleep(2000);
				  	  	  	  	    																								    			driver111.findElement(By.xpath("//li[@id='welcome-notification']//span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    			logger1.info("Welcome Notification opened Successfully");
				  	  	  	  	    																								    			Thread.sleep(2000);	

				  	  	  	  	    																								    			//Test case 1
				  	  	  	  	    																								    			
				  	  	  	  	    																								    			driver111.findElement(By.xpath("//body/section[@class='page-container']//div[@class='col-md-7 welcome-bg']//span[@class='switch-label']")).click();
				  	  	  	  	    																								    			////body/section[@class='page-container']//div[@class='col-md-7 welcome-bg']//span[@class='switch-label']
				  	  	  	  	    																								    			// working fine need to enter notification title
				  	  	  	  	    																								    			driver111.findElement(By.xpath("//body/section[@class='page-container']/div[@class='container pt-30']/div[@class='welcomeOptions']/div[@class='row']//button[@type='button']")).click();
				  	  	  	  	    																								    			//working fine
				  	  	  	  	    																								    			      Thread.sleep(2000); 
				  	  	  	  	    																								    			      
				  	  	  	  	    																								    			       // talk to us click button
				  	  	  	  	    																								    			       //driver.findElement(By.xpath("//div[@id='paymentRequired']/div[@role='document']/div[@class='modal-content']//a[@href='javascript:void(0)']")).click();
				  	  	  	  	    																								    			       Thread.sleep(2000); 
				  	  	  	  	    																								    			       // closed the izootobot
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			      
				  	  	  	  	    																								    			     //driver.findElement(By.xpath("//div[@id='paymentRequired']/div[@role='document']//button[@type='button']/span[.='×'] ")).click();
				  	  	  	  	    																								    			     Thread.sleep(2000); 
				  	  	  	  	    																								    			     // Enter notification title here
				  	  	  	  	    																								    			  // Test case 2 title no enter then error message should come
				  	  	  	  	    																								    			     Thread.sleep(5000);
				  	  	  	  	    																								    			     driver111.findElement(By.xpath("/html//input[@id='wsTitle']")).sendKeys("");
				  	  	  	  	    																								    			     
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//body/section[@class='page-container']/div[@class='container pt-30']/div[@class='welcomeOptions']/div[@class='row']//button[@type='button']")).click();
				  	  	  	  	    																								    			    // Test case 3 title entered then please enter welcome notification message should come
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("/html//input[@id='wsTitle']")).sendKeys("Test welcome notifiction here vipin");
				  	  	  	  	    																								    			       Thread.sleep(5000);  
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//body/section[@class='page-container']/div[@class='container pt-30']/div[@class='welcomeOptions']/div[@class='row']//button[@type='button']")).click();
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			    // Test case 4 message entered then please upload notification icon should come 
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("/html//input[@id='wsTitle']")).clear();
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("/html//input[@id='wsTitle']")).sendKeys("Test welcome notifiction here vipin");
				  	  	  	  	    																								    			       Thread.sleep(5000); 
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("/html//input[@id='campmessage']")).sendKeys(" welcome message notifiction data");
				  	  	  	  	    																								    			       Thread.sleep(3000);
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//body/section[@class='page-container']/div[@class='container pt-30']/div[@class='welcomeOptions']/div[@class='row']//button[@type='button']")).click();
				  	  	  	  	    																								    			    // Test case 5 icon upload 
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("/html//input[@id='wsTitle']")).clear();
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("/html//input[@id='wsTitle']")).sendKeys("Test welcome notifiction here vipin");
				  	  	  	  	    																								    			       Thread.sleep(5000); 
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("/html//input[@id='campmessage']")).sendKeys(" welcome message notifiction data");
				  	  	  	  	    																								    			       Thread.sleep(3000);
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//body/section[@class='page-container']/div[@class='container pt-30']/div[@class='welcomeOptions']/div[@class='row']//button[@type='button']")).click();
				  	  	  	  	    																								    			       //click icon upload 
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//form[@id='imgForm']//span[@class='group-span-filestyle input-group-btn']//span[@class='buttonText']")).click();
				  	  	  	  	    																								    			       Thread.sleep(5000); 
				  	  	  	  	    																								    			       // negative test add in icon upload
				  	  	  	  	    																								    			       Runtime.getRuntime().exec("C:\\Users\\hp\\Desktop\\AutoIT\\ImageUpload.exe"); 
				  	  	  	  	    																								    			       // added negative test case here
				  	  	  	  	    																								    			       // image upload my direcTORY
				  	  	  	  	    																								    			       Runtime.getRuntime().exec("C:\\Users\\hp\\Desktop\\AutoIT\\ImageUpload.exe"); 
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			      // CLICK ON OK BUTTON
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       driver111.findElement(By.cssSelector("[onclick='closeCroppieIconC\\(\\)']")).click();
				  	  	  	  	    																								    			       Thread.sleep(5000);  
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("/html//input[@id='wsLand']")).sendKeys("www.izooto.com");
				  	  	  	  	    																								    			       //Push button clicked
				  	  	  	  	    																								    			       Thread.sleep(4000);
				  	  	  	  	    																								    			       driver111.findElement(By.cssSelector("[class='col-md-12 pr-0 pl-0 mt-10'] [data-on]")).click();
				  	  	  	  	    																								    			       Thread.sleep(4000);
				  	  	  	  	    																								    			       //driver.findElement(By.xpath("//div[@id='showNotiImage']//div[@class='col-md-12 pl-0 pr-0']//input[@name='bannerbase64']")).sendKeys("");
				  	  	  	  	    																								    			       driver111.findElement(By.cssSelector(".save-btn-wid")).click();
				  	  	  	  	    																								    			       System.out.println("banner canot blank");
				  	  	  	  	    																								    			       // clear banner then enter banner
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//div[@id='showNotiImage']//div[@class='col-md-12 pl-0 pr-0']//input[@name='bannerbase64']")).click();
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//div[@id='showNotiImage']//div[@class='col-md-12 pl-0 pr-0']//input[@name='bannerbase64']")).sendKeys("https://homepages.cae.wisc.edu/~ece533/images/airplane.png");
				  	  	  	  	    																								    			       //save button click
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			       // add notification button tab click
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//body/section[@class='page-container']/div[@class='container pt-30']/div[3]/div[@class='welcomeOptions']//span[@class='switch-label']")).click();
				  	  	  	  	    																								    			       //---.save-btn-wid
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       driver111.findElement(By.cssSelector(".save-btn-wid")).click();
				  	  	  	  	    																								    			       System.out.println("banner url entered and cta button name cannot blank");
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			// Enter cta button name
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//body/section[@class='page-container']/div[@class='container pt-30']/div[3]/div[@class='welcomeOptions']//div[@class='widget']/div[2]/form[@method='post']//input[@name='button1name']")).sendKeys("button 1 cta");
				  	  	  	  	    																								    			       //---.save-btn-wid
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       driver111.findElement(By.cssSelector(".save-btn-wid")).click();
				  	  	  	  	    																								    			       System.out.println("cta one entered and cta one url is blank");
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			       //Button 1 Landing URL enter
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//body/section[@class='page-container']/div[@class='container pt-30']/div[3]/div[@class='welcomeOptions']//div[@class='widget']/div[2]/form[@method='post']//input[@name='button1link']")).clear();
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//body/section[@class='page-container']/div[@class='container pt-30']/div[3]/div[@class='welcomeOptions']//div[@class='widget']/div[2]/form[@method='post']//input[@name='button1link']")).sendKeys("www.izooto.com");
				  	  	  	  	    																								    			       //---.save-btn-wid
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       //driver.findElement(By.cssSelector(".save-btn-wid")).click();
				  	  	  	  	    																								    			       System.out.println("cta one entered and cta one url is blank");
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			// clicked to add another button

				  	  	  	  	    																								    			       driver111.findElement(By.xpath("/html//button[@id='addBtn2']")).click();
				  	  	  	  	    																								    			       //button name and url enter
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//div[@id='btn2']/div[@class='col-md-4']//input[@name='button2name']")).sendKeys("test button 2");
				  	  	  	  	    																								    			       //---.save-btn-wid
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       //button 2 url
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//div[@id='btn2']/div[@class='col-md-4']//input[@name='button2name']")).sendKeys("");
				  	  	  	  	    																								    			       driver111.findElement(By.cssSelector(".save-btn-wid")).click();
				  	  	  	  	    																								    			       System.out.println("cta two url blank");
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			// cta 2 enter url
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			      // driver.findElement(By.cssSelector("#btn2 .btnDis")).clear();
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//div[@id='btn2']/div[@class='col-md-7 plr-0']//input[@name='button2link']")).sendKeys("www.facebool.com");
				  	  	  	  	    																								    			      // driver.findElement(By.cssSelector(".save-btn-wid")).click();
				  	  	  	  	    																								    			       System.out.println("cta two url entered");
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			       driver111.findElement(By.cssSelector(".save-btn-wid")).click();
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			       

				  	  	  	  	    																								    			       // back to dashboard
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//li[@id='dashboard']//span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    			       //again click welcome notification for disabled
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			       Thread.sleep(5000);
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//li[@id='welcome-notification']//span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    			       // //body/section[@class='page-container']//div[@class='col-md-7 welcome-bg']//span[@class='switch-label']
				  	  	  	  	    																								    			       Thread.sleep(3000);
				  	  	  	  	    																								    			       driver111.findElement(By.xpath("//body/section[@class='page-container']//div[@class='col-md-7 welcome-bg']//span[@class='switch-label']")).click();
				  	  	  	  	    																								    			       	Thread.sleep(5000);
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			//Logout from panel
				  	  	  	  	    																								    			       
				  	  	  	  	    																								    			       WebElement signout = driver111.findElement(By.xpath("/html//a[@id='dropdownMenu2']"));
				  	  	  	  	    																								    					signout.click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    				    driver111.findElement(By.xpath("//header[@id='mainheader']/div/div[3]/ul/li/div/ul[@class='media-list']//a[@href='https://panel.izooto.com/logout']")).click();
				  	  	  	  	    																								    				    logger1.info("Logged Out Successfully");
				  	  	  	  	    																								    				    
				  	  	  	  	    																								    				    Thread.sleep(2000);
				  	  	  	  	    																								    				    
				  	  	  	  	    																								    				    driver111.close();
				  	  	  	  	    																								    				    
				  	  	  	  	    																								    				    //Modify Subscription prompt
				  	  	  	  	    																								    				    
				  	  	  	  	    																								    				    Thread.sleep(2000);
				  	  	  	  	    																								    				    
				  	  	  	  	    																								    				    System.out.println("Starting Login Test");
				  	  	  	  	    																								    					String exePath1111 = "C:\\SeleniumDrivers\\chromedriver.exe";
				  	  	  	  	    																								    					System.setProperty("webdriver.chrome.driver", exePath1111);
				  	  	  	  	    																								    					WebDriver driver1111 = new ChromeDriver();
				  	  	  	  	    																								    					driver1111.manage().window().maximize();
				  	  	  	  	    																								    					driver1111.get("https://panel.izooto.com");
				  	  	  	  	    																								    					driver1111.findElement(By.name("email")).sendKeys("dummyizautomate@gmail.com");
				  	  	  	  	    																								    					driver1111.findElement(By.name("password")).sendKeys("123456");
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//form[@id='loginForm']/input[@value='Log In']")).click();
				  	  	  	  	    																								    					System.out.println("Page is Opened");

				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					
				  	  	  	  	    																								    					//driver.navigate().refresh();

				  	  	  	  	    																								    					// setting page click
				  	  	  	  	    																								    					Thread.sleep(2000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//a[@id='settingsA']/span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    					System.out.println(" Clicked on setting  tab");

				  	  	  	  	    																								    					Thread.sleep(2000);	
				  	  	  	  	    																								    					// dailog box full comment



				  	  	  	  	    																								    					//Test case 1--click on subscription prompt tab then dailog box testing
				  	  	  	  	    																								    					 	driver1111.findElement(By.xpath("/html//a[@id='multi-optin']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move on subscription page");


				  	  	  	  	    																								    					// click on dailog box prompt
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[2]/div/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("clicked on dailog box subscription page");

				  	  	  	  	    																								    					//Test case 2 clear default test
				  	  	  	  	    																								    					// clear title
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_first']")).clear();
				  	  	  	  	    																								    					// clear message
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_first']")).clear();
				  	  	  	  	    																								    					// click save & activate button
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[7]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000); 
				  	  	  	  	    																								    					System.out.println("title can't blank"); 
				  	  	  	  	    																								    					 

				  	  	  	  	    																								    					//Test case 2 message can't be blank

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_first']")).sendKeys("vipin test");
				  	  	  	  	    																								    					// clear message
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_first']")).clear();
				  	  	  	  	    																								    					// click save & activate button
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[7]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000); 
				  	  	  	  	    																								    					System.out.println("message can be blank"); 
				  	  	  	  	    																								    					 
				  	  	  	  	    																								    					// title text more then given test
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[2]/div/div/button[.='Edit']")).click();

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_first']")).sendKeys("vipin difference between Radio button and Checkbox is that, using radio button we will be able to select only one option from the options available. whereas using checkbox, we can select multiple options.\r\n" + 
				  	  	  	  	    																								    					"\r\n" + 
				  	  	  	  	    																								    					"When we inspect a Radio button or a Checkbox, HTML code looktest");
				  	  	  	  	    																								    					// clear message
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_first']")).sendKeys("difference between Radio button and Checkbox is that, using radio button we will be able to select only one option from the options available. whereas using checkbox, we can select multiple options.\r\n" + 
				  	  	  	  	    																								    					"\r\n" + 
				  	  	  	  	    																								    					"When we inspect a Radio button or a Checkbox, HTML code look");
				  	  	  	  	    																								    					// click save & activate button
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[7]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000); 
				  	  	  	  	    																								    					System.out.println("save and active successfully");
				  	  	  	  	    																								    					// chinese languages 
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[2]/div/div/button[.='Edit']")).click();

				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_first']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_first']")).sendKeys("服务即时翻译英语和ove之间的单词，短语和网页服务即时翻译英语和ove之间的单词，短语和网页服务即时翻译英语和ove之间的单词，短语和网页");
				  	  	  	  	    																								    					// clear message
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_first']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_first']")).sendKeys("服务即时翻译英语和ove之间的单词，短语和网页服务即时翻译英语和ove之间的单词，短语和网页服务即时翻译英语和ove之间的单词，短语和网页");
				  	  	  	  	    																								    					// click save & activate button
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[7]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000); 
				  	  	  	  	    																								    					System.out.println("save and active successfully");

				  	  	  	  	    																								    					// hindi laguage selected as inputs

				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[2]/div/div/button[.='Edit']")).click();

				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_first']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_first']")).sendKeys("विराट कोहली की नजरों में टीम के चयन को लेकर ज्यादा माथापच्ची नहीं है। आस्ट्रेलिया के खिलाफ वन-डे श्रृंखला 2-3 से हारने के बाद खुद कोहली खुलासा कर चुके हैं कि सिर्फ एक स्थान को लेकर दिक्कत है, लेकिन इसी स्थान ने चयनकर्ताओं के काम को पेचीदा कर रखा है। ");
				  	  	  	  	    																								    					// clear message
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_first']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_first']")).sendKeys("नंबर चार के बल्लेबाजी क्रम से लेकर दूसरे विकेटकीपर और चौथे तेज गेंदबाज को लेकर लंबे समय से बहस जारी है। टीम के चयन से पह");
				  	  	  	  	    																								    					// click save & activate button
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[7]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000); 
				  	  	  	  	    																								    					System.out.println("save and active successfully");
				  	  	  	  	    																								    					// allow button click

				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[2]/div/div/button[.='Edit']")).click();

				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='one-time']")).click();

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_first']")).clear();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_first']")).sendKeys("विराट कोहली की नज");

				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='recurring']")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_first']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_first']")).sendKeys("amarujalatest");
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[7]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(5000); 
				  	  	  	  	    																								    					System.out.println("save and active successfully");
				  	  	  	  	    																								    					//Upload icon and change color of text and background
				  	  	  	  	    																								    					// click on background color
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[2]/div/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000); 
				  	  	  	  	    																								    					// choose color
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(7) .customization-body__contents div:nth-child(1) .minicolors-input")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					// click choosen color
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(7) .customization-body__contents div:nth-child(1) .minicolors-grid-inner")).click();
				  	  	  	  	    																								    					Thread.sleep(7000);
				  	  	  	  	    																								    					// click outsite
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='recurring']")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					// again radio batton
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='prompt-radio']")).click();
				  	  	  	  	    																								    					// click upload icon
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//section[@class='page-container']/div[2]/div[7]//div[@class='customization-body scrollbar']//div[@class='radio-prompt']//div[@class='upload-banner']/i[@class='ti-upload']")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					Runtime.getRuntime().exec("C:\\Users\\hp\\Desktop\\AutoIT\\ImageUpload.exe"); 
				  	  	  	  	    																								    					Thread.sleep(5000);



				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_first']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_first']")).sendKeys("ઈ સેવા અંગ્રેજી, ઓવ વચ્ચેના શબ્દો, શબ્દસમૂહો અને વેબ પૃષ્ઠોનો તરત જ અનુવાદ કરે છે");
				  	  	  	  	    																								    					// clear message 
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_first']")).clear();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_first']")).sendKeys("ਈ ਸਰਵਿਸ ਅੰਗ੍ਰੇਜ਼ੀ ਅਤੇ ਓਵ ਦੇ ਵਿਚਲੇ ਸ਼ਬਦਾਂ, ਵਾਕਾਂਸ਼ ਅਤੇ ਵੈਬ ਪੇਜਾਂ ਦਾ ਤੁਰੰਤ ਅਨੁਵਾਦ ਕਰਦੀ ਹੈ");
				  	  	  	  	    																								    					Thread.sleep(5000);


				  	  	  	  	    																								    					// click save & activate button
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[7]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);  
				  	  	  	  	    																								    					// dailog box testing done here now

				  	  	  	  	    																								    					//full dailog box under comment


				  	  	  	  	    																								    					//driver.navigate().refresh();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//a[@id='multi-optin']")).click();


				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move on subscription page");

				  	  	  	  	    																								    					//Test case 1--click on subscription prompt tab then  testing

				  	  	  	  	    																								    					     Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move to  page ");
				  	  	  	  	    																								    					// click on  prompt
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("clicked on  prompt for subscription page");

				  	  	  	  	    																								    					//Test case 
				  	  	  	  	    																								    					// 
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// click color selection
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .customization-body__contents div:nth-child(1) .minicolors-input")).click();
				  	  	  	  	    																								    					// select green color
				  	  	  	  	    																								    					// choose color
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .customization-body__contents div:nth-child(1) .minicolors-input")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					System.out.println("color selected");
				  	  	  	  	    																								    					// click choosen color
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .customization-body__contents div:nth-child(1) .minicolors-grid-inner")).click();
				  	  	  	  	    																								    					Thread.sleep(7000);
				  	  	  	  	    																								    					// click outsite
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(1) .radio-btn")).click();
				  	  	  	  	    																								    					// click radio button two then one
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					System.out.println("radio button one clicked"); 
				  	  	  	  	    																								    					// click on title text color

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// click color selection
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .radio-prompt div:nth-of-type(3) .minicolors-input")).click();
				  	  	  	  	    																								    					// select green color
				  	  	  	  	    																								    					// choose color
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .radio-prompt div:nth-of-type(3) .minicolors-input")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					System.out.println("color selected");
				  	  	  	  	    																								    					// click choosen color
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .radio-prompt > div:nth-of-type(3) .minicolors-picker div")).click();
				  	  	  	  	    																								    					Thread.sleep(7000);
				  	  	  	  	    																								    					// click outsite
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .radio-prompt > div:nth-of-type(3) .minicolors-grid-inner")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(1) .radio-btn")).click();
				  	  	  	  	    																								    					 // message text color change

				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) div:nth-of-type(5) .minicolors-input")).click();
				  	  	  	  	    																								    					// select green color
				  	  	  	  	    																								    					// choose color
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) div:nth-of-type(5) .minicolors-input")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					System.out.println("color selected");
				  	  	  	  	    																								    					// click choosen color
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) div:nth-of-type(5) .minicolors-grid-inner")).click();
				  	  	  	  	    																								    					Thread.sleep(7000);
				  	  	  	  	    																								    					// click outsite
				  	  	  	  	    																								    					//driver.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) div:nth-of-type(5) .minicolors-grid-inner")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(1) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					// title is blank
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("#optin_title_second")).clear();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					// click save and activate button
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[onclick='savemeall\\(this\\, \\'second\\'\\,2\\,\\'desktop\\'\\)\\;']")).click();
				  	  	  	  	    																								    					// title and save button enter

				  	  	  	  	    																								    					// title is blank
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("#optin_title_second")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("#optin_title_second")).sendKeys("Addressing a public rally in Sambalpur in Odisha, Prime Minister Narendra Modi promised");
				  	  	  	  	    																								    					System.out.println("title entered");
				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					// click save and activate button

				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[onclick='savemeall\\(this\\, \\'second\\'\\,2\\,\\'desktop\\'\\)\\;']")).click();
				  	  	  	  	    																								    					// with positive and negative

				  	  	  	  	    																								    					//  one negative test case


				  	  	  	  	    																								    					// Negative test case for 
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					// optin tab click
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//a[@id='multi-optin']")).click();
				  	  	  	  	    																								    					// will remove that after negative test cases done for clicking on optin page

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					    driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move to  page for negative test cases ");
				  	  	  	  	    																								    					// click on  prompt
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("clicked on  prompt for subscription page");
				  	  	  	  	    																								    					// edit title text box or clear
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).clear();
				  	  	  	  	    																								    					System.out.println(" title cannot blank");
				  	  	  	  	    																								    					// clicking save button
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[onclick='savemeall\\(this\\, \\'second\\'\\,2\\,\\'desktop\\'\\)\\;']")).click();	
				  	  	  	  	    																								    					System.out.println(" save button clicked");	
				  	  	  	  	    																								    					// radio button one click allow radion
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					// allow button clear
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_second']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_second']")).clear();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					//save button clicked here
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[onclick='savemeall\\(this\\, \\'second\\'\\,2\\,\\'desktop\\'\\)\\;']")).click();	
				  	  	  	  	    																								    					System.out.println(" save button clicked after allow button cannot blank");
				  	  	  	  	    																								    					// save button click

				  	  	  	  	    																								    					// radio button two click
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// click radio button three for
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// radio button three clear and click
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_second']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_second']")).clear();
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[onclick='savemeall\\(this\\, \\'second\\'\\,2\\,\\'desktop\\'\\)\\;']")).click();	
				  	  	  	  	    																								    					System.out.println(" save button clicked after later button cannot blank");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// Clicking prompt radio button
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(1) .radio-btn")).click();
				  	  	  	  	    																								    					System.out.println(" clicked prompt radio button");
				  	  	  	  	    																								    					// enter text in title text box
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).sendKeys("positive test b start here");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// edit message text box
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_second']")).click();
				  	  	  	  	    																								    					// clear message text boz
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_second']")).clear();
				  	  	  	  	    																								    					System.out.println("message text box has been clear");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// enter values in message text box
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_second']")).sendKeys(" data base testing here");
				  	  	  	  	    																								    					System.out.println("message text box has been entered now");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// save button click
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[onclick='savemeall\\(this\\, \\'second\\'\\,2\\,\\'desktop\\'\\)\\;']")).click();	
				  	  	  	  	    																								    					System.out.println(" save button clicked after  title and message entered");

				  	  	  	  	    																								    					// again click radio button one(allow) because already blank
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_second']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_second']")).sendKeys("vipintest");
				  	  	  	  	    																								    					System.out.println(" allow button text entered");

				  	  	  	  	    																								    					// again click radio button three(later button) because already blank
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// enter text radio button three
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_second']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_second']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_second']")).sendKeys("dataabasehai");
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[onclick='savemeall\\(this\\, \\'second\\'\\,2\\,\\'desktop\\'\\)\\;']")).click();	
				  	  	  	  	    																								    					System.out.println(" save button clicked after later button cannot blank");
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// title message allow and later button testing for different languages-- test case for hind language 

				  	  	  	  	    																								    					// click to edit button on 

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println(" edit button");

				  	  	  	  	    																								    					// title text button click and clear then enter new text
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).sendKeys(" ड्रग्स रखने पर जापान में 2 साल की जेलनारायण साईं-आसाराम ही नहीं ये ");

				  	  	  	  	    																								    					// Message title edit text in hindi
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_second']")).clear();
				  	  	  	  	    																								    					//clear text in title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_second']")).sendKeys("कारोबारी नेस वाडिया को ड्रग्स रखने पर जापान में 2 साल की जेलनारायण साईं-आसाराम ही नहीं ये बाबा भी हैं का");
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("title text enter in hindi language");
				  	  	  	  	    																								    					// click and clear radio button 1 and enter hind text

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_second']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_second']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_second']")).sendKeys("काशी के बाद अयोध्या");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in hindi language and click and clear radio button 1 and enter hind text");
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// click and clear radio button 2 and enter hind text
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_second']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_second']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_second']")).sendKeys("राहुल को ब्रिटिश नागरिक क्यों बताते हैं स्वामी, जा");
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[onclick='savemeall\\(this\\, \\'second\\'\\,2\\,\\'desktop\\'\\)\\;']")).click();	
				  	  	  	  	    																								    					System.out.println("hindi text enter then save button clicked");
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					//  Chinese languages testing for  testing

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println(" edit button");

				  	  	  	  	    																								    					// title text button click and clear then enter new text
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).sendKeys("已经完成了对Lok Sabha选举四个阶段的投票。现在转弯是最后政治法庭上也有重要的一");

				  	  	  	  	    																								    					// Message title edit text in hindi
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_second']")).clear();
				  	  	  	  	    																								    					//clear text in title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_second']")).sendKeys("三个步骤。今天有许多退伍军人的选举会议，包括总理纳伦德拉莫迪，国会主席拉胡尔甘地和人民党总统阿米特沙阿。因此，今天在最高法院的");
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("title text enter in chinese language");
				  	  	  	  	    																								    					// click and clear radio button 1 and enter chinese text

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_second']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_second']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_second']")).sendKeys("伍军人的选举会议，包括总理纳伦德拉莫迪，");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in hindi language and click and clear radio button 1 and enter hind text");
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// click and clear radio button 2 and enter chinese text
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(8) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_second']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_second']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_second']")).sendKeys("的选举会议，包括总理纳伦德拉莫迪，");
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[onclick='savemeall\\(this\\, \\'second\\'\\,2\\,\\'desktop\\'\\)\\;']")).click();	
				  	  	  	  	    																								    					System.out.println("chinese text enter then save button clicked");
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// close Chinese languages test cases
				  	  	  	  	    																								    					  

				  	  	  	  	    																								    					// Message text clear and enter in hind language for 







				  	  	  	  	    																								    					    // all full screen pop up testing  now
				  	  	  	  	    																								    					//Test case for full screen pop up

				  	  	  	  	    																								    					// click on setting page
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//a[@id='settingsA']/span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    					//setting page clicked
				  	  	  	  	    																								    					// click optin page

				  	  	  	  	    																								    					// open optin page
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					Thread.sleep(5000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//a[@id='multi-optin']")).click();

				  	  	  	  	    																								    					//optin page open here
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move full screen modal page ");
				  	  	  	  	    																								    					// click on  prompt to edit page
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[4]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("clicked on full screen pop up prompt for subscription page");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// click sava and activate button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[9]/div[@role='document']//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("save button clicked for postive test case");

				  	  	  	  	    																								    					// negative test case for full screen pop up

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[4]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("full screen modal edit button");

				  	  	  	  	    																								    					// title text button click and clear then enter new text
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_third']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_third']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_third']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_third']")).sendKeys("已经完成了对Lok Sabha选举四个阶段的投票。现在转弯是最后政治法庭上也有重要的一");

				  	  	  	  	    																								    					// Message title edit text in chinese
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_third']")).clear();
				  	  	  	  	    																								    					//clear text in title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_third']")).sendKeys("三个步骤。今天有许多退伍军人的选举会议，包括总理纳伦德拉莫迪，国会主席拉胡尔甘地和人民党总统阿米特沙阿。因此，今天在最高法院的");
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("title text enter in chinese language");
				  	  	  	  	    																								    					// click and clear radio button 1 and enter Chinese text

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(9) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_third']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_third']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_third']")).sendKeys("伍军人的选举会议，包括总理纳伦德拉莫迪，");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in hindi language and click and clear radio button 1 and enter hind text");
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// click and clear radio button 2 and enter chinese text
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(9) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_third']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_third']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_third']")).sendKeys("的选举会议，包括总理纳伦德拉莫迪，");
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[9]/div[@role='document']//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("save button clicked for negative test case for full pop up test case");

				  	  	  	  	    																								    					// full screen pop up test case for another langauge(URDU)


				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[4]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("full screen modal edit button");

				  	  	  	  	    																								    					// title text button click and clear then enter new text
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_third']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_third']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_third']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_third']")).sendKeys("غاندي ورئيس حزب بهاراتيا جاناتا أميت شاه. إذن هناك يوم كبير في المحكمة السياسية اليوم في المحكمة العليا. من ناحية ، ");

				  	  	  	  	    																								    					// Message title edit text in chinese
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_third']")).clear();
				  	  	  	  	    																								    					//clear text in title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_third']")).sendKeys("غاندي ورئيس حزب بهاراتيا جاناتا أميت شاه. إذن هناك يوم كبير في المحكمة السياسية اليوم في المحكمة العليا. من ناحية ، غاندي ورئيس حزب بهاراتيا جاناتا أميت شاه. إذن هناك يوم كبير في المحكمة السياسية اليوم في المحكمة العليا. من ناحية ، ");
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("title text enter in URDU language");
				  	  	  	  	    																								    					// click and clear radio button 1 and enter Chinese text

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(9) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_third']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_third']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_third']")).sendKeys(" الأخيرة. توجد اليوم اجتماعات انتخابية للعديد من المحاربين القدامى بمن فيهم رئيس الوزراء ناريندرا مودي ورئيس المؤتمر راهول غاندي ورئيس حزب بهاراتيا جاناتا أميت شاه. إذن هناك يوم كبير في المحكمة السياسية اليوم في المحكمة العليا. من ناحية ، كان على مودي شاه أن يسمع مدونة قواعد السلوك ، والتي ستستمر حتى يوم الجمعة.");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in URDU  language and click and clear radio button 1 and enter hind text");
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// click and clear radio button 2 and enter chinese text
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(9) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_third']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_third']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_third']")).sendKeys(" الأخيرة. توجد اليوم اجتماعات انتخابية للعديد من المحاربين القدامى بمن فيهم رئيس الوزراء ناريندرا مودي ورئيس المؤتمر راهول غاندي ورئيس حزب بهاراتيا جاناتا أميت شاه. إذن هناك يوم كبير في المحكمة السياسية اليوم في المحكمة العليا. من ناحية ، كان على مودي شاه أن يسمع مدونة قواعد السلوك ، والتي ستستمر حتى يوم الجمعة.");
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[9]/div[@role='document']//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("save button clicked for negative test case for full pop up test case");

				  	  	  	  	    																								    					// END full screen pop up test case for another language URDU

				  	  	  	  	    																								    					// FULL SCREEN TESTING for another langauses(TAMil text) with color changes

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[4]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("full screen modal edit button");

				  	  	  	  	    																								    					// title text button click and clear then enter new text
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_third']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_third']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_third']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_third']")).sendKeys("غ\r\n" + 
				  	  	  	  	    																								    					"லோக்சபா தேர்தலில் நான்கு கட்டங்களாக தேர்தல் முடிந்துவிட்டது. இப்போது மூன்று கடைசி படிகள் உள்ளன. இன்று பிரதம மந்திரி நரேந்திர மோடி, காங்கிரஸ் தலைவர் ராகுல் காந்தி மற்றும் பாரதீய ஜனதா தலைவர் அமித் ஷா உள்ளிட்ட பல்வேறு வீரர்களின் ");

				  	  	  	  	    																								    					// Message title edit text in chinese
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//textarea[@id='optin_title_second']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_third']")).clear();
				  	  	  	  	    																								    					//clear text in title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_third']")).sendKeys("غاندي ي மந்திரி நரேந்திர மோடி, காங்கிரஸ் தலைவர் ராகுல் காந்தி மற்றும் பாரதீய ஜனதா தலைவர் அமித் ஷா உள்ளிட்ட பல்வேறு வீரர் ، ");
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("title text enter in URDU language");
				  	  	  	  	    																								    					// click and clear radio button 1 and enter Chinese text

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(9) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_third']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_third']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_third']")).sendKeys("ர மோடி, காங்கிரஸ் தலைவர் ராகுல் معة.");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in URDU  language and click and clear radio button 1 and enter hind text");
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// click and clear radio button 2 and enter chinese text
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(9) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_third']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_third']")).clear();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_third']")).sendKeys("ர மோடி, காங்கிரஸ் தலைவர் ராகுல் م الجمعة.");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in tamil  language and click and clear radio button two and enter tamil text");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[9]/div[@role='document']//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("save button clicked for negative test case for full pop up test tamil text case");



				  	  	  	  	    																								    					// END FULL SCREEN TESTING WITH COLOR
				  	  	  	  	    																								    					   //test done full screen 
				  	  	  	  	    																								    					// end full screen pop up




				  	  	  	  	    																								    					//Test case for Right side bar subscription prompt

				  	  	  	  	    																								    					//driver.navigate().refresh();
				  	  	  	  	    																								    					// setting page click
				  	  	  	  	    																								    					Thread.sleep(5000);	
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//a[@id='settingsA']/span[@class='sidebar-title']")).click();
				  	  	  	  	    																								    					// setting page
				  	  	  	  	    																								    					// multi optin page
				  	  	  	  	    																								    					Thread.sleep(5000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//a[@id='multi-optin']")).click();
				  	  	  	  	    																								    					// multi optin here
				  	  	  	  	    																								    					Thread.sleep(5000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[5]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move to full screen modal page ");
				  	  	  	  	    																								    					// click on  prompt
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("clicked on right side bar prompt for subscription page");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// click sava and activate button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// negative test cases for right side bar


				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[5]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("right side bar modal edit button");

				  	  	  	  	    																								    					// title text button click and clear then enter new text
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fourth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fourth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fourth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fourth']")).sendKeys("已经完成了对Lok Sabha选举四个阶段的投票。现在转弯是最后政治法庭上也有重要的一");

				  	  	  	  	    																								    					// Message title edit text in chinese
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fourth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fourth']")).clear();
				  	  	  	  	    																								    					//clear text in title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fourth']")).sendKeys("三个步骤。今天有许多退伍军人的选举会议，包括总理纳伦德拉莫迪，国会主席拉胡尔甘地和人民党总统阿米特沙阿。因此，今天在最高法院的");
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("title text enter in chinese language");
				  	  	  	  	    																								    					// click and clear radio button 1 and enter Chinese text

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(10) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fourth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fourth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fourth']")).sendKeys("伍军人的选举会议，包括总理纳伦德拉莫迪，");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in hindi language and click and clear radio button 1 and enter hind text");
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// click and clear radio button 2 and enter chinese text
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(10) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fourth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fourth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fourth']")).sendKeys("的选举会议，包括总理纳伦德拉莫迪，");
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("save button clicked for negative test case for right side bar chinese lanhuage");

				  	  	  	  	    																								    					//test complete here
				  	  	  	  	    																								    					// new test cases for right side bar subscription prompt Japanese language

				  	  	  	  	    																								    					// multi optin page
				  	  	  	  	    																								    					Thread.sleep(5000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//a[@id='multi-optin']")).click();
				  	  	  	  	    																								    					// multi optin here
				  	  	  	  	    																								    					Thread.sleep(5000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[5]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move to full screen modal page ");
				  	  	  	  	    																								    					// click on  prompt
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("clicked on right side bar prompt for subscription page");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// click sava and activate button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// negative test cases for right side bar


				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[5]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("right side bar modal edit button");

				  	  	  	  	    																								    					// title text button click and clear then enter new text
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fourth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fourth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fourth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fourth']")).sendKeys("どの機能が各言語で機能するかを確認してください");

				  	  	  	  	    																								    					// Message title edit text in chinese
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fourth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fourth']")).clear();
				  	  	  	  	    																								    					//clear text in title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fourth']")).sendKeys("どの機能が各言語で機能するかを確認してくださいどの機能が各言語で機能するかを確認してください");
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("title text enter in chinese language");
				  	  	  	  	    																								    					// click and clear radio button 1 and enter Chinese text

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(10) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fourth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fourth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fourth']")).sendKeys("各言語で機能するかを確認してください");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in hindi language and click and clear radio button 1 and enter hind text");
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// click and clear radio button 2 and enter chinese text
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(10) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fourth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fourth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fourth']")).sendKeys("言語で機能するかを確認してください");
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("save button clicked for negative test case for right side bar japanes lanhuage");

				  	  	  	  	    																								    					// test case for hind language

				  	  	  	  	    																								    					// multi optin page
				  	  	  	  	    																								    					Thread.sleep(5000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//a[@id='multi-optin']")).click();
				  	  	  	  	    																								    					// multi optin here
				  	  	  	  	    																								    					Thread.sleep(5000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[5]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move to full screen modal page ");
				  	  	  	  	    																								    					// click on  prompt
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("clicked on right side bar prompt for subscription page");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// click sava and activate button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// negative test cases for right side bar


				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[5]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("right side bar modal edit button");

				  	  	  	  	    																								    					// title text button click and clear then enter new text
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fourth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fourth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fourth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fourth']")).sendKeys("अधिक भाषाओं को समझने और संवाद करने में मदद करता है। देखें कि प्रत्येक भाषा के साथ कौन सी सुविधाएँ काम ");

				  	  	  	  	    																								    					// Message title edit text in chinese
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fourth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fourth']")).clear();
				  	  	  	  	    																								    					//clear text in title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fourth']")).sendKeys("भाषाओं को समझने और संवाद करने में मदद करता है। देखें कि प्रत्येक भाषा के साथ कौन सी सुविधाएँ काम ");
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("title text enter in chinese language");
				  	  	  	  	    																								    					// click and clear radio button 1 and enter Chinese text

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(10) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fourth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fourth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fourth']")).sendKeys("संवाद करने में मदद करता है। देखें कि प्रत्येक काम ");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in hindi language and click and clear radio button 1 and enter hindi text");
				  	  	  	  	    																								    					// color selecting radio button one
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//div[@class='customization-body scrollbar']//div[@class='radio-button2']//input[@value='#df3528']")).click();

				  	  	  	  	    																								    					// color selected
				  	  	  	  	    																								    					//Thread.sleep(3000);
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//div[@class='customization-body scrollbar']//div[@class='radio-button2']/div[2]/div/div[@class='minicolors-panel minicolors-slider-hue']/div[@class='minicolors-grid minicolors-sprite']/div[@class='minicolors-picker']/div")).click();
				  	  	  	  	    																								    					//Thread.sleep(2000);
				  	  	  	  	    																								    					// click on color selection here

				  	  	  	  	    																								    					// selected color test
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// click and clear radio button 2 and enter chinese text
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(10) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fourth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fourth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fourth']")).sendKeys("कौन सी सुविधाएँ काम い");
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("save button clicked for negative test case for right side bar hind  lanhuage");


				  	  	  	  	    																								    					// test case hindi language complete here


				  	  	  	  	    																								    					// new test complete
				  	  	  	  	    																								    					// right side bar	



				  	  	  	  	    																								    					// Test case for Sticky header

				  	  	  	  	    																								    					//driver.navigate().refresh();


				  	  	  	  	    																								    					//Test case 1--click on subscription prompt tab then dailog box testing
				  	  	  	  	    																								    					 	driver1111.findElement(By.xpath("/html//a[@id='multi-optin']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move on subscription page");


				  	  	  	  	    																								    					// click on dailog box prompt
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[2]/div/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("clicked on dailog box subscription page");
				  	  	  	  	    																								    					Thread.sleep(2000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']/div[@class='widget-body']/div/div[6]/div[2]/div")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move to full screen modal page ");
				  	  	  	  	    																								    					// click on  prompt
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("clicked on sticky header prompt for subscription page");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// click save and activate button

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[11]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// negative test cases for

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']/div[@class='widget-body']/div/div[6]/div[2]/div")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("sticky header modal edit button");

				  	  	  	  	    																								    					// title text button click and clear then enter new text
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fifth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fifth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fifth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fifth']")).sendKeys("अधिक भाषाओं को समझने और संवाद करने में मदद करता है। देखें कि प्रत्येक भाषा के साथ कौन सी सुविधाएँ काम ");

				  	  	  	  	    																								    					// Message title edit text in chinese
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fifth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fifth']")).clear();
				  	  	  	  	    																								    					//clear text in title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fifth']")).sendKeys("भाषाओं को समझने और संवाद करने में मदद करता है। देखें कि प्रत्येक भाषा के साथ कौन सी सुविधाएँ काम ");
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("title text enter in hind for sticky headr language");
				  	  	  	  	    																								    					// click and clear radio button 1 and enter Chinese text

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(11) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fifth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fifth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fifth']")).sendKeys("संवाद करने में मदद करता है। देखें कि प्रत्येक काम ");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in hindi language and click and clear radio button 1 and enter hindi text");
				  	  	  	  	    																								    					// color selecting radio button one
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//div[@class='customization-body scrollbar']//div[@class='radio-button2']//input[@value='#df3528']")).click();

				  	  	  	  	    																								    					// color selected
				  	  	  	  	    																								    					//Thread.sleep(3000);
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//div[@class='customization-body scrollbar']//div[@class='radio-button2']/div[2]/div/div[@class='minicolors-panel minicolors-slider-hue']/div[@class='minicolors-grid minicolors-sprite']/div[@class='minicolors-picker']/div")).click();
				  	  	  	  	    																								    					//Thread.sleep(2000);
				  	  	  	  	    																								    					// click on color selection here

				  	  	  	  	    																								    					// selected color test
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// click and clear radio button 2 and enter chinese text
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(11) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fifth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fifth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fifth']")).sendKeys("कौन सी सुविधाएँ काम い");
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[11]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("save button clicked for negative test case for sticky bar bar hind  lanhuage");

				  	  	  	  	    																								    					// test sticky bar for panjabi language

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']/div[@class='widget-body']/div/div[6]/div[2]/div")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("sticky header modal edit button");

				  	  	  	  	    																								    					// title text button click and clear then enter new text
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fifth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fifth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fifth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_fifth']")).sendKeys("ਤੋਂ ਵੱਧ ਭਾਸ਼ਾਵਾਂ ਵਿੱਚ ਤੁਹਾਨੂੰ ਸਮਝਣ ਅਤੇ ਸੰਚਾਰ ਕਰਨ ਵਿੱਚ ਮਦਦ ਕਰਦਾ ਹੈ. ਇਹ ਦੇਖੋ ਕਿ ਹਰੇਕ ਸਲੇਗ ਨਾਲ ਕਿਹੜੀਆਂ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ");

				  	  	  	  	    																								    					// Message title edit text in chinese
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fifth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fifth']")).clear();
				  	  	  	  	    																								    					//clear text in title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_fifth']")).sendKeys("ਤਧ ਭਾਸ਼ਾਵਾਂ ਵਿੱਚ ਤੁਹਾਨੂੰ ਸਮਝਣ ਅਤੇ ਸੰਚਾਰ ਕਰਨ ਵਿੱਚ ਮਦਦ ਕਰਦਾ ਹੈ. ਇਹ ਦੇਖੋ ਕਿ ਹਰੇਕ ਸਲੇਗ ਨਾਲ ਕਿਹੜੀਆਂ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ  ");
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("title text enter in hind for sticky headr language");
				  	  	  	  	    																								    					// click and clear radio button 1 and enter Chinese text

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(11) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fifth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fifth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_fifth']")).sendKeys("ਹੈ. ਇਹ ਦੇਖੋ ਕਿ ਹਰੇਕ ਸਲੇਗ ਨਾਲ ਕਿਹੜੀਆਂ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ  ");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in hindi language and click and clear radio button 1 and enter hindi text");
				  	  	  	  	    																								    					// color selecting radio button one
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//div[@class='customization-body scrollbar']//div[@class='radio-button2']//input[@value='#df3528']")).click();

				  	  	  	  	    																								    					// color selected
				  	  	  	  	    																								    					//Thread.sleep(3000);
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//div[@class='customization-body scrollbar']//div[@class='radio-button2']/div[2]/div/div[@class='minicolors-panel minicolors-slider-hue']/div[@class='minicolors-grid minicolors-sprite']/div[@class='minicolors-picker']/div")).click();
				  	  	  	  	    																								    					//Thread.sleep(2000);
				  	  	  	  	    																								    					// click on color selection here

				  	  	  	  	    																								    					// selected color test
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// click and clear radio button 2 and enter punjabi text
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(11) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fifth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fifth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_fifth']")).sendKeys("ਤੋਂ ਵੱਧ ਭਾਸ਼ਾਵਾਂ ਵਿੱਚ ਤੁਹਾਨੂੰ ਸਮਝਣ ਅੜੀਆਂ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ");
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[11]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("save button clicked for negative test case for sticky bar bar punjabi  lanhuage");

				  	  	  	  	    																								    					// full panjabi language for sticky bar
				  	  	  	  	    																								    					// done sticky bar testing



				  	  	  	  	    																								    					// all negative test case for sticky header

				  	  	  	  	    																								    					// Test case for slide up box for desktop

				  	  	  	  	    																								    					//driver.navigate().refresh();
				  	  	  	  	    																								    					// click on multioptin page
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//a[@id='multi-optin']")).click();
				  	  	  	  	    																								    					               // click to edit slide up box
				  	  	  	  	    																								    					            driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[7]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					            // clicked slide up box
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					Thread.sleep(5000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[12]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move to slide up box modal page ");
				  	  	  	  	    																								    					// click sava and activate button
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[12]//button[@type='button']")).click();


				  	  	  	  	    																								    					// text enter in slide up box


				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']/div[@class='widget-body']/div/div[7]/div[2]/div")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("sticky header modal edit button");

				  	  	  	  	    																								    					// title text button click and clear then enter new text
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_sixth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_sixth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_sixth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_sixth']")).sendKeys("วยให้คุณเข้าใจและสื่อสารได้มากกว่า 100 ภาษา ดูว่าฟีเจอร์ใดทำงานได้กับแต่ละภ ");

				  	  	  	  	    																								    					// Message title edit text in chinese
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_sixth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_sixth']")).clear();
				  	  	  	  	    																								    					//clear text in title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_sixth']")).sendKeys("วให้คุณเข้าใจและสื่อสารได้มากกว่า 100 ภาษา ดูว่าฟีเจอร์ใดทำงานได้กับแต่ละภ");
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("title text enter in hind for sticky headr language");
				  	  	  	  	    																								    					// click and clear radio button 1 and enter Chinese text

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(12) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_sixth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_sixth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_sixth']")).sendKeys("วยให้คุณเข้าใจและสื่อสารได้มากกว่า 100 ภาษา ดูว่าฟีเจอร์ใดทำงานได้กับแต่ละภ  ");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in punjabi in slide up box language and click and clear radio button 1 and enter hindi text");
				  	  	  	  	    																								    					// color selecting radio button one
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//div[@class='customization-body scrollbar']//div[@class='radio-button2']//input[@value='#df3528']")).click();

				  	  	  	  	    																								    					// color selected
				  	  	  	  	    																								    					//Thread.sleep(3000);
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//div[@class='customization-body scrollbar']//div[@class='radio-button2']/div[2]/div/div[@class='minicolors-panel minicolors-slider-hue']/div[@class='minicolors-grid minicolors-sprite']/div[@class='minicolors-picker']/div")).click();
				  	  	  	  	    																								    					//Thread.sleep(2000);
				  	  	  	  	    																								    					// click on color selection here

				  	  	  	  	    																								    					// selected color test
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// click and clear radio button 2 and enter punjabi text
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(12) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_sixth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_sixth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_sixth']")).sendKeys("วยให้คุณเข้าใจและสื่อสารได้มากกว่า 100 ภาษา ดูว่าฟีเจอร์ใดทำงานได้กับแต่ละภ ");
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[12]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("save button clicked for negative test case for slide up box bar punjabi  lanhuage");

				  	  	  	  	    																								    					// slide up box language test here

				  	  	  	  	    																								    					// click to edit slide up box
				  	  	  	  	    																								    					            driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[7]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					            // clicked slide up box
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					Thread.sleep(5000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[12]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move to slide up box modal page ");
				  	  	  	  	    																								    					// click sava and activate button
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[12]//button[@type='button']")).click();


				  	  	  	  	    																								    					// text enter in slide up box


				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']/div[@class='widget-body']/div/div[7]/div[2]/div")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("sticky header modal edit button");

				  	  	  	  	    																								    					// title text button click and clear then enter new text
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_sixth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_sixth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_sixth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_title_sixth']")).sendKeys("ਤੋਂ ਵੱਧ ਭਾਸ਼ਾਵਾਂ ਵਿੱਚ ਤੁਹਾਨੂੰ ਸਮਝਣ ਅਤੇ ਸੰਚਾਰ ਕਰਨ ਵਿੱਚ ਮਦਦ ਕਰਦਾ ਹੈ. ਇਹ ਦੇਖੋ ਕਿ ਹਰੇਕ ਸਲੇਗ ਨਾਲ ਕਿਹੜੀਆਂ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ");

				  	  	  	  	    																								    					// Message title edit text in chinese
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_sixth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_sixth']")).clear();
				  	  	  	  	    																								    					//clear text in title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//textarea[@id='optin_subtitle_sixth']")).sendKeys("วยให้คุณเข้าใจและสื่อสารได้มากกว่า 100 ภาษา ดูว่าฟีเจอร์ใดทำงานได้กับแต่ละภ  ");
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("title text enter in hind for sticky headr language");
				  	  	  	  	    																								    					// click and clear radio button 1 and enter Chinese text

				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(12) .checkbox-inline:nth-of-type(2) .radio-btn")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_sixth']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_sixth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_allow_btn_sixth']")).sendKeys("วยให้คุณเข้าใจและสื่อสารได้มากกว่า 100 ภาษา ดูว่าฟีเจอร์ใดทำงานได้กับแต่ละภ  ");
				  	  	  	  	    																								    					System.out.println(" allow button text entered in punjabi in slide up box language and click and clear radio button 1 and enter hindi text");
				  	  	  	  	    																								    					// color selecting radio button one
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//div[@class='customization-body scrollbar']//div[@class='radio-button2']//input[@value='#df3528']")).click();

				  	  	  	  	    																								    					// color selected
				  	  	  	  	    																								    					//Thread.sleep(3000);
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[10]//div[@class='customization-body scrollbar']//div[@class='radio-button2']/div[2]/div/div[@class='minicolors-panel minicolors-slider-hue']/div[@class='minicolors-grid minicolors-sprite']/div[@class='minicolors-picker']/div")).click();
				  	  	  	  	    																								    					//Thread.sleep(2000);
				  	  	  	  	    																								    					// click on color selection here

				  	  	  	  	    																								    					// selected color test
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// click and clear radio button 2 and enter punjabi text
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector("[data-backdrop='static']:nth-of-type(12) .checkbox-inline:nth-of-type(3) .radio-btn")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_sixth']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_sixth']")).clear();
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//input[@id='optin_disallow_btn_sixth']")).sendKeys("วยให้คุณเข้าใจและสื่อสารได้มากกว่า 100 ภาษา ดูว่าฟีเจอร์ใดทำงานได้กับแต่ละภ ");
				  	  	  	  	    																								    					// save button clicked
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[12]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("save button clicked for negative test case for slide up box bar punjabi  lanhuage");


				  	  	  	  	    																								    					// slide up langage now

				  	  	  	  	    																								    					// Testing done slide up box testing


				  	  	  	  	    																								    					// Test case for bell


				  	  	  	  	    																								    					  Thread.sleep(5000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[8]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move to slide up box modal page ");
				  	  	  	  	    																								    					// click on  prompt
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("clicked on slide up box prompt for subscription page");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// click sava and activate button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[13]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// test case 2 for bell


				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[8]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move to slide up box modal page ");
				  	  	  	  	    																								    					// click on  prompt
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//div[@id='izooto_position_seventh']/label[.='Left']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("clicked on slide up box prompt for subscription page");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// click sava and activate button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[13]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);



				  	  	  	  	    																								    					// bell test case 2

				  	  	  	  	    																								    					// Test case for Sticky bar

				  	  	  	  	    																								    					//driver.navigate().refresh();
				  	  	  	  	    																								    					Thread.sleep(5000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[9]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move to sticky bar box modal page ");
				  	  	  	  	    																								    					// click on  prompt
				  	  	  	  	    																								    					//driver.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println(" stick bar prompt for subscription page");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// click sava and activate button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[14]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);


				  	  	  	  	    																								    					// Test case 2 for Sticky bar

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[9]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move to sticky bar box modal page ");
				  	  	  	  	    																								    					//test button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='izooto_position_eighth']/label[.='Left']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println(" stick bar prompt for subscription page");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					// click sava and activate button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[14]//button[@type='button']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// Test case 2 closed for Sticky bar

				  	  	  	  	    																								    					// Test casr for Prompt user after spending   seconds on the website
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//select[@id='first_trigger']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//select[@id='first_trigger']")).sendKeys("5");
				  	  	  	  	    																								    					System.out.println("Value selected 5 seconds");
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// test case for Prompt user again after every 2 or 5  minutes if there is no interaction with the subscription prompt 

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//select[@id='seconds_trigger']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//select[@id='seconds_trigger']")).sendKeys("7");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("Value selected 7 seconds");
				  	  	  	  	    																								    					// test case for Prompt user after  1 or 2 hour of clicking on the 'later' CTA 

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//select[@id='seconds_trigger_later']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//select[@id='seconds_trigger_later']")).sendKeys("3");
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					System.out.println("Value selected 3 seconds");
				  	  	  	  	    																								    					// click save button to apply delay 
				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[3]//div[@class='col-md-12']//center/a[1]")).click();
				  	  	  	  	    																								    					System.out.println("delay after save button has been set"); 



				  	  	  	  	    																								    					// Test case for Mobile Subscription Prompts  dialog box normal no negative test cases

				  	  	  	  	    																								    					//  all subscription prompt comment


				  	  	  	  	    																								    					Thread.sleep(3000);
				  	  	  	  	    																								    					driver1111.navigate().refresh();
				  	  	  	  	    																								    					//Thread.sleep(5000);

				  	  	  	  	    																								    					// click on multi optin page to agian click
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//a[@id='multi-optin']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("move on su bscription page for mobile test");

				  	  	  	  	    																								    					// click
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[2]//div[@class='row']/div[2]/div/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt for dailog box ");

				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//Save button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[18]//button[@type='button']")).click();

				  	  	  	  	    																								    					// Test case for Mobile Subscription Prompts 

				  	  	  	  	    																								    					Thread.sleep(5000);	

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[2]//div[@class='row']/div[3]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt for  normal test case");

				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//Save button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[19]//button[@type='button']")).click();
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt for ");
				  	  	  	  	    																								    					// Test case for Mobile Subscription Prompts full pop up screen

				  	  	  	  	    																								    					Thread.sleep(5000);	

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[2]//div[@class='row']/div[4]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt forfull pop up test case");

				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//Save button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[20]//button[@type='button']")).click();
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt for full screen pop up");
				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					// Test case for Mobile Subscription Prompts Sticky header

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[2]//div[@class='row']/div[6]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt for sticky headernormal test case");

				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//Save button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[22]//button[@type='button']")).click();
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt for Sticky header");
				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					// Test case for Mobile Subscription Prompts Slide up box

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[2]//div[@class='row']/div[7]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt for sticky headernormal test case");

				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//Save button
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[23]//button[@type='button']")).click();
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt for Slide up bob");
				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					// Test case for Mobile Subscription Prompts Bell
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[2]//div[@class='row']/div[8]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt for Bell  test case");

				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					//Save and active button  clicked
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[24]//button[@type='button']")).click();
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt for bell");
				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					// Test case for Mobile Subscription Prompts Sticky bar



				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='optimizer']//div[@class='row']/div[9]/div[2]/div/button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt for Sticky bar  test case");

				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//div[@id='izooto_position_eighth']/label[.='Left']")).click();	
				  	  	  	  	    																								    					//Save and active button  clicked
				  	  	  	  	    																								    					Thread.sleep(3000);	
//				  	  	  	  	    																								    						driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[25]//button[@type='button']")).click();
				  	  	  	  	    																								    					driver1111.findElement(By.cssSelector(".design8-izooto .optin-bottom-btn button.btn.btn-primary.btn-raised")).click();
				  	  	  	  	    																								    					Thread.sleep(3000);	
				  	  	  	  	    																								    					System.out.println("Mobile subscription prompt for Sticky bar");
				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					// Test for Enforce native subscription prompt on Chrome v61 & below, Firefox browsers. Know More.

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//div[@id='forceNative']/div[@class='row']/div/div[@class='frmtng_brdr_iz mb-20']//span[@class='switch2-label']")).click();	
				  	  	  	  	    																								    					Thread.sleep(3000);

				  	  	  	  	    																								    					// Test for disabled Enforce native subscription prompt on Chrome v61 & below, Firefox browsers. Know More
				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//div[@id='forceNative']/div[@class='row']/div/div[@class='frmtng_brdr_iz mb-20']//span[@class='switch2-label']")).click();	

				  	  	  	  	    																								    					//comment for disabled multiopin desktop and mobile 

				  	  	  	  	    																								    					// Test case for Enable GDPR Compliant Subscription
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[4]//div[@class='col-md-12']//div[@class='panel panel-default']//span[@class='switch2-label']")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					System.out.println(" Clicked on GDPR TAB");

				  	  	  	  	    																								    					// Test case for Disabled GDPR Compliant Subscription
				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[4]//div[@class='col-md-12']//div[@class='panel panel-default']//span[@class='switch2-label']")).click();
				  	  	  	  	    																								    					//Thread.sleep(4000);

				  	  	  	  	    																								    					System.out.println(" Clicked on  disabled GDPR TAB");
				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					//  click to enabled agian gdpr

				  	  	  	  	    																								    					//driver.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[4]//div[@class='col-md-12']//div[@class='panel panel-default']//span[@class='switch2-label']")).click();
				  	  	  	  	    																								    					//Thread.sleep(4000);

				  	  	  	  	    																								    					System.out.println(" Clicked on  enable agian GDPR TAB");
				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					// Sticky header for GDPR  CLICK EDIT 

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//div[@id='gdpr-body']/div[1]//button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					// CLICK FOR SAVE AND ACTIVATE

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//button[@id='first_gdpr_save']")).click();
				  	  	  	  	    																								    					System.out.println(" Clicked and save sticky header prompt for gdpr");
				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					// Test case for gdpr , sticky footer

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//div[@id='gdpr-body']/div[2]//button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					// CLICK FOR SAVE AND ACTIVATE

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[16]//button[@type='button']")).click();
				  	  	  	  	    																								    					System.out.println(" Clicked and save sticky footer prompt for gdpr");
				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					// Test case for gdpr ,   


				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//div[@id='gdpr-body']/div[3]//button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);
				  	  	  	  	    																								    					// CLICK FOR SAVE AND ACTIVATE

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//body/section[@class='page-container']/div[2]/div[26]//button[@type='button']")).click();
				  	  	  	  	    																								    					System.out.println(" Clicked and save sticky footer prompt for gdpr");
				  	  	  	  	    																								    					Thread.sleep(5000);


				  	  	  	  	    																								    					// Sticky header for GDPR  CLICK EDIT negative test cases

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//div[@id='gdpr-body']/div[1]//button[.='Edit']")).click();
				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					//  click pencil edit text title
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//div[@id='izooto_title_gdpr_first']/i[@class='fa fa-pencil fs-14']")).click();
				  	  	  	  	    																								    					Thread.sleep(2000);

				  	  	  	  	    																								    					// click on pencil to edit agree
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//p[@id='izooto_allow_button_gdpr_first']/i[@class='fa fa-pencil fs-14']")).click();
				  	  	  	  	    																								    					// click on pencil to not now
				  	  	  	  	    																								    					driver1111.findElement(By.xpath("//p[@id='izooto_disallow_button_gdpr_first']/i[@class='fa fa-pencil fs-14']")).click();
				  	  	  	  	    																								    					// clear title text

				  	  	  	  	    																								    					//driver.findElement(By.xpath("//div[@id='izooto_title_gdpr_first']/i[@class='fa fa-pencil fs-14']")).clear();

				  	  	  	  	    																								    					Thread.sleep(5000);

				  	  	  	  	    																								    					// CLICK FOR SAVE AND ACTIVATE

				  	  	  	  	    																								    					driver1111.findElement(By.xpath("/html//button[@id='first_gdpr_save']")).click();
				  	  	  	  	    																								    					System.out.println(" negative test case Clicked and save sticky header prompt for gdpr");
				  	  	  	  	    																								    					Thread.sleep(4000);

				  	  	  	  	    																								    			
				  	  	  	  	    																								    			
				  	  	  	  	    																								    			
				  	  	  	  	    																								    			
				  	  	  	  	    																								    			  

				  	  	  	  	    																													



		  
				  	  	  	  	    						         
		    
		}

	private static void assertclickhere() {
		// TODO Auto-generated method stub
	
		
		
		
		
		
		
		
		
		
		
		
		
		
	}

}
