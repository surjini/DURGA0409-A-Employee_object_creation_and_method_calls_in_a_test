## DURGA0409-A-Employee_object_creation_and_method_calls_in_a_test
## REG NUM :25015534
## NAME :R.Surjini
## EXPERIMENT –6 Design a SystemVerilog class Employee and demonstrate its usage through object creation and method calls in a testbench.
 ## Aim
To design a SystemVerilog class named Employee with data members and methods, and verify the usage of class through object creation, method calling, salary modification, and bonus calculation using EDA Playground.
##  Tool Used
Xilinx Vivado (SystemVerilog Simulation)

## Theory

SystemVerilog supports Object-Oriented Programming (OOP) through classes, enabling advanced modeling and testbench generation.
 Class in SystemVerilog
A class is a user-defined data type containing:
Data members → variables
Functions / Methods → behavior

Constructor

Executed during object creation:
function new(int id, string n, real s);

 Object Creation
Employee e1 = new(101,"Ram",50000);

 Method Calling
e1.display();
e1.update_salary(55000);
e1.calc_bonus();

## SystemVerilog Program
```
// Employee class definition
class Employee;
  // Attributes
  int emp_id;       // Employee ID
  string name;      // Employee name
  real salary;      // Employee salary

  // Constructor to initialize employee details
  function new(int id, string n, real s);
    emp_id = id;
    name   = n;
    salary = s;
  endfunction

  // Method to update salary
  function void update_salary(real new_salary);
    salary = new_salary;
    $display("Updated salary of %s (ID=%0d) is %.2f", name, emp_id, salary);
  endfunction

  // Method to calculate yearly bonus (10% of salary)
  function real calc_bonus();
    return 0.1 * salary;
  endfunction

  // Method to display employee details
  function void display();
    $display("Employee ID: %0d, Name: %s, Salary: %.2f", emp_id, name, salary);
  endfunction
endclass
```

## TestBench 
```
// Testbench module
module test;
  Employee e1, e2;  // Declare employee objects

  initial begin
    // Object creation
    e1 = new(101, "Ram", 50000);
    e2 = new(102, "Deva", 60000);

    // Display details
    e1.display();
    e2.display();

    // Update salary of employee 1
    e1.update_salary(55000);

    // Calculate and display bonus
    $display("Bonus of %s = %.2f", e1.name, e1.calc_bonus());
    $display("Bonus of %s = %.2f", e2.name, e2.calc_bonus());
  end
endmodule
```

## Output
![screenshot 2025-11-19 090452](https://github.com/user-attachments/assets/8bfab5db-be2f-4371-bec9-0ea116c8abfb)


## Result

The SystemVerilog Employee class was successfully implemented.
Objects were created using a constructor, employee details were displayed, salary was updated, and bonus was calculated and displayed using member methods.
Simulation was performed successfully in Vivado.
