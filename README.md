# CSE 3150: Homework 3 - Explaination

## Pointers

```
void addStudent(char* name, double gpa, char* names[], double gpas[], int& size, int capacity);
```
- In the overall program, ``` char* names[capacity];```, initializes a list of pointers to char. The pointer to this array is passed into the addStudent function
- Then at the current size (the index), a memory block is dynamically allocated with the pointer to that block is stored at the corresponding index of the array
- The ```char* name``` parameter, is the location of the buffer array that is used to read the name from the cin, which is later copied into the ```names[size]``` pointer location

```
void updateGPA(double* gpaPtr, double newGpa);
```
- In the updateGPA function, a pointer is used to directly update the GPA's via memory reference
- If the pointer is not null, then it is dereferenced value is the newGpa

```
void printStudent(const char* name, const double& gpa);
```
- The array of pointers to char is passed in the printStudent function

## Const

```
void printStudent(const char* name, const double& gpa);
double averageGPA(const double gpas[], int size);
```
- In printStudent the use of a pointer to the char name, that is constant. This means that the pointer cannot be modified
- In printStudent the use of ```const double& gpa``` is a reference to a double that is constant. This indicates that the double cannot be modified by this reference. 
- In averageGPA the use the constant array of double, also prevents modification of the values
- In general constants, provide safeguards in the program and show the intent of the variable

## References

```
void addStudent(char* name, double gpa, char* names[], double gpas[], int& size, int capacity);
void printStudent(const char* name, const double& gpa);
```
- In addStudent, the size variable is passed by reference, so that it is correctly incremented in the code, and not the a copy of the value
- In printStudent, gpa is a constant reference to a double value 
```
updateGPA(&gpas[index], newGpa);
```
- Since updateGPA expects a pointer to the intended GPA, the function argument passes the reference to the index of the gpa in the array

## Casting

```
std::cout << "Average GPA = " << avg << " (int=" << static_cast<int>(avg) << ")" << std::endl;
```
- In the rounded int version of the average GPA ```static_cast<int>``` is used to convert from double to int

## Exceptions

```
if (size == 0) {
        throw "No students";
    }
```
- In the averageGPA function, there is a condition to throw and expection of no students in the list if the size is 0

```
if (size >= capacity){
        throw "List full";
    }
```
- In the addStudent function, there is a concition that throws 'list full' if the current size is greater or equal to the capacity

## Control Flow

Control flow is implemented in various methods throughout the entire program:
- Switch cases
    - The main menu logic is driven using switch cases based on the user's selection
- If/Else
    - If statements are in close for various edge case checks for size and capacity limits, nullptrs, correct number of arguments to run the program, and checks index are within range
- Try/Catch
    - When adding a student or when trying to get the average there are try statements in place
    - If an exception is thrown, a catch statement, then catches the error message and prints if to std::cout
