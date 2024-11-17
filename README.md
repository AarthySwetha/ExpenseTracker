# ExpenseTracker
import java.util.Scanner;

// Base class (Inheritance and Access Specifiers)
class Expense {
    protected String category; // Access specifier: protected
    protected double amount;

    // Constructor
    public Expense(String category, double amount) {
        this.category = category;
        this.amount = amount;
    }

    // Method to display expense details
    public void displayDetails() {
        System.out.println("Category: " + category + ", Amount: $" + amount);
    }
}

// Derived class for MonthlyExpense (Inheritance)
class MonthlyExpense extends Expense {
    private String month; // Access specifier: private

    // Constructor
    public MonthlyExpense(String category, double amount, String month) {
        super(category, amount); // Calling parent class constructor
        this.month = month;
    }

    // Method overriding
    @Override
    public void displayDetails() {
        System.out.println("Month: " + month + ", Category: " + category + ", Amount: $" + amount);
    }
}

// Main class
public class ExpenseTracker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Using an array to store expenses
        System.out.println("How many expenses do you want to add?");
        int n = scanner.nextInt();
        scanner.nextLine(); // Consume newline

        MonthlyExpense[] expenses = new MonthlyExpense[n];

        // Adding expenses
        for (int i = 0; i < n; i++) {
            System.out.println("Enter details for Expense " + (i + 1) + ":");

            System.out.print("Category: ");
            String category = scanner.nextLine();

            System.out.print("Amount: ");
            double amount = scanner.nextDouble();
            scanner.nextLine(); // Consume newline

            System.out.print("Month: ");
            String month = scanner.nextLine();

            // Creating and storing the expense object
            expenses[i] = new MonthlyExpense(category, amount, month);
        }

        // Displaying all expenses
        System.out.println("\nExpense Details:");
        for (MonthlyExpense expense : expenses) {
            expense.displayDetails(); // Polymorphism: Method overriding
        }

        scanner.close();
    }
}
