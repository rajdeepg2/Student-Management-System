#include <stdio.h>
#include <string.h>

#define MAX_STUDENTS 100

struct Student {
  char first_name[50];
  char last_name[50];
  int rollNumber;
  int marks;
  char grade;
};

struct Student students[MAX_STUDENTS];
int numStudents = 0;

void addStudent() {
  struct Student newStudent;

  printf("Enter first name: ");
  scanf("%s", newStudent.first_name);

  printf("Enter last name: ");
  scanf("%s", newStudent.last_name);

  printf("Enter roll number: ");
  scanf("%d", &newStudent.rollNumber);

  printf("Enter marks: ");
  scanf("%d", &newStudent.marks);

  // Calculate grade based on marks
  if (newStudent.marks >= 90) {
    newStudent.grade = 'A';
  } else if (newStudent.marks >= 80) {
    newStudent.grade = 'B';
  } else if (newStudent.marks >= 70) {
    newStudent.grade = 'C';
  } else if (newStudent.marks >= 60) {
    newStudent.grade = 'D';
  } else {
    newStudent.grade = 'F';
  }

  students[numStudents++] = newStudent;

  printf("Student added successfully!\n");
}

void displayStudents() {
  if (numStudents == 0) {
    printf("No students found.\n");
    return;
  }

  printf("Student Data:\n");
  printf("----------------------------------------------------------\n");
  printf("Roll No.\tFirst Name\t\tLast Name\tMarks\tGrade\n");
  printf("----------------------------------------------------------\n");

  for (int i = 0; i < numStudents; i++) {
    printf("%d\t\t\t%s\t\t%s\t\t\t%d\t\t\t%c\n", students[i].rollNumber, students[i].first_name, students[i].last_name, students[i].marks, students[i].grade);
  }

  printf("----------------------------------------------------------\n");
}

void searchStudent() {
  int rollNumber;
  printf("Enter roll number to search: ");
  scanf("%d", &rollNumber);

  for (int i = 0; i < numStudents; i++) {
    if (students[i].rollNumber == rollNumber) {
      printf("Student Found:\n");
      printf("First Name: %s\n", students[i].first_name);
      printf("Last Name: %s\n", students[i].last_name);
      printf("Roll No.: %d\n", students[i].rollNumber);
      printf("Marks: %d\n", students[i].marks);
      printf("Grade: %c\n", students[i].grade);
      return;
    }
  }

  printf("Student with roll number %d not found.\n", rollNumber);
}

int main() {
  int choice;

  do {
    printf("\nStudent Management System\n");
    printf("----------------------------\n");
    printf("1. Add Student\n");
    printf("2. Display Students\n");
    printf("3. Search Student\n");
    printf("4. Quit\n");
    printf("----------------------------\n");
    printf("Enter your choice: ");
    scanf("%d", &choice);

    switch (choice) {
    case 1:
      addStudent();
      break;
    case 2:
      displayStudents();
      break;
    case 3:
      searchStudent();
      break;
    case 4:
      printf("Thank you for using the program!\n");
      break;
    default:
      printf("Invalid choice. Please try again.\n");
    }
  } while (choice != 4);

  return 0;
}


