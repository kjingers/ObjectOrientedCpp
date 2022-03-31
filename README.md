# Object Opiented CPP

## Pointers and Dynamic Memory
```
#include <iostream>
using namespace std;

int main() {
  int *p = new int;   // dynamic memory reserved for an integer 
  *p = 10;   // the object is assigned the value of 10
  cout << "The value of the object p points to: " << *p << endl;
  
  int *q = p;   // both pointers point to the same object
  cout << "The value of the object q points to: " << *q << endl;
  
  double *arr = new double[500]; // an array of size 500 has been created in the heap
  arr[0] = 50;
  cout << "arr[0]: " << arr[0] << endl;
  
  // delete pointers and free up space
  delete p, q;
  delete[] arr;
  cout << "p now points to a random value and should not be accesed: " << *p << endl;
  p = new int(5); // The pointer can now be re-used to point to something else
  cout << "The value of the object p points to: " << *p << endl;
}
```
Pass By Pointer:
```
#include <iostream>
using namespace std;

void square(int *a){ // the function takes a pointer and replaces the value with its square
  if(a != NULL){
    *a = (*a) * (*a);
  }
}

int main() {
  int *p = new int(5);
  cout << "The value of p before the function call: " << *p << endl;
  square(p);
  cout << "The value of p after the function call: " << *p << endl;
}
```

## Friend Functions
When you pass an object to a function, the function can alter the private variables.
```
#include <iostream>
#include <string>

using namespace std;

class Ball{
  double radius;
  string color;
  
  public:
  Ball(){
    radius = 0;
    color = "";
  }
  
  Ball(double r, string c){
    radius = r;
    color = c;
  }
  
  void printVolume();
  void printRadius();
  
  // The friend keyword specifies that this is a friend function
  friend void setRadius(Ball &b, double r); 
    
};

// This is a member function that calculates the volume.
void Ball::printVolume(){
  cout << (4/3) * 3.142 * radius * radius * radius << endl;
}

void Ball::printRadius(){
  cout << radius << endl;
}

// The implementation of our friend function
void setRadius(Ball &b, double r){
  b.radius = r;
}

 int main(){
   Ball b(30, "green");
   cout << "Radius: ";
   b.printRadius();
   setRadius(b, 60);
   cout << "New radius: ";
   b.printRadius();
   cout << "Volume: ";
   b.printVolume();
 }
```
## Data Hiding
main.cpp
```
#include <iostream>
#include "./Circle.h"

using namespace std;


int main() {
  Circle c(5);
  cout << "Area: " << c.area() << endl;
  cout << "Perimeter: " << c.perimeter() << endl;
}
```
Circle.h
```
#ifndef CIRCLE_H
#define CIRCLE_H

// Declare all the members of the class here.
class Circle{
  double radius;
  double pi;
  
  public:
  Circle ();
  Circle(double r);  
  double area();  
  double perimeter();
};
#endif
```
Circle.cpp
```
#include "Circle.h"

Circle::Circle(){
  radius = 0;
  pi = 3.142;
}

Circle::Circle(double r){
  radius = r;
  pi = 3.142;
}

double Circle::area(){
  return pi * radius * radius;
}

double Circle::perimeter(){
  return 2 * pi * radius;
}
```

## Object Oriented

```

```

