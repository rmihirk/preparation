<em>

# QA Basics

## Basics of Software Testing

There are two fundamental approaches to software testing:

### Black Box Testing (Functional Testing)
Black box testing is a testing technique that ignores the internal mechanism of the system and focuses on the output generated against any input and execution of the system. It is also called functional testing.

### White Box Testing (Structural Testing)
White box testing is a testing technique that takes into account the internal mechanism of a system. It is also called structural testing and glass box testing.

**Note:** Black box testing is often used for validation, while white box testing is often used for verification.

## Types of Testing

- Unit Testing
- Integration Testing
- Functional Testing
- System Testing
- Stress Testing
- Performance Testing
- Usability Testing
- Acceptance Testing
- Regression Testing
- Beta Testing

### Unit Testing
Written by software developers, these tests validate a unit of code in isolation. It falls under white box testing and is often done by programmers to ensure their implementation produces expected output.

### Integration Testing
Tests how well different software components work with each other. It falls under both white box and black box testing categories.

### Functional Testing
Ensures specified functionality required in system requirements works. Falls under black box testing.

### System Testing
Ensures software works correctly in different environments (e.g., Operating Systems). Falls under black box testing.

### Stress Testing
Evaluates system behavior under unfavorable conditions beyond specification limits. Falls under black box testing.

### Performance Testing
Assesses speed and effectiveness of the system under heavy load to ensure results are generated within specified time requirements. Falls under black box testing.

### Usability Testing
Evaluates GUI user-friendliness, ease of learning, and design appeal from the client's perspective. Falls under black box testing.

### Acceptance Testing
Often conducted by customers to ensure the delivered product meets requirements and works as expected. Falls under black box testing.

### Regression Testing
Verifies that new code didn't break existing functionality after system modifications. Falls under black box testing.

### Beta Testing
Conducted by end users or external teams using the pre-release version to uncover unexpected errors. Falls under black box testing.

## Smoke vs Sanity vs Regression vs Retesting

| Aspect | Smoke Testing | Sanity Testing | Regression Testing | Retesting |
|--------|---------------|----------------|--------------------|-----------|
| **Purpose** | Verify system "stability" for rigorous testing | Verify system "rationality" after minor changes | Confirm recent changes don't adversely affect existing features | Confirm failed test cases pass after defect fixes |
| **Defect Verification** | Not part of smoke testing | Not part of sanity testing | Not part of regression testing | Part of retesting |
| **Execution Order** | Before regression test | After smoke testing | Parallel with retesting | Before sanity testing |
| **Automation** | Manual or automated | Typically manual | Can be automated | Cannot be automated |
| **Classification** | Subset of regression testing | Subset of acceptance testing | Performed after modifications | Uses previous test cases |

## Verification vs Validation

| Aspect | Verification | Validation |
|--------|--------------|-----------|
| **Definition** | Checking documents, design, code, and program | Dynamic mechanism of testing actual product |
| **Involves Execution** | Does not involve executing code | Always involves executing code |
| **Methods** | Reviews, walkthroughs, inspections, desk-checking | Black box, white box, non-functional testing |
| **Focus** | Software conformance to specification | Software meets customer requirements |
| **Bug Detection** | Finds bugs early in development | Finds bugs verification cannot catch |
| **Target** | Application architecture, design, database | Actual product |
| **Responsible Team** | QA team | Testing team |
| **Sequence** | Comes before validation | Comes after verification |

### Example: Verification vs Validation
**Spelling Error (Verification Phase)**
- Verification checks design documentation for "Submet" and corrects spelling.

**Functionality Check (Validation Phase)**
- Validation ensures the "Submit" button is actually clickable after code implementation.

## Severity & Priority in Testing

### Severity
Severity is the degree of impact a defect has on the development or operation of a component or application. Higher impact on system functionality results in higher severity assignment. Determined by QA engineers.

### Priority
Priority is the order in which a defect should be fixed. Defects that render the software unusable receive higher priority than those affecting minor functionality.

## Manual Testing vs Automated Testing

| Aspect | Manual Testing | Automated Testing |
|--------|----------------|-------------------|
| **Execution** | Human executes test cases one by one | Testing tool/framework executes tests |
| **Best For** | Non-repeatable tests, human ingenuity required | Repeatable tests with stable features |
| **Testing Type** | Good for accessibility and usability testing | Good for regression testing |
| **Speed** | Slow and time-consuming | Fast and error-free |
| **Exploration** | Exploratory testing possible | Exploratory testing not possible |
| **UI Detection** | UI problems easily spotted | Requires specific programming |
| **Performance Testing** | Difficult under extreme load | Easily conducted |
| **Prerequisites** | No programming knowledge required | Requires programming knowledge |

## When to Automate Tests

A test is a good candidate for automation when:
- The test is repeatable
- The feature doesn't change behavior frequently
- It's time-consuming for manual testing
- The test involves complicated calculations
- It ensures previous functionality didn't break after changes

## Automation Testing Life Cycle Phases

1. Figure out the scope of automation testing
2. Choose correct automation frameworks and tools
3. Design test plan + test execution strategy
4. Set up the test environment
5. Develop and execute test cases
6. Analyze and generate test reports

</em>