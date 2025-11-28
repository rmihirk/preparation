<em>

# Selenium Learning Guide

## Q.1 Automation Testing Basics
### What is Automation Testing?
Automation testing is a process of automating manual testing to test an application/system. It uses testing tools to create reusable test scripts that can be executed repeatedly without manual intervention.

### Framework Definition
A framework is a constructive blend of guidelines, coding standards, concepts, processes, practices, hierarchies, modularity, and reporting mechanisms that support automation testing.

### Advantages of Automation Framework
- Reusability of code
- Maximum coverage
- Recovery scenarios
- Low-cost maintenance
- Minimal manual intervention
- Easy reporting

### Benefits of Automation Testing
- Supports execution of repeated test cases
- Enables testing of large test matrices
- Enables parallel execution
- Encourages unattended execution
- Improves accuracy and reduces human-generated errors
- Saves time and money

## Q.2 Selenium Overview
### Why Choose Selenium?
- Free and open source
- Large user base and support communities
- Cross-browser compatibility (Firefox, Chrome, Internet Explorer, Safari)
- Cross-platform compatibility (Windows, macOS, Linux)
- Supports multiple programming languages (Java, C#, Ruby, Python, Perl)
- Regular repository updates
- Supports distributed testing

### Selenium Components
1. **Selenium IDE**: Record and playback tool (Firefox Plugin)
2. **Selenium RC**: Server allowing test scripts in desired language
3. **Selenium WebDriver**: Direct browser communication with native automation
4. **Selenium Grid**: Distributed test execution across platforms

### Selenium Versions
- **Selenium 1**: Selenium RC alone
- **Selenium 2**: Selenium RC + WebDriver combination
- **Selenium 3**: Improved WebDriver and support for modern browsers
- **Selenium 4**: Introduced W3C WebDriver standard, new features like relative locators, and enhanced support for modern web applications

### Limitations of Selenium
- Web-based applications only
- No mobile application testing (use Appium for mobile)
- Cannot test CAPTCHAs or Barcode readers
- Reports require third-party tools (TestNG, JUnit)
- Requires programming language knowledge
- Community support only (no vendor support)

### Supported Testing Types
- Functional testing
- Regression testing

## Q.3 Locators
### Types of Locators
- ID
- ClassName
- Name
- TagName
- LinkText
- PartialLinkText
- XPath
- CSS Selector
- DOM

### XPath Syntax
- **Single Slash (`/`)**: Absolute path from document root
- **Double Slash (`//`)**: Relative path from anywhere in document

## Q.4 Assertions vs Verification
| Feature | Assert | Verify |
|---------|--------|--------|
| Behavior | Stops execution on failure | Continues execution |
| Condition Check | True or False | True or False |
| Use Case | Critical validations | Non-critical checks |

## Q.5 Waits
### Implicit Wait
Tells WebDriver to wait a specified time before throwing `NoSuchElementException`.
```java
driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
```

### Explicit Wait
Waits for specific conditions with intelligent waiting for dynamic AJAX elements.
```java
WebDriverWait wait = new WebDriverWait(driver, timeOut);
wait.until(ExpectedConditions.elementToBeClickable(By.locator));
```

### Fluent Wait
Allows waiting with custom polling frequency.
```java
Wait<WebDriver> wait = new FluentWait<>(driver)
    .withTimeout(Duration.ofSeconds(30))
    .pollingEvery(Duration.ofSeconds(5))
    .ignoring(NoSuchElementException.class);
```

### Implicit vs Explicit Wait
| Aspect | Implicit | Explicit |
|--------|----------|----------|
| Scope | All elements | Specific elements |
| Expected Conditions | Not required | Required |
| Use Case | Quick localization | Long load times |

## Q.6 WebDriver Commands
### Navigation Commands
```java
driver.navigate().back();        // Previous page
driver.navigate().forward();     // Next page
driver.navigate().refresh();     // Refresh current page
driver.navigate().to(url);       // Go to URL
```

### get() vs navigate()
- **`get()`**: Direct navigation (no history/cookies)
- **`navigate()`**: Maintains browser history and cookies

### Finding Elements
```java
WebElement element = driver.findElement(By.locator);        // Single element
List<WebElement> elements = driver.findElements(By.locator); // Multiple elements
```

### Close vs Quit
- **`close()`**: Closes current window
- **`quit()`**: Closes all windows

## Q.7 Advanced Topics
### Handling Frames
```java
driver.switchTo().frame("frame_id");
driver.switchTo().frame(0);
driver.switchTo().defaultContent();
```

### Alert Handling
```java
Alert alert = driver.switchTo().alert();
alert.accept();           // Click OK
alert.dismiss();          // Click Cancel
String text = alert.getText();
alert.sendKeys("input");
```

### Mouse Hover
```java
Actions actions = new Actions(driver);
actions.moveToElement(driver.findElement(By.locator)).perform();
```

### Screenshot Capture
```java
File scrFile = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
FileUtils.copyFile(scrFile, new File("path/to/screenshot.jpg"));
```

### CSS Properties
```java
String value = driver.findElement(By.id("id")).getCssValue("font-size");
```

### Multiple Windows
```java
String currentHandle = driver.getWindowHandle();
Set<String> allHandles = driver.getWindowHandles();
driver.switchTo().window(handle);
```

### Page Object Model (POM) vs PageFactory
| Aspect | POM | PageFactory |
|--------|-----|-------------|
| Type | Design pattern approach | Selenium WebDriver class |
| Annotation | `@By` | `@FindBy` |
| Exception Handling | Less efficient | Efficient |
| Initialization | Manual | Automatic |
| Performance | Cache storage | No cache needed |

### PageFactory Example
```java
public class LoginPage {
    WebDriver driver;
    
    @FindBy(id = "username")
    WebElement usernameField;
    
    @FindBy(id = "password")
    WebElement passwordField;
    
    public LoginPage(WebDriver driver) {
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }
}
```

### Parallel Execution (TestNG)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE suite SYSTEM "http://testng.org/testng-1.0.dtd">
<suite name="TestSuite" thread-count="3" parallel="methods">
    <test name="testGuru">
        <classes>
            <class name="NewTest" />
        </classes>
    </test>
</suite>
```

## Q.8 Exception Handling
### Common Selenium Exceptions
- **ElementNotVisibleException**: Element exists but not visible
- **ElementNotSelectableException**: Element disabled
- **NoSuchElementException**: Element not found
- **NoSuchFrameException**: Invalid frame
- **NoAlertPresentException**: Invalid alert
- **StaleElementReferenceException**: Element no longer in DOM
- **SessionNotFoundException**: WebDriver used after quit
- **TimeoutException**: Operation exceeded time limit
- **WebDriverException**: WebDriver used after close

## Q.9 Important Concepts
### WebElement
WebElement represents an HTML element (DOM element) in a document.

### FirefoxDriver
FirefoxDriver is a Java class implementing the WebDriver interface.

### SearchContext
SearchContext is the super interface of WebDriver.

### PageFactory
PageFactory initializes WebElements to prevent `NullPointerException`.
```java
LoginPage loginPage = PageFactory.initElements(driver, LoginPage.class);
```

</em>