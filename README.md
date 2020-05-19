

<h2>Overview:</h2>

• In this you will create an employee database application by fulfilling the
requirements given below. You must first create the classes as described. Given there are more requirements in this, please read the whole document carefully and adjust your code accordingly.
</br>
• After creating required classes, write a program that will use these classes to build an
application for an Employee Database. All employee data is stored in a file called
“empdata.dat”. This file is provided and will be used to test your program (don’t change
this file). Each time you run the program, the user is allowed to repeatedly select from the
seven choices described below:
1. Add a new employee
2. Display employees’ information
3. Compute and print the name and compensation of all employees
4. Search employees by name
5. Check basic statistics of employees
6. Calculate the reimbursement of one employee
7. Exit the application

• The first time you execute the program, your file will have several employees in it. They
are used to test your program. As you add employees to the program, it may contain more
employees. When you exit the application, all these employees will be stored in a new
data file. This setting doesn’t reflect the real use case, but it fits the final exam purpose
(i.e. you will never change the original empdata.dat file so you can debug your program
until you get the correct outputs).

• This program splits coding task and testing task into small pieces so you don’t need to worry about how
to complete and test a “huge” program. Just make sure you read and follow all the instructions closely. The program template and this document should complement each other.

<h3>Requirements:</h3>
<b>First step, create the classes as described.</b></br>
• Create a base class Employee that has the following attributes:<br>
o Employee’s name (string)<br>
o Employee’s address (string)<br>
o Vehicle data (Vehicle object).<br>
• The child classes FullTimeEmployee, HourlyEmployee and Consultant that inherit from
Employee class have the following additional properties<br>
o FullTimeEmployee – salary (float).<br>
o HourlyEmployee - hoursWorked (int) and hourlyRate (float).<br>
o Consultant – hoursWorked (int) and ProjectType (valid values are 1, 2, and 3).<br><br>
• The child class Management inherits from both FullTimeEmployee class and Consultant
class. Management class has inherited three attributes (i.e. name, address, and vehicle object)
indirectly from Employ class, one attribute (i.e. salary) from FullTimeEmployee class and
two attributes (i.e. hours worked and project type) from Consultant class.<br><br>
• All these classes have the __init__ method as well as the get and set methods. In addition,
they have additional methods, i.e. get_compensation() and get_reimbursement() as described
below. Function get_compensation() returns weekly compensation and function
get_reimbursement() returns weekly reimbursement.<br><br>
• Compensation (weekly) for any employee type doesn’t call for “outside” information. In
other words, all information needed is available after initializing/creating an object.
Compensation is to be computed as follows:<br>
o FullTimeEmployee: Compensation is salary minus taxes and taxes are calculated based
on the tax rate in the table below. Please notice that this format calculates the annual
compensation and what this function needs to return is the weekly compensation
(assuming there are 52 weeks per year).<br>
<table><tr><th>Salary</th> <th>TaxRate</th></tr>
<tr><td>$45, 000 or less</td> <td>18%</td></tr>
<tr><td> > $45,000 and <= $82,000</td> <td>18% for the first 45000, 28% for the rest</td></tr>
<tr><td> > $ 82,000</td> <td>18% for the first 45000, 28% for the amount
between 45000 and 82000, and 33% for the
rest</td></tr></table>
<small>For example, someone whose salary is $123,000 will pay 18% on the first 45,000, 28% on the
next (82,000 – 45,000) and 33% on the remaining (123,000 – 82,000)</small><br>
o HourlyEmployee: Compensation is hoursWorked times hourlyRate for the first 40 hours.
For hours in excess of 40 hours, the hourly rate is 1.8 times the regular hourly rate. The
sum of the two is weekly compensation.<br>
For example, someone whose hourlyRate is $12.50 and who has worked 48 hours will
earn 40 * $12.5 + 8 * $12.5 * 1.8.<br>
o Consultant: Compensation is HourlyRate times the hours worked (this is weekly
compensation). HourlyRate for Consultants is computed based on the ProjectType as
given in the table below:<br>
<table><tr><th>Project Type </th><th> HourlyRate</th></tr>
<tr><td>1 </td><td> $55.00 </td></tr>
<tr><td> 2 </td><td> $70.00 </td></tr>
<tr><td> 3 </td><td> $85.00 </td></tr></table>
o Management: Total weekly compensation is the sum of the compensation from
FullTimeEmployee role (i.e. from salary) and the compensation from Consultant role (i.e.
from hours worked on a project).<br>
• Reimbursement (weekly) for every employee type calls for “outside” information as input
argument(s). In other words, the information is not provided when initializing/creating an
object and there is no corresponding attribute. Reimbursement is to be computed as follows:<br>
o FullTimeEmployee: This method will take an argument which is the annual expense. If
the annual expense is no more than $10,000, then the total reimbursement will be equal to
the annual expense. If the annual expense is more than $10,000, then the total reimbursement will be equal to $10,000 plus 50 percent of the amount of the annual expense that exceeds $10,000. Please notice that this format calculates the annual reimbursement and what this function needs to return is the weekly reimbursement<br>
(assuming there are 52 weeks per year). For example, someone whose annual expense is $12,000 will get $10,000 plus 50% on the remaining ($12,000 – $10,000), totaling $11,000. <br>
<table><tr><th>Expense</th> <th>Reimbursement Rate</th></tr>
<tr><td>$10, 000 or less</td><td> 100% </td></tr>
<tr><td> > $10,000</td> <td>100% for the first $10,000, 50% for the rest </td></tr> </table>
o HourlyEmployee: This method will take an argument which is the weekly expense. If the
weekly expense is no more than $100, then the total reimbursement will be equal to the
weekly expense. If the weekly expense exceeds $100, then the total reimbursement will
be equal to $100. For example, someone whose weekly expense is $80 will get a weekly
compensation of $80 while someone whose weekly expense is $120 will get a weekly
compensation of $100. <br>
o Consultant: This method will take an argument which is the weekly expense. The weekly
reimbursement is the product of weekly expense and the reimbursement rate (which is
based on the project type as given in the table below). For example, three consultants all
have a weekly expense of $100, then the one working on type 1 project will get $100, the
one working on type 2 project will get $90, and the one working on type 3 will get $80. <br>
<table><tr><th>Project Type </th><th>Reimbursement Rate</th></tr>
<tr><td>1</td><td> 100% </td></tr>
<tr><td>2 </td><td>90% </td></tr>
<tr><td>3</td><td> 80% </td></tr></table>
o Management: This method will take two arguments. The first argument is the annual
expense which fits the FullTimeEmployee role. The second argument is the weekly
expense which fits the Consultant role. Total reimbursement is the sum of the  reimbursement from FullTimeEmployee role (i.e. from the annual expense) and the compensation from Consultant role (i.e. from the weekly expense). <br><br>
• The Vehicle class is as described below: It has four instance variables – make (string),
model (string), year of manufacture (int) and mileage (int). It should have a constructor
(__init__) method which accepts values for all of the instance variables. You should use
aggregation to include a Vehicle object to your Employee data. <br>
Second step, write a program to take user inputs to work on the Employee Database:
(The information here just provides some simple guidelines; see program template for
more detailed and specific requirements.)<br>
<h3>The Employee Database application contains seven options:</h3>
Option 1: Accept input for new Employees. If the user chooses option 1, the program should ask
the type of employee first and then guide the user to provide all required information. New
employee will be added to a temporary “object container” and written into a new database when
program exits.<br>
Option 2: Display employee information. If the user chooses option 2, the program should ask
one question (introduced in the program template) and then display employee information.<br>
Option 3: List the name of all employees along with the compensation received by each.<br>
Option 4: Search for employees by name. If the user chooses option 4, the program should ask
for a name and then display all employees that match the name search.<br>
Option 5: Display basic statistics (defined in the program template).<br>
Option 6: Calculate the reimbursement of one employee. If the user chooses option 6, the
program should ask for a name and let the user to select one employee. Then certain information
will be asked (depending on employee type) to calculate the weekly reimbursement.<br>
Option 7: Exit the system after writing all information to a new database/file. The program
should ask if the user really wants to exit the system before closing the program.<br>
If users select options 1-6, this program should show the option menu again after completing the
required job. If users select option 7 and want to exit the system, this program will end then.
Your program should also be able to handle exceptions in some settings. The detailed
requirements are provided in the code template. Normally when users enter invalid values, the
program should print an appropriate message and ask the user to re-enter a valid value.
