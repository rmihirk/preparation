# TestNG Documentation

## Q.1 What is TestNG?
➢ TestNG is a testing framework designed to simplify a broad range of testing needs, from unit testing to integration testing.

## Q.2 What are the advantages of TestNG?
1. TestNG provides parallel execution of test methods.
2. It allows defining the dependency of one test method over another.
3. It allows assigning priority to test methods.
4. It allows grouping of test methods into test groups.
5. It has support for parameterizing test cases using `@Parameters` annotation.
6. It allows data-driven testing using `@DataProvider` annotation.
7. It has different assertions that help in checking the expected and actual results.
8. Detailed (HTML) reports.

## Q.3 What are the annotations available in TestNG?
1. `@BeforeTest`
2. `@AfterTest`
3. `@BeforeClass`
4. `@AfterClass`
5. `@BeforeMethod`
6. `@AfterMethod`
7. `@BeforeSuite`
8. `@AfterSuite`
9. `@BeforeGroups`
10. `@AfterGroups`
11. `@Test`

## Q.4 Can you arrange the below testng.xml tags from parent to child?
`<test> <suite> <class> <methods> <classes>` => `<suite> <test> <classes> <class> <methods>`

## Q.5 How to create and run testng.xml?
➢ In TestNG framework, we need to create a `testng.xml` file to create and handle multiple test classes. We configure our test run, set test dependency, include or exclude any test, method, class, or package, and set priority, etc., in the XML file.

## Q.6 What is the importance of testng.xml file?
➢ In a Selenium TestNG project, we use `testng.xml` file to configure the complete test suite in a single file. Some of the features are as follows:
- `testng.xml` file allows including or excluding the execution of test methods and test groups.
- It allows passing parameters to the test cases.
- Allows adding group dependencies.
- Allows adding priorities to the test cases.
- Allows configuring parallel execution of test cases.
- Allows parameterizing the test cases.

## Q.7 How to pass parameter through testng.xml file to a test case?
➢ We could define the parameters in the `testng.xml` file and then reference those parameters in the source files.
➢ Create a Java test class, say, `ParameterizedTest.java`, and add a test method, say, `parameterizedTest()`, to the test class. This method takes a string as input parameter. Add the annotation `@Parameters("browser")` to this method.

```java
public class ParameterizedTest {
    @Test
    @Parameters("browser")
    public void parameterizedTest(String browser) {
        if (browser.equals("firefox")) {
            System.out.println("Open Firefox Driver");
        } else if (browser.equals("chrome")) {
            System.out.println("Open Chrome Driver");
        }
    }
}
```

➢ The parameter would be passed a value from `testng.xml`, which we will see in the next step.
➢ We could set the parameter using the below syntax in the `testng.xml` file.
```xml
<parameter name="browser" value="firefox"/>
```
➢ Here, the name attribute represents the parameter name and value represents the value of that parameter.

## Q.8 What is TestNG Assert and list out common TestNG Assertions?
➢ TestNG Asserts help us to verify the condition of the test in the middle of the test run. Based on the TestNG Assertions, we will consider a successful test only if it completes the test run without throwing any exception.
➢ Some of the common assertions supported by TestNG are:
- `assertEqual(String actual, String expected)`
- `assertEqual(String actual, String expected, String message)`
- `assertEquals(boolean actual, boolean expected)`
- `assertTrue(condition)`
- `assertTrue(condition, message)`
- `assertFalse(condition)`
- `assertFalse(condition, message)`

## Q.9 What is Soft Assert in TestNG?
➢ Soft Assert collects errors during `@Test`. Soft Assert does not throw an exception when an assert fails and would continue with the next step after the assert statement.
➢ If there is any exception and you want to throw it, then you need to use `assertAll()` method as the last statement in the `@Test`, and the test suite continues with the next `@Test` as it is.

## Q.10 What is Hard Assert in TestNG?
➢ Hard Assert throws an `AssertException` immediately when an assert statement fails, and the test suite continues with the next `@Test`.

## Q.11 What is exception test in TestNG?
➢ TestNG gives an option for tracing the Exception handling of code. You can verify whether a code throws the expected exception or not. The expected exception to validate while running the test case is mentioned using the `expectedExceptions` attribute value along with `@Test` annotation.

## Q.12 How to set test case priority in TestNG?
➢ We use the priority attribute in the `@Test` annotations. In case priority is not set, then the test scripts execute in alphabetical order.

```java
package TestNG;
import org.testng.annotations.*;

public class PriorityTestCase {
    @Test(priority = 0)
    public void testCase1() {
        System.out.println("Test Case 1");
    }

    @Test(priority = 1)
    public void testCase2() {
        System.out.println("Test Case 2");
    }
}
```
**Output:**
```
Test Case 1
Test Case 2
```

## Q.13 What is Parameterized testing in TestNG?
➢ Parameterized tests allow developers to run the same test over and over again using different values.
➢ There are two ways to set these parameters:
- Using `testng.xml`
- Using Data Providers

## Q.14 How can we create a data-driven framework using TestNG?
➢ By using `@DataProvider` annotation, we can create a Data Driven Framework.

```java
@DataProvider(name = "getData")
public Object[][] getData() {
    Object[][] data = new Object[2][2];
    data[0][0] = "FirstUid";
    data[0][1] = "FirstPWD";
    data[1][0] = "SecondUid";
    data[1][1] = "SecondPWD";
    return data;
}
```

## Q.15 How to run a group of test cases using TestNG?
➢ TestNG allows you to perform sophisticated groupings of test methods. Not only can you declare that methods belong to groups, but you can also specify groups that contain other groups. Then TestNG can be invoked and asked to include a certain set of groups (or regular expressions) while excluding another set. This gives you maximum flexibility in how you partition your tests and doesn’t require you to recompile anything if you want to run two different sets of tests back to back.
➢ Groups are specified in your `testng.xml` file and can be found either under the `<test>` or `<suite>` tag. Groups specified in the `<suite>` tag apply to all the `<test>` tags underneath.

```java
@Test(groups = { "smokeTest", "functionalTest" })
public void loginTest() {
    System.out.println("Logged in successfully");
}
```

## Q.16 How to create Group of Groups in TestNG?
➢ Groups can also include other groups. These groups are called MetaGroups. For example, you might want to define a group called `all` that includes `smokeTest` and `functionalTest`. Let’s modify our `testng.xml` file as follows:

```xml
<groups>
    <define name="all">
        <include name="smokeTest" />
        <include name="functionalTest" />
    </define>
    <run>
        <include name="all" />
    </run>
</groups>
```

## Q.17 How to run test cases in parallel using TestNG?
➢ We can use the `parallel` attribute in `testng.xml` to accomplish parallel test execution in TestNG.
➢ The parallel attribute of the suite tag can accept four values:
- `tests` – All the test cases inside `<test>` tag of `testng.xml` file will run in parallel.
- `classes` – All the test cases inside a Java class will run in parallel.
- `methods` – All the methods with `@Test` annotation will execute in parallel.
- `instances` – Test cases in the same instance will execute in parallel, but two methods of two different instances will run in different threads.

```xml
<suite name="softwaretestingmaterial" parallel="methods">
```

## Q.18 How to exclude a particular test method from a test case execution?
➢ By adding the exclude tag in the `testng.xml`.

```xml
<classes>
    <class name="TestCaseName">
        <methods>
            <exclude name="TestMethodNameToExclude"/>
        </methods>
    </class>      
</classes>
```

## Q.19 How to exclude a particular test group from a test case execution?
➢ By adding the exclude tag in the `testng.xml`.

```xml
<groups>
    <run>
        <exclude name="TestGroupNameToExclude"/>
    </run>      
</groups>
```

## Q.20 How to disable/Ignore a test case in TestNG?
➢ To disable/ignore the test case, we use the parameter `enabled = false` in the `@Test` annotation.

```java
@Test(enabled = false)
```

## Q.21 How to skip a @Test method from execution in TestNG?
➢ By using `throw new SkipException()`.
➢ Once `SkipException()` is thrown, the remaining part of that test method will not be executed, and control will go directly to the next test method execution.

```java
throw new SkipException("Skipping - This is not ready for testing");
```

## Q.22 How TestNG allows to state dependencies?
➢ TestNG allows two ways to declare the dependencies:
- Using attributes `dependsOnMethods` in `@Test` annotations.
- Using attributes `dependsOnGroups` in `@Test` annotations.

## Q.23 What are the different ways to produce reports for TestNG results?
➢ TestNG offers two ways to produce a report:
- Listeners implement the interface `org.testng.ITestListener` and are notified in real-time of when a test starts, passes, fails, etc.
- Reporters implement the interface `org.testng.IReporter` and are notified when all the suites have been run by TestNG. The `IReporter` instance receives a list of objects that describe the entire test run.

## Q.24 What is the use of @Listener annotation in TestNG?
➢ TestNG listeners are used to configure reports and logging. One of the most widely used listeners in TestNG is the `ITestListener` interface. It has methods like `onTestStart`, `onTestSuccess`, `onTestFailure`, `onTestSkipped`, etc. We should implement this interface by creating a listener class of our own. Next, we should add the listeners annotation (`@Listeners`) in the class that was created.

## Q.25 How to write a regular expression in testng.xml file to search @Test methods containing “smoke” keyword?
➢ Regular expression to find `@Test` methods containing the keyword “smoke” is as mentioned below.

```xml
<methods>
    <include name=".*smoke.*"/>
</methods>
```

## Q.26 What is the time unit we specify in test suites and test cases?
➢ We specify the time unit in test suites and test cases in milliseconds.

## Q.27 List out various ways in which TestNG can be invoked?
➢ TestNG can be invoked in the following ways:
- Using Eclipse IDE.
- Using Ant build tool.
- From the command line.
- Using IntelliJ IDEA.

## Q.28 How To Run TestNG Using Command Prompt?
➢ Run TestNG using the command prompt:
```bash
C:\Users\Admin\workspace\SoftwareTestingMaterial
set classpath=C:\Users\Admin\workspace\SoftwareTestingMaterial\bin;C:\Users\Admin\workspace\SoftwareTestingMaterial\lib\*

java org.testng.TestNG C:\Users\Admin\workspace\SoftwareTestingMaterial\testng.xml
```

## Q.29 What is the use of @Test(invocationCount=x)?
➢ The `invocationCount` attribute tells how many times TestNG should run a test method.

```java
@Test(invocationCount = 10)
public void testCase1() {}
```
➢ In this example, the method `testCase1` will be invoked ten times.

## Q.30 What is the use of @Test(threadPoolSize=x)?
➢ The `threadPoolSize` attribute tells to form a thread pool to run the test method through multiple threads.
➢ Note: This attribute is ignored if `invocationCount` is not specified.

```java
@Test(threadPoolSize = 3, invocationCount = 10)
public void testCase1() {}
```
➢ In this example, the method `testCase1` will be invoked from three different threads.

## Q.31 What does the test timeout mean in TestNG?
➢ The maximum number of milliseconds a test case should take.

```java
@Test(threadPoolSize = 3, invocationCount = 10, timeOut = 10000)
public void testCase1() {}
```
➢ In this example, the function `testCase1` will be invoked ten times from three different threads. Additionally, a time-out of ten seconds guarantees that none of the threads will block on this thread forever.

## Q.32 What are @Factory and @DataProvider annotations?
➢ `@Factory`: A factory will execute all the test methods present inside a test class using a separate instance of the respective class with a different set of data.
➢ `@DataProvider`: A test method that uses `DataProvider` will be executed the specific methods multiple times based on the data provided by the `DataProvider`. The test method will be executed using the same instance of the test class to which the test method belongs.

## Q.33 TestNG Listeners in Selenium
➢ There are two main listeners:
- WebDriver Listeners
- TestNG Listeners

## Q.34 What is Listeners in TestNG?
➢ Listener is defined as an interface that modifies the default TestNG’s behavior. As the name suggests, Listeners “listen” to the event defined in the Selenium script and behave accordingly. It is used in Selenium by implementing the Listeners Interface. It allows customizing TestNG reports or logs. There are many types of TestNG listeners available.

## Q.35 How many types of Listeners in TestNG?
➢ There are many types of listeners which allow you to change TestNG’s behavior. Below are a few TestNG listeners:
1. `IAnnotationTransformer`
2. `IAnnotationTransformer2`
3. `IConfigurable`
4. `IConfigurationListener`
5. `IExecutionListener`
6. `IHookable`
7. `IInvokedMethodListener`
8. `IInvokedMethodListener2`
9. `IMethodInterceptor`
10. `IReporter`
11. `ISuiteListener`
12. `ITestListener`

➢ The above interfaces are called TestNG Listeners. These interfaces are used in Selenium to generate logs or customize the TestNG reports.

## Q.36 ITestListener has the following methods:
➢ `onStart` - Called when any Test starts.
➢ `onTestSuccess` - Called on the success of any Test.
➢ `onTestFailure` - Called on the failure of any Test.
➢ `onTestSkipped` - Called on skipped of any Test.
➢ `onTestFailedButWithinSuccessPercentage` - Called each time Test fails but is within success percentage.
➢ `onFinish` - Called after all Tests are executed.

## Q.37 Use of Listener for multiple classes.
➢ If a project has multiple classes, adding Listeners to each one of them could be cumbersome and error-prone. In such cases, we can create a `testng.xml` and add the listeners tag in XML.
➢ This listener is implemented throughout the test suite irrespective of the number of classes you have. When you run this XML file, listeners will work on all classes mentioned. You can also declare any number of listener classes.

## Q.38 What are the latest changes in TestNG?
➢ TestNG has introduced new features for better reporting and enhanced support for parallel execution.

## Q.39 How has TestNG improved integration with build tools?
➢ TestNG has improved integration with build tools like Maven and Gradle.

## Q.40 What enhancements have been made for data-driven testing in TestNG?
➢ TestNG has enhanced support for data-driven testing with better annotations and configurations.