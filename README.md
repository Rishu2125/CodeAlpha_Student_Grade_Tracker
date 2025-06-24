# CodeAlpha_Student_Grade_Tracker
package studentsGrade;

import java.util.ArrayList;
import java.util.Scanner;

class Students {
    String name;
    int roll;
    double grade;
    public Students(String name,int roll,double grade)
    {
        this.name=name;
        this.roll=roll;
        this.grade=grade;
    }
    void displayInfo() {
        System.out.println("Roll No: " + roll + ", Name: " + name + ", Grade: " + grade);
    }

}
public class GradeManagementSystem {
    static ArrayList<Students> students = new ArrayList<>();
    static Scanner sc = new Scanner(System.in);

    static void addStudent() {
        System.out.print("Enter student's name: ");
        String name = sc.nextLine();

        System.out.print("Enter roll number: ");
        int rollNo = sc.nextInt();

        System.out.print("Enter grade: ");
        double grade = sc.nextDouble();

        students.add(new Students(name, rollNo, grade));
        System.out.println("Student added successfully.");

    }

    static void viewStudents() {
        if (students.isEmpty()) {
            System.out.println("No student records found.");
        } else {
            System.out.println("\n--- Student List ---");
            for (Students s : students) {
                s.displayInfo();
            }

        }
    }

    static void calculateAverage() {
        if (students.isEmpty()) {
            System.out.println("No students to calculate average.");
            return;
        }

        double total = 0;
        for (Students s : students) {
            total += s.grade;
        }

        double avg = total / students.size();
        System.out.printf("Average Grade: " + avg);
    }
    static void displayHighestScore() {
        if (students.isEmpty()) {
            System.out.println("No student records found.");
            return;
        }

        double highest = students.get(0).grade;
        for (Students s : students) {
            if (s.grade > highest) {
                highest = s.grade;
            }
        }

        System.out.println("--- Student with the Highest Grade (" + highest + ") ---");
        for (Students s : students) {
            if (s.grade == highest) {
                s.displayInfo();
            }
        }
    }
    static void displayLowestScore() {
        if (students.isEmpty()) {
            System.out.println("No student records found.");
            return;
        }

        double lowest = students.get(0).grade;
        for (Students s : students) {
            if (s.grade < lowest) {
                lowest = s.grade;
            }
        }

        System.out.println("--- Student(s) with the Lowest Grade (" + lowest + ") ---");
        for (Students s : students) {
            if (s.grade == lowest) {
                s.displayInfo();
            }
        }
    }




    public static void main(String[] args) {
        int choice;
        do {
            System.out.println("\n--- Student Grade Management System ---");
            System.out.println("1. Add Student");
            System.out.println("2. View Students");
            System.out.println("3. Calculate Average Grade");
            System.out.println("4. highest score ");
            System.out.println("5.lowest score");
            System.out.println("6. Exit");
            System.out.print("Enter your choice: ");

            choice = sc.nextInt();
            sc.nextLine();

            switch (choice) {
                case 1 -> addStudent();
                case 2 -> viewStudents();
                case 3 -> calculateAverage();
                case 4-> displayHighestScore();
                case 5->displayLowestScore();
                case 6 -> System.out.println("Exiting system. Goodbye!");
                default -> System.out.println("Invalid choice. Please try again.");
            }
        } while (choice != 6);

    }
}
