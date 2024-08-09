# week5
#include <iostream>
#include <string>
using namespace std;

struct Student {
  string name;
  int marks;
  Student* next;
};

class Stack {
private:
  Student* top;
public:
  Stack() {
    top = nullptr; // Initialize top to nullptr
  }

  // Function to add a student to the stack
  void push(string name, int marks) {
    Student* newStudent = new Student();
    newStudent->name = name;
    newStudent->marks = marks;
    newStudent->next = top;
    top = newStudent;
  }

  // Function to remove a student from the stack
  void pop() {
    if (top == nullptr) {
      cout << "Stack is empty. Cannot pop." << endl;
      return;
    }
    Student* temp = top;
    top = top->next;
    delete temp;
  }

  // Function to display the students in the stack
  void display() {
    Student* temp = top;
    while (temp != nullptr) {
      cout << "Name: " << temp->name << ", Marks: " << temp->marks << endl;
      temp = temp->next;
    }
  }
};

int main() {
  Stack stack;
  stack.push("John", 85);
  stack.push("Alice", 92);
  stack.push("Bob", 78);

  cout << "Students in the stack:" << endl;
  stack.display();

  stack.pop();

  cout << "Students in the stack after pop:" << endl;
  stack.display();

  return 0;
}
