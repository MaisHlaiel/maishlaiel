// Create a namespace for the project
namespace EmployeeComparisonApp
{
// Create the Employee class
public class Employee
{
// Store the employee's ID
public int Id { get; set; }

// Store the employee's first name
public string FirstName { get; set; }

// Store the employee's last name
public string LastName { get; set; }

// Overload the == operator to compare Employee objects by their Id
public static bool operator ==(Employee emp1, Employee emp2)
{
// Check if both objects are null
if (ReferenceEquals(emp1, emp2))
return true;

// Check if either object is null
if (emp1 is null || emp2 is null)
return false;

// Return true if the Id values match
return emp1.Id == emp2.Id;
}

// Overload the != operator (required when overloading ==)
public static bool operator !=(Employee emp1, Employee emp2)
{
// Return the opposite result of ==
return !(emp1 == emp2);
}

// Override Equals so it uses the overloaded == operator
public override bool Equals(object obj)
{
// Check if the object is an Employee
if (obj is Employee employee)
{
return this == employee;
}

return false;
}

// Override GetHashCode because Equals was overridden
public override int GetHashCode()
{
// Return the hash code of the Id
return Id.GetHashCode();
}
}
}
