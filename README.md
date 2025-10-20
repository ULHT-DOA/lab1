# Lab 1 

## Topics: Java Variables, Arrays, Flow control and Exceptions

## Learning Objectives

Upon completion of this laboratory exercise, students will be able to:

- Declare and initialize variables with appropriate data types
- Create and manipulate arrays in Java
- Implement flow control structures (conditionals and loops) to solve programming problems
- Write robust code using exception handling mechanisms (try, catch, finally blocks)

## Pre-Lab Setup

Before starting the exercises, ensure the following:

1. **Java Development Kit (JDK)** is installed (version 11 or higher)
2. **IDE or Text Editor** is available (IntelliJ IDEA, Eclipse, VS Code, or terminal with javac)
3. **Working directory** is created for all lab files
4. **Compiler test:** Open a terminal and verify `javac -version` works

## Exercise 1: Variables, Data Types & Arrays 

### Learning Outcomes

- Practice declaring variables with various primitive and reference data types
- Understand array initialization and element access
- Perform basic arithmetic and string operations

### Goal

Create a program that stores student grades in an array, calculates the average grade, and identifies the maximum grade.

### Instructions

Write a Java class named `GradeAnalyzer.java` that:

1. Declares an array of `double` values to store 5 student grades
2. Initializes the array with the following grades: 78.5, 92.0, 85.5, 88.0, 76.5
3. Calculates and prints the average grade using a loop
4. Finds and prints the maximum grade
5. Counts and prints how many students scored above 85.0

### Starter Code

```java
public class GradeAnalyzer {
    public static void main(String[] args) {
        // TODO: Declare and initialize the grades array
        double[] grades = {78.5, 92.0, 85.5, 88.0, 76.5};
        
        // TODO: Calculate average
        double sum = 0;
        // Use a for loop to add all grades
        
        // TODO: Find maximum grade
        double maxGrade = grades[0];
        // Use a for loop to find the maximum
        
        // TODO: Count grades above 85.0
        int countAbove85 = 0;
        // Use a for loop to count
        
        // Print results
    }
}
```

### Expected Output

```
Average Grade: 84.1
Maximum Grade: 92.0
Students with Grade Above 85.0: 3
```

### Hints

- Use `grades.length` to determine the array size dynamically
- The average is the sum divided by the number of grades
- Remember that array indices start at 0

## Exercise 2: Flow Control & Array Processing 

### Learning Outcomes

- Apply conditional statements (if, else, switch) to control program flow
- Nested loops for 2D array or multi-pass processing
- Classify data based on conditions

### Goal

Create a program that categorizes students based on their grades and generates a report.

### Instructions

Write a Java class named `GradeClassifier.java` that:

1. Declares an array of 6 student grades: 95, 78, 65, 88, 72, 91
2. Uses a `for` loop to iterate through each grade
3. Assigns each grade to a category using an `if-else` structure:
   - **A:** 90–100
   - **B:** 80–89
   - **C:** 70–79
   - **D:** 60–69
   - **F:** Below 60
4. Counts how many students fall into each category
5. Prints a summary report

### Starter Code

```java
public class GradeClassifier {
    public static void main(String[] args) {
        int[] grades = {95, 78, 65, 88, 72, 91};
        
        int countA = 0, countB = 0, countC = 0, countD = 0, countF = 0;
        
        // TODO: Loop through grades and classify each one
        for (int grade : grades) {
            // TODO: Use if-else to assign category and increment counter
        }
        
        // TODO: Print the report
    }
}
```

### Expected Output

```
Grade Distribution Report:
A (90-100): 2 students
B (80-89): 2 students
C (70-79): 2 students
D (60-69): 0 students
F (Below 60): 0 students
Total Students: 6
```

### Hints

- The enhanced `for` loop (`for (int grade : grades)`) is simpler for iteration without needing indices
- Consider using a nested structure or separate loops for clarity
- Verify that all students are counted by checking that the total equals the array length

### Challenge 

Modify the program to use a `switch` statement instead of `if-else`. Map numeric grade ranges to single-character letter grades. Discuss with your lab partner which approach is clearer.

## Exercise 3: Exception Handling & Integration 

### Learning Outcomes

- Implement try-catch-finally blocks to handle runtime errors
- Understand array index out-of-bounds exceptions
- Integrate previous concepts in a more complex scenario

### Goal

Create a program that safely reads student grades from user input, handles invalid data, and generates a report.

### Instructions

Write a Java class named `SafeGradeReader.java` that:

1. Uses `try-catch-finally` to handle potential exceptions
2. Attempts to read 3 grades from the user (simulate with hardcoded values for this lab)
3. Validates that grades are between 0 and 100; if not, throw or catch an exception
4. Stores valid grades in an array
5. Calculates statistics only for valid grades
6. Ensures cleanup code runs in the `finally` block (e.g., printing a completion message)

### Starter Code

```java
import java.util.Scanner;

public class SafeGradeReader {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int[] grades = new int[3];
        int validCount = 0;
        
        try {
            // TODO: Attempt to read 3 grades
            for (int i = 0; i < 3; i++) {
                System.out.print("Enter grade " + (i + 1) + ": ");
                int grade = scanner.nextInt();
                
                // TODO: Validate grade (0–100)
                if (grade < 0 || grade > 100) {
                    throw new IllegalArgumentException("Grade must be between 0 and 100.");
                }
                
                grades[i] = grade;
                validCount++;
            }
            
            // TODO: Calculate and display average of valid grades
            
        } catch (IllegalArgumentException e) {
            // TODO: Handle invalid grade values
            System.out.println("Error: " + e.getMessage());
        } catch (java.util.InputMismatchException e) {
            // TODO: Handle non-integer input
            System.out.println("Error: Please enter a valid integer.");
        } finally {
            // TODO: Print completion message
            System.out.println("Grade entry process completed.");
            scanner.close();
        }
    }
}
```

### Expected Output (Example with Valid Input)

```
Enter grade 1: 85
Enter grade 2: 92
Enter grade 3: 78
Average of valid grades: 85.0
Grade entry process completed.
```

### Expected Output (Example with Invalid Input)

```
Enter grade 1: 85
Enter grade 2: 105
Error: Grade must be between 0 and 100.
Grade entry process completed.
```

### Java Concepts Practiced

- **Exception Handling:** `try-catch-finally` blocks
- **Custom Validation:** Checking input constraints
- **Standard Exceptions:** `IllegalArgumentException`, `InputMismatchException`
- **Resource Management:** Closing scanner in `finally` block
- **Integration:** Combines variables, arrays, loops, and conditionals from previous exercises

### Hints

- The `finally` block always executes, whether an exception is caught or not
- Use `InputMismatchException` to handle cases where the user enters non-numeric input
- Test your code with both valid and invalid inputs to ensure robust error handling
- For this lab, you may hardcode test values instead of using actual `Scanner` input


### Challenge: Grade Management System

Extend Exercise 3 to create a simple grade management system with the following features:

1. **Multiple students:** Use a 2D array or an array of objects to store grades for 3 students (each with 4 subjects)
2. **Nested loops:** Calculate the average grade per student and overall class average
3. **Exception handling:** Validate all inputs; handle division by zero if no valid grades exist
4. **Flow control:** Use a `switch` statement to implement a menu system:
   - Option 1: Add a grade
   - Option 2: View student averages
   - Option 3: Exit

### Suggested Structure

```java
public class GradeManagementSystem {
    public static void main(String[] args) {
        // 2D array: 3 students, 4 subjects each
        int[][] studentGrades = new int[3][4];
        
        // Populate with sample data
        // TODO: Implement menu-driven interface using switch statement
        // TODO: Calculate per-student and class averages
        // TODO: Handle exceptions for invalid operations
    }
}
```



### Key Takeaways

1. **Variables and data types** are the foundation; choose the right type for your data
2. **Arrays** enable efficient storage and processing of multiple values
3. **Flow control** allows you to make decisions and repeat operations systematically
4. **Exception handling** makes programs robust and user-friendly



## Deliverables

### Required Submissions

1. **Exercise 1:** `GradeAnalyzer.java` with working output
2. **Exercise 2:** `GradeClassifier.java` with working output
3. **Exercise 3:** `SafeGradeReader.java` with exception handling demonstrated
4. **Bonus Challenge:** `GradeManagementSystem.java` 



### Submission 

Place all Java files in a single folder named `Lab_YourName_StudentID` and deliver it in moodle in a .zip file under Lab 1.



