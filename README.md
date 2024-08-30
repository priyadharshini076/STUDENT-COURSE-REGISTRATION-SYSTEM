# STUDENT-COURSE-REGISTRATION-SYSTEM
import java.util.ArrayList;
import java.util.Scanner;

class Course {
    String courseName;
    String courseID;

    Course(String courseName, String courseID) {
        this.courseName = courseName;
        this.courseID = courseID;
    }
}

class Student {
    String studentName;
    ArrayList<Course> registeredCourses;

    Student(String studentName) {
        this.studentName = studentName;
        this.registeredCourses = new ArrayList<>();
    }

    void registerCourse(Course course) {
        registeredCourses.add(course);
        System.out.println("Course " + course.courseName + " registered successfully.");
    }

    void viewRegisteredCourses() {
        System.out.println("Courses registered by " + studentName + ":");
        for (Course course : registeredCourses) {
            System.out.println(course.courseName + " (" + course.courseID + ")");
        }
    }
}

public class CourseRegistrationSystem {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Course> courses = new ArrayList<>();
        courses.add(new Course("Mathematics", "MATH101"));
        courses.add(new Course("Physics", "PHYS101"));
        courses.add(new Course("Chemistry", "CHEM101"));

        System.out.print("Enter student name: ");
        String studentName = scanner.nextLine();
        Student student = new Student(studentName);

        while (true) {
            System.out.println("\n1. Register for a course");
            System.out.println("2. View registered courses");
            System.out.println("3. Exit");
            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();
            scanner.nextLine();  // Consume newline

            if (choice == 1) {
                System.out.println("Available courses:");
                for (int i = 0; i < courses.size(); i++) {
                    System.out.println((i + 1) + ". " + courses.get(i).courseName);
                }
                System.out.print("Enter course number to register: ");
                int courseNumber = scanner.nextInt();
                scanner.nextLine();  // Consume newline
                if (courseNumber > 0 && courseNumber <= courses.size()) {
                    student.registerCourse(courses.get(courseNumber - 1));
                } else {
                    System.out.println("Invalid course number.");
                }
            } else if (choice == 2) {
                student.viewRegisteredCourses();
            } else if (choice == 3) {
                break;
            } else {
                System.out.println("Invalid choice. Please try again.");
            }
        }
        scanner.close();
    }
}
