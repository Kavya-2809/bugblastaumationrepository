package com.bugblast.core;

import java.time.Duration;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.openqa.selenium.edge.EdgeDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.AfterMethod;
import org.testng.annotations.BeforeMethod;
import com.bugblast.config.ConfigReader;

public class BaseTest {
	
   protected WebDriver driver;

	    @BeforeMethod
	    public void setUp() {
	        String browser = ConfigReader.getProperty("browser").toLowerCase();

	        switch (browser) {
	            case "chrome":
	                ChromeOptions options = new ChromeOptions();
	                options.addArguments("--start-maximized");
	                driver = new ChromeDriver(options);
	                break;
	            case "firefox":
	                driver = new FirefoxDriver();
	                driver.manage().window().maximize();
	                break;
	            case "edge":
	                driver = new EdgeDriver();
	                driver.manage().window().maximize();
	                break;
	            default:
	                throw new RuntimeException("Browser not supported: " + browser);
	        }

	        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
	        driver.get(ConfigReader.getProperty("baseUrl"));
	    }

	    @AfterMethod
	    public void tearDown() {
	        if (driver != null) {
	            driver.quit();
	        }
	    }
}


