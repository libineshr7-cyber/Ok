# 241GES311L -- Object Oriented Programming Using Java Laboratory

## Set of 20 Practical Programs -- Preparation README

**Source:** `241GES311L SET 1 Split Up.docx` supplied for the practical
preparation.

This README contains the 20 distinct question numbers from the
lecturer's split-up sheet. The source sheet gives the question
statements, but it does not prescribe algorithms, sample inputs, class
names, or JavaFX implementation details. The programs below are practice
implementations that satisfy the stated tasks. Follow any additional
format or grading rules given by your lecturer.

## Before running

-   Use **JDK 21** (or the JDK configured in your Eclipse project).
-   In Eclipse: `File → New → Java Project`, then create a class whose
    name matches the public class in the code.
-   For console programs, run using **Run → Run As → Java Application**.
-   JavaFX programs (Q19 and Q20) require a separate JavaFX SDK and VM
    arguments/module path. They will not run in a plain Java project
    until JavaFX is configured.
-   Each code block is a separate program. Do not paste all programs
    into one Java file.

------------------------------------------------------------------------

## Q1. Student Grading System

**Question:** Read marks of a student, calculate the average and assign
grades: average ≥ 90 -- S; ≥ 80 -- A; ≥ 60 -- B; otherwise -- Fail.

**Aim:** To calculate a student's average and display the corresponding
grade.

**Algorithm:** Read subject count and marks; calculate total and
average; use an `if-else-if` ladder to assign the grade; display the
result.

**File:** `StudentGrading.java`

``` java
import java.util.Scanner;

public class StudentGrading {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n, total = 0;

        System.out.print("Enter number of subjects: ");
        n = sc.nextInt();

        for (int i = 1; i <= n; i++) {
            System.out.print("Enter mark " + i + ": ");
            total += sc.nextInt();
        }

        double average = (double) total / n;
        String grade;

        if (average >= 90)
            grade = "S";
        else if (average >= 80)
            grade = "A";
        else if (average >= 60)
            grade = "B";
        else
            grade = "Fail";

        System.out.println("Total = " + total);
        System.out.println("Average = " + average);
        System.out.println("Grade = " + grade);
        sc.close();
    }
}
```

**Sample output:** For marks 95, 85, 75: `Total = 255`,
`Average = 85.0`, `Grade = A`.

**Result:** The student's total, average and grade are calculated and
displayed.

------------------------------------------------------------------------

## Q2. Student Total, Average and Grade

**Question:** Read marks in different subjects and calculate total,
average and grade using appropriate control statements.

**Aim:** To calculate and display the total, average and grade.

**Algorithm:** Read the number of subjects; read each mark in a loop;
add marks; calculate average; use conditional statements to decide
grade; display all values.

**File:** `StudentGrade.java`

``` java
import java.util.Scanner;

public class StudentGrade {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n, total = 0;

        System.out.print("Enter number of subjects: ");
        n = sc.nextInt();

        if (n <= 0) {
            System.out.println("Number of subjects must be positive.");
            sc.close();
            return;
        }

        for (int i = 1; i <= n; i++) {
            System.out.print("Enter mark for subject " + i + ": ");
            int mark = sc.nextInt();
            total = total + mark;
        }

        double average = (double) total / n;
        String grade;

        // Example grade scale only: the Q2 statement does not specify grade boundaries.
        if (average >= 90)
            grade = "A";
        else if (average >= 80)
            grade = "B";
        else if (average >= 70)
            grade = "C";
        else if (average >= 60)
            grade = "D";
        else
            grade = "F";

        System.out.println("Total Marks = " + total);
        System.out.println("Average = " + average);
        System.out.println("Grade = " + grade);
        sc.close();
    }
}
```

**Sample output:** 90, 85, 80, 75, 70 → total `400`, average `80.0`,
grade `B`.

**Important:** The lecturer's Q2 does not state grade boundaries. The
scale in this sample is an example. If your lecturer gives a specific
scale, replace the conditions.

**Result:** The total, average and grade are displayed.

------------------------------------------------------------------------

## Q3. Default, Parameterized and Copy Constructors -- Student

**Aim:** To demonstrate three types of constructors using a `Student`
class.

**Algorithm:** Create a default constructor, a parameterized constructor
and a copy constructor; create three objects; display their details.

**File:** `StudentConstructorDemo.java`

``` java
class Student {
    int id;
    String name;

    Student() {
        id = 0;
        name = "Not Assigned";
    }

    Student(int i, String n) {
        id = i;
        name = n;
    }

    Student(Student s) {
        id = s.id;
        name = s.name;
    }

    void display() {
        System.out.println("ID: " + id + ", Name: " + name);
    }
}

public class StudentConstructorDemo {
    public static void main(String[] args) {
        Student s1 = new Student();
        Student s2 = new Student(101, "Arun");
        Student s3 = new Student(s2);

        System.out.println("Default constructor:");
        s1.display();

        System.out.println("Parameterized constructor:");
        s2.display();

        System.out.println("Copy constructor:");
        s3.display();
    }
}
```

**Sample output:** Default object shows `0, Not Assigned`; parameterized
and copied objects both show `101, Arun`.

**Result:** Default, parameterized and copy constructors are
demonstrated.

------------------------------------------------------------------------

## Q4. Employee Default and Parameterized Constructors

**Aim:** To initialize and display employee details using default and
parameterized constructors.

**Algorithm:** Define employee fields; initialize them in a default
constructor and a parameterized constructor; create objects and display
details.

**File:** `EmployeeConstructorDemo.java`

``` java
class Employee {
    int empId;
    String name;
    double salary;

    Employee() {
        empId = 0;
        name = "Not Assigned";
        salary = 0.0;
    }

    Employee(int id, String n, double s) {
        empId = id;
        name = n;
        salary = s;
    }

    void display() {
        System.out.println("Employee ID: " + empId);
        System.out.println("Name: " + name);
        System.out.println("Salary: " + salary);
    }
}

public class EmployeeConstructorDemo {
    public static void main(String[] args) {
        Employee e1 = new Employee();
        Employee e2 = new Employee(101, "Kumar", 30000);

        System.out.println("Default constructor:");
        e1.display();

        System.out.println("Parameterized constructor:");
        e2.display();
    }
}
```

**Result:** Employee details are initialized and displayed using both
constructors.

------------------------------------------------------------------------

## Q5. Employee Pay Slip Using Inheritance

**Question:** Create an `Employee` class with `Emp_name`, `Emp_id`,
`Address`, `Mail_id` and `Mobile_no`. Derive `Programmer`,
`AssistantProfessor`, `AssociateProfessor` and `Professor` classes and
generate a pay slip using inheritance.

**Aim:** To demonstrate hierarchical inheritance and generate employee
pay slips.

**Algorithm:** Create a base `Employee` class containing common details;
derive four job classes; accept basic pay; calculate DA, HRA, PF and
staff club fund; display gross and net pay.

**File:** `EmployeePaySlip.java`

``` java
class Employee {
    String empName, address, mailId, mobileNo;
    int empId;
    double basicPay;

    Employee(String name, int id, String addr, String mail, String mobile, double bp) {
        empName = name;
        empId = id;
        address = addr;
        mailId = mail;
        mobileNo = mobile;
        basicPay = bp;
    }

    void generatePaySlip(String designation) {
        double da = basicPay * 0.97;
        double hra = basicPay * 0.10;
        double pf = basicPay * 0.12;
        double club = basicPay * 0.001;
        double gross = basicPay + da + hra;
        double net = gross - pf - club;

        System.out.println("\n--- " + designation + " PAY SLIP ---");
        System.out.println("Name: " + empName);
        System.out.println("Employee ID: " + empId);
        System.out.println("Address: " + address);
        System.out.println("Mail ID: " + mailId);
        System.out.println("Mobile: " + mobileNo);
        System.out.println("Basic Pay: " + basicPay);
        System.out.println("DA: " + da);
        System.out.println("HRA: " + hra);
        System.out.println("PF: " + pf);
        System.out.println("Staff Club Fund: " + club);
        System.out.println("Gross Pay: " + gross);
        System.out.println("Net Pay: " + net);
    }
}

class Programmer extends Employee {
    Programmer(String n, int id, String a, String m, String mob, double bp) {
        super(n, id, a, m, mob, bp);
    }
}
class AssistantProfessor extends Employee {
    AssistantProfessor(String n, int id, String a, String m, String mob, double bp) {
        super(n, id, a, m, mob, bp);
    }
}
class AssociateProfessor extends Employee {
    AssociateProfessor(String n, int id, String a, String m, String mob, double bp) {
        super(n, id, a, m, mob, bp);
    }
}
class Professor extends Employee {
    Professor(String n, int id, String a, String m, String mob, double bp) {
        super(n, id, a, m, mob, bp);
    }
}

public class EmployeePaySlip {
    public static void main(String[] args) {
        Programmer p = new Programmer("Arun", 101, "Chennai",
                "arun@mail.com", "9876543210", 30000);
        p.generatePaySlip("Programmer");

        AssistantProfessor ap = new AssistantProfessor("Bala", 102, "Chennai",
                "bala@mail.com", "9876543211", 40000);
        ap.generatePaySlip("Assistant Professor");

        AssociateProfessor acp = new AssociateProfessor("Charan", 103, "Madurai",
                "charan@mail.com", "9876543212", 50000);
        acp.generatePaySlip("Associate Professor");

        Professor prof = new Professor("Devi", 104, "Trichy",
                "devi@mail.com", "9876543213", 60000);
        prof.generatePaySlip("Professor");
    }
}
```

**Formulae:** DA = 97% of BP; HRA = 10% of BP; PF = 12% of BP; Staff
Club Fund = 0.1% of BP; Gross = BP + DA + HRA; Net = Gross − PF − Staff
Club Fund.

**Result:** Pay slips are generated for all four employee categories
using inheritance.

------------------------------------------------------------------------

## Q6. Gross Salary and Net Salary Using Inheritance

**Aim:** To calculate gross and net salary for employee categories using
inheritance.

**Algorithm:** Read basic pay; calculate DA, HRA, PF and staff club fund
using the specified percentages; calculate gross and net salary; display
the values.

**File:** `SalaryCalculation.java`

``` java
class Salary {
    double basicPay;

    Salary(double bp) {
        basicPay = bp;
    }

    void calculate(String category) {
        double da = basicPay * 0.97;
        double hra = basicPay * 0.10;
        double pf = basicPay * 0.12;
        double club = basicPay * 0.001;
        double gross = basicPay + da + hra;
        double net = gross - pf - club;

        System.out.println("\nCategory: " + category);
        System.out.println("Basic Pay: " + basicPay);
        System.out.println("DA: " + da);
        System.out.println("HRA: " + hra);
        System.out.println("PF: " + pf);
        System.out.println("Staff Club Fund: " + club);
        System.out.println("Gross Salary: " + gross);
        System.out.println("Net Salary: " + net);
    }
}

class TeachingStaff extends Salary {
    TeachingStaff(double bp) { super(bp); }
}
class NonTeachingStaff extends Salary {
    NonTeachingStaff(double bp) { super(bp); }
}

public class SalaryCalculation {
    public static void main(String[] args) {
        TeachingStaff t = new TeachingStaff(40000);
        t.calculate("Teaching Staff");

        NonTeachingStaff n = new NonTeachingStaff(25000);
        n.calculate("Non-Teaching Staff");
    }
}
```

**Result:** Gross and net salary are calculated using the percentages
given in the question. The two subclasses are illustrative employee
categories; use the categories specified by your lecturer if different.

------------------------------------------------------------------------

## Q7. Abstract Class Shape with `printArea()`

**Aim:** To demonstrate an abstract class and abstract method.

**Algorithm:** Define abstract class `Shape` with `printArea()`; derive
Rectangle, Triangle and Circle; override the method; create objects and
call the method.

**File:** `AbstractShapePrint.java`

``` java
abstract class Shape {
    abstract void printArea();
}

class Rectangle extends Shape {
    double length = 10, breadth = 5;

    void printArea() {
        System.out.println("Rectangle area = " + (length * breadth));
    }
}

class Triangle extends Shape {
    double base = 8, height = 6;

    void printArea() {
        System.out.println("Triangle area = " + (0.5 * base * height));
    }
}

class Circle extends Shape {
    double radius = 7;

    void printArea() {
        System.out.println("Circle area = " + (Math.PI * radius * radius));
    }
}

public class AbstractShapePrint {
    public static void main(String[] args) {
        Shape r = new Rectangle();
        Shape t = new Triangle();
        Shape c = new Circle();

        r.printArea();
        t.printArea();
        c.printArea();
    }
}
```

**Result:** Areas are displayed by overriding the abstract method.

------------------------------------------------------------------------

## Q8. Abstract Class to Calculate Areas

**Aim:** To calculate rectangle, circle and triangle areas using an
abstract class, inheritance and method overriding.

**Algorithm:** Declare abstract method `area()` in `Shape`; implement it
in each child class; call the overridden methods through parent
references.

**File:** `AbstractShapeArea.java`

``` java
abstract class Shape {
    abstract double area();
}

class Rectangle extends Shape {
    double length = 10, breadth = 5;
    double area() { return length * breadth; }
}

class Circle extends Shape {
    double radius = 7;
    double area() { return Math.PI * radius * radius; }
}

class Triangle extends Shape {
    double base = 8, height = 6;
    double area() { return 0.5 * base * height; }
}

public class AbstractShapeArea {
    public static void main(String[] args) {
        Shape r = new Rectangle();
        Shape c = new Circle();
        Shape t = new Triangle();

        System.out.println("Rectangle area = " + r.area());
        System.out.println("Circle area = " + c.area());
        System.out.println("Triangle area = " + t.area());
    }
}
```

**Result:** The three areas are calculated using inheritance and method
overriding.

------------------------------------------------------------------------

## Q9. Interface `Shape` to Calculate Areas

**Aim:** To calculate areas by implementing an interface named `Shape`.

**Algorithm:** Declare `area()` in the interface; implement it in
Rectangle, Circle and Triangle; create objects and display the returned
areas.

**File:** `InterfaceShapeArea.java`

``` java
interface Shape {
    double area();
}

class Rectangle implements Shape {
    public double area() {
        return 10 * 5;
    }
}

class Circle implements Shape {
    public double area() {
        double r = 7;
        return Math.PI * r * r;
    }
}

class Triangle implements Shape {
    public double area() {
        return 0.5 * 8 * 6;
    }
}

public class InterfaceShapeArea {
    public static void main(String[] args) {
        Shape r = new Rectangle();
        Shape c = new Circle();
        Shape t = new Triangle();

        System.out.println("Rectangle area = " + r.area());
        System.out.println("Circle area = " + c.area());
        System.out.println("Triangle area = " + t.area());
    }
}
```

**Result:** The interface is implemented by three classes to calculate
areas.

------------------------------------------------------------------------

## Q10. Interface for Different Geometrical Shapes

**Aim:** To demonstrate an interface implemented by separate shape
classes.

**Algorithm:** Create an interface with an area method; implement the
method in Rectangle, Circle and Triangle classes; display each result.

**File:** `GeometryInterfaceDemo.java`

``` java
interface Geometry {
    double calculateArea();
}

class Rect implements Geometry {
    public double calculateArea() {
        double length = 12, breadth = 4;
        return length * breadth;
    }
}

class Circ implements Geometry {
    public double calculateArea() {
        double radius = 5;
        return Math.PI * radius * radius;
    }
}

class Tri implements Geometry {
    public double calculateArea() {
        double base = 10, height = 6;
        return 0.5 * base * height;
    }
}

public class GeometryInterfaceDemo {
    public static void main(String[] args) {
        Geometry r = new Rect();
        Geometry c = new Circ();
        Geometry t = new Tri();

        System.out.println("Rectangle = " + r.calculateArea());
        System.out.println("Circle = " + c.calculateArea());
        System.out.println("Triangle = " + t.calculateArea());
    }
}
```

**Result:** Areas are calculated and displayed through an interface.

------------------------------------------------------------------------

## Q11. Exception Handling: `try`, `catch`, `finally`, `throw`, `throws`

**Aim:** To demonstrate Java exception-handling keywords.

**Algorithm:** Call a method declared with `throws`; use `throw` when
the denominator is zero; handle the exception in `catch`; execute
`finally`.

**File:** `ExceptionKeywordsDemo.java`

``` java
public class ExceptionKeywordsDemo {
    static int divide(int a, int b) throws ArithmeticException {
        if (b == 0) {
            throw new ArithmeticException("Cannot divide by zero");
        }
        return a / b;
    }

    public static void main(String[] args) {
        try {
            int result = divide(10, 0);
            System.out.println("Result = " + result);
        } catch (ArithmeticException e) {
            System.out.println("Exception: " + e.getMessage());
        } finally {
            System.out.println("Finally block executed.");
        }
    }
}
```

**Result:** `try`, `catch`, `finally`, `throw` and `throws` are
demonstrated.

------------------------------------------------------------------------

## Q12. User-Defined Exception for Invalid Age

**Aim:** To create and handle a user-defined exception for invalid age.

**Algorithm:** Create an exception class; read age; throw the custom
exception if age is below 18; catch and display the error.

**File:** `InvalidAgeDemo.java`

``` java
import java.util.Scanner;

class InvalidAgeException extends Exception {
    InvalidAgeException(String message) {
        super(message);
    }
}

public class InvalidAgeDemo {
    static void checkAge(int age) throws InvalidAgeException {
        if (age < 18) {
            throw new InvalidAgeException("Age must be 18 or above.");
        }
        System.out.println("Valid age.");
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter age: ");
        int age = sc.nextInt();

        try {
            checkAge(age);
        } catch (InvalidAgeException e) {
            System.out.println("Error: " + e.getMessage());
        }

        sc.close();
    }
}
```

**Sample output:** Enter `16` → `Error: Age must be 18 or above.`

**Result:** A user-defined exception is raised and handled for an
invalid age.

------------------------------------------------------------------------

## Q13. Three Threads: Random Number, Square and Cube

**Aim:** To create three threads where one generates a random number
every second, a second finds the square of even numbers, and a third
finds the cube of odd numbers.

**Algorithm:** Create a square thread and a cube thread; create a
random-number thread; every second generate a number; start the square
thread for even numbers or cube thread for odd numbers.

**File:** `RandomSquareCube.java`

``` java
import java.util.Random;

class SquareThread extends Thread {
    int number;
    SquareThread(int n) { number = n; }

    public void run() {
        System.out.println("Square of " + number + " = " + (number * number));
    }
}

class CubeThread extends Thread {
    int number;
    CubeThread(int n) { number = n; }

    public void run() {
        System.out.println("Cube of " + number + " = " + (number * number * number));
    }
}

class RandomThread extends Thread {
    public void run() {
        Random random = new Random();

        for (int i = 1; i <= 5; i++) {
            int number = random.nextInt(100);
            System.out.println("Random number: " + number);

            if (number % 2 == 0)
                new SquareThread(number).start();
            else
                new CubeThread(number).start();

            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
                break;
            }
        }
    }
}

public class RandomSquareCube {
    public static void main(String[] args) {
        new RandomThread().start();
    }
}
```

**Result:** Three thread roles are demonstrated. The random thread
generates five numbers at one-second intervals and starts the matching
calculation thread.

------------------------------------------------------------------------

## Q14. Multiple Threads and Synchronization

**Aim:** To demonstrate thread creation, execution and synchronization.

**Algorithm:** Create a shared object with a synchronized method; create
two worker threads that call the method; start both threads and observe
that access to the shared method is controlled.

**File:** `ThreadSynchronization.java`

``` java
class SharedPrinter {
    synchronized void printMessage(String message) {
        for (int i = 1; i <= 3; i++) {
            System.out.println(message + " - " + i);
            try {
                Thread.sleep(300);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
                return;
            }
        }
    }
}

class Worker extends Thread {
    SharedPrinter printer;
    String message;

    Worker(SharedPrinter p, String msg) {
        printer = p;
        message = msg;
    }

    public void run() {
        printer.printMessage(message);
    }
}

public class ThreadSynchronization {
    public static void main(String[] args) {
        SharedPrinter p = new SharedPrinter();

        Worker t1 = new Worker(p, "Thread 1");
        Worker t2 = new Worker(p, "Thread 2");

        t1.start();
        t2.start();
    }
}
```

**Result:** Two threads execute, while the synchronized method allows
only one thread at a time to use the shared printer method.

------------------------------------------------------------------------

## Q15. Copy Contents from One File to Another

**Aim:** To copy the contents of a source file into a destination file
and display the destination contents.

**Algorithm:** Create source and destination paths; read source using
`FileInputStream`; write bytes using `FileOutputStream`; read and
display destination; handle `IOException`.

**File:** `FileCopyDemo.java`

``` java
import java.io.*;

public class FileCopyDemo {
    public static void main(String[] args) {
        String source = "source.txt";
        String destination = "destination.txt";

        try (FileInputStream in = new FileInputStream(source);
             FileOutputStream out = new FileOutputStream(destination)) {

            int data;
            while ((data = in.read()) != -1) {
                out.write(data);
            }

            System.out.println("File copied successfully.");

        } catch (IOException e) {
            System.out.println("File error: " + e.getMessage());
            return;
        }

        try (BufferedReader br = new BufferedReader(new FileReader(destination))) {
            String line;
            System.out.println("Destination file contents:");
            while ((line = br.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            System.out.println("Read error: " + e.getMessage());
        }
    }
}
```

**Before running:** Create `source.txt` in the program's working
directory and add some text.

**Result:** The source file is copied to the destination file and its
contents are displayed.

------------------------------------------------------------------------

## Q16. Create, Read, Write and Copy a File

**Aim:** To perform basic file operations and handle file exceptions.

**Algorithm:** Create a file; write text; read and display it; copy its
contents to another file; handle `IOException`.

**File:** `BasicFileOperations.java`

``` java
import java.io.*;

public class BasicFileOperations {
    public static void main(String[] args) {
        File source = new File("myfile.txt");
        File copy = new File("myfile_copy.txt");

        try {
            if (source.createNewFile())
                System.out.println("File created.");
            else
                System.out.println("File already exists.");

            try (FileWriter writer = new FileWriter(source)) {
                writer.write("Java file handling example.\n");
                writer.write("Create, write, read and copy.");
            }

            System.out.println("File contents:");
            try (BufferedReader reader = new BufferedReader(new FileReader(source))) {
                String line;
                while ((line = reader.readLine()) != null)
                    System.out.println(line);
            }

            try (FileInputStream in = new FileInputStream(source);
                 FileOutputStream out = new FileOutputStream(copy)) {
                int data;
                while ((data = in.read()) != -1)
                    out.write(data);
            }

            System.out.println("File copied to " + copy.getName());

        } catch (IOException e) {
            System.out.println("File operation failed: " + e.getMessage());
        }
    }
}
```

**Result:** File creation, writing, reading and copying are performed
with exception handling.

------------------------------------------------------------------------

## Q17. Generic Function to Find Maximum and Minimum

**Aim:** To use a generic method to find the maximum and minimum values
in an array.

**Algorithm:** Create a generic method with a type bound implementing
`Comparable`; compare each element; update maximum and minimum; display
the results.

**File:** `GenericMaxMin.java`

``` java
public class GenericMaxMin {
    public static <T extends Comparable<T>> void findMaxMin(T[] values) {
        T max = values[0];
        T min = values[0];

        for (int i = 1; i < values.length; i++) {
            if (values[i].compareTo(max) > 0)
                max = values[i];

            if (values[i].compareTo(min) < 0)
                min = values[i];
        }

        System.out.println("Maximum = " + max);
        System.out.println("Minimum = " + min);
    }

    public static void main(String[] args) {
        Integer[] numbers = {10, 50, 20, 5, 40};
        findMaxMin(numbers);

        String[] names = {"Apple", "Orange", "Banana"};
        findMaxMin(names);
    }
}
```

**Sample output for integers:** `Maximum = 50`, `Minimum = 5`.

**Result:** A generic method finds maximum and minimum values from a set
of comparable elements.

------------------------------------------------------------------------

## Q18. Generic Class to Store and Display Different Data Types

**Aim:** To demonstrate a generic class that stores and displays
different data types.

**Algorithm:** Define a class with type parameter `T`; store a value
using a constructor; display it; create objects with different types.

**File:** `GenericClassDemo.java`

``` java
class DataStore<T> {
    T value;

    DataStore(T v) {
        value = v;
    }

    void display() {
        System.out.println("Stored value: " + value);
    }
}

public class GenericClassDemo {
    public static void main(String[] args) {
        DataStore<Integer> a = new DataStore<>(100);
        DataStore<String> b = new DataStore<>("Hello Java");
        DataStore<Double> c = new DataStore<>(25.75);

        a.display();
        b.display();
        c.display();
    }
}
```

**Result:** The generic class stores and displays Integer, String and
Double values.

------------------------------------------------------------------------

## Q19. JavaFX Student Registration Form

**Question:** Use Label, TextField, RadioButton, CheckBox, ChoiceBox and
Button. Display entered details when the button is clicked.

**Aim:** To create a student registration form using JavaFX controls and
layouts.

**Algorithm:** Create a JavaFX application; add labels and input
controls; group radio buttons; add a choice box and check box; place
controls in a layout; on button click, display entered details.

**File:** `StudentRegistrationFX.java`

``` java
import javafx.application.Application;
import javafx.geometry.Insets;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.GridPane;
import javafx.stage.Stage;

public class StudentRegistrationFX extends Application {
    public void start(Stage stage) {
        Label title = new Label("Student Registration");

        Label nameLabel = new Label("Name:");
        TextField nameField = new TextField();

        Label ageLabel = new Label("Age:");
        TextField ageField = new TextField();

        Label genderLabel = new Label("Gender:");
        RadioButton male = new RadioButton("Male");
        RadioButton female = new RadioButton("Female");
        ToggleGroup genderGroup = new ToggleGroup();
        male.setToggleGroup(genderGroup);
        female.setToggleGroup(genderGroup);

        CheckBox hostel = new CheckBox("Hostel required");

        Label deptLabel = new Label("Department:");
        ChoiceBox<String> department = new ChoiceBox<>();
        department.getItems().addAll("CSE", "ECE", "IT", "EEE");
        department.setValue("CSE");

        Button submit = new Button("Submit");
        Label result = new Label();

        submit.setOnAction(e -> {
            RadioButton selected = (RadioButton) genderGroup.getSelectedToggle();
            String gender = selected == null ? "Not selected" : selected.getText();

            result.setText("Name: " + nameField.getText()
                    + "\nAge: " + ageField.getText()
                    + "\nGender: " + gender
                    + "\nDepartment: " + department.getValue()
                    + "\nHostel: " + (hostel.isSelected() ? "Yes" : "No"));
        });

        GridPane root = new GridPane();
        root.setPadding(new Insets(15));
        root.setHgap(10);
        root.setVgap(10);

        root.add(title, 0, 0, 2, 1);
        root.add(nameLabel, 0, 1);
        root.add(nameField, 1, 1);
        root.add(ageLabel, 0, 2);
        root.add(ageField, 1, 2);
        root.add(genderLabel, 0, 3);
        root.add(male, 1, 3);
        root.add(female, 1, 4);
        root.add(hostel, 1, 5);
        root.add(deptLabel, 0, 6);
        root.add(department, 1, 6);
        root.add(submit, 1, 7);
        root.add(result, 1, 8);

        stage.setTitle("Student Registration Form");
        stage.setScene(new Scene(root, 400, 400));
        stage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
```

**JavaFX setup note:** Add the JavaFX SDK libraries to the project and
configure VM arguments, for example:

`--module-path "PATH_TO_FX/lib" --add-modules javafx.controls`

Replace `PATH_TO_FX` with the actual JavaFX SDK folder on your computer.
This example uses controls from `javafx.controls`.

**Result:** A JavaFX registration form accepts student details and
displays them when Submit is clicked.

------------------------------------------------------------------------

## Q20. JavaFX Editor Application with Menu

**Aim:** To create a simple JavaFX text editor with a MenuBar, Menu and
MenuItems.

**Algorithm:** Create a `TextArea`; create a MenuBar with File menu; add
New, Open, Save and Exit menu items; connect each item to its action;
display the stage.

**File:** `JavaFXEditor.java`

``` java
import javafx.application.Application;
import javafx.stage.Stage;
import javafx.stage.FileChooser;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.BorderPane;
import java.io.*;

public class JavaFXEditor extends Application {
    public void start(Stage stage) {
        TextArea textArea = new TextArea();

        Menu fileMenu = new Menu("File");
        MenuItem newItem = new MenuItem("New");
        MenuItem openItem = new MenuItem("Open");
        MenuItem saveItem = new MenuItem("Save");
        MenuItem exitItem = new MenuItem("Exit");

        fileMenu.getItems().addAll(newItem, openItem, saveItem,
                new SeparatorMenuItem(), exitItem);

        MenuBar menuBar = new MenuBar(fileMenu);

        newItem.setOnAction(e -> textArea.clear());

        openItem.setOnAction(e -> {
            FileChooser chooser = new FileChooser();
            File file = chooser.showOpenDialog(stage);
            if (file != null) {
                try (BufferedReader reader = new BufferedReader(new FileReader(file))) {
                    textArea.clear();
                    String line;
                    while ((line = reader.readLine()) != null)
                        textArea.appendText(line + "\n");
                } catch (IOException ex) {
                    showError(ex.getMessage());
                }
            }
        });

        saveItem.setOnAction(e -> {
            FileChooser chooser = new FileChooser();
            File file = chooser.showSaveDialog(stage);
            if (file != null) {
                try (FileWriter writer = new FileWriter(file)) {
                    writer.write(textArea.getText());
                } catch (IOException ex) {
                    showError(ex.getMessage());
                }
            }
        });

        exitItem.setOnAction(e -> stage.close());

        BorderPane root = new BorderPane();
        root.setTop(menuBar);
        root.setCenter(textArea);

        stage.setTitle("Simple JavaFX Editor");
        stage.setScene(new Scene(root, 600, 400));
        stage.show();
    }

    private void showError(String message) {
        Alert alert = new Alert(Alert.AlertType.ERROR);
        alert.setContentText(message);
        alert.showAndWait();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
```

**JavaFX setup note:** Add the JavaFX SDK and configure the VM argument:

`--module-path "PATH_TO_FX/lib" --add-modules javafx.controls`

Replace `PATH_TO_FX` with your JavaFX SDK location.

**Result:** A JavaFX editor is created with New, Open, Save and Exit
menu actions.

------------------------------------------------------------------------

# Quick Revision -- Key Java Concepts

  -----------------------------------------------------------------------
  Concept                             Meaning
  ----------------------------------- -----------------------------------
  Class                               Blueprint for creating objects

  Object                              Instance of a class

  Constructor                         Special member used to initialize
                                      an object

  Default constructor                 Constructor with no parameters

  Parameterized constructor           Constructor that receives
                                      parameters

  Copy constructor                    User-written constructor that
                                      copies another object's values

  Inheritance                         One class acquiring members of
                                      another class

  Method overriding                   Child class provides its own
                                      implementation of a parent method

  Abstract class                      Class that cannot be instantiated
                                      directly and may contain abstract
                                      methods

  Interface                           Contract that implementing classes
                                      agree to implement

  Exception                           An event that interrupts normal
                                      program flow

  `try`                               Encloses code that may cause an
                                      exception

  `catch`                             Handles an exception

  `finally`                           Block normally executed after
                                      try/catch

  `throw`                             Explicitly throws an exception

  `throws`                            Declares possible exceptions in a
                                      method signature

  Thread                              A path of execution within a
                                      program

  `synchronized`                      Controls concurrent access to a
                                      shared method or block

  Generic `<T>`                       Type parameter used to write
                                      reusable type-safe code

  JavaFX                              Java GUI framework

  `FileInputStream`                   Reads bytes from a file

  `FileOutputStream`                  Writes bytes to a file
  -----------------------------------------------------------------------

## Practical Exam Checklist

-   Write **Aim, Algorithm, Program, Sample Output and Result** for each
    question.
-   Check that the public class name matches the filename.
-   Compile and run each program separately in Eclipse.
-   Practise explaining the key statements, not only memorizing the
    code.
-   For file programs, ensure the input file exists in the working
    directory.
-   For JavaFX programs, configure the JavaFX SDK before the practical;
    a normal JDK alone is not enough.
-   The sample values and class names here are practice choices. Keep
    the question's required class names and formulas when your lecturer
    specifies them.
