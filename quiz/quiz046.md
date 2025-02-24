# This is quiz 46

## Code solution
```.py
class Citizen:
    def __init__(self, name, city, status):
        self.name = name
        self.city = city
        self.status = status

class Employee(Citizen):
    def __init__(self,name,city,status,annual_salary):
        super().__init__(name,city,status)
        self.annual_salary = annual_salary

class PartTimeEmployee(Employee):
    def __init__(self,name,city,status,annual_salary,fraction,union_member):
        super().__init__(name,city,status,annual_salary)
        self.fraction = fraction
        self.union_member = union_member
```

## UML Diagram
![image](https://github.com/user-attachments/assets/1cf915e5-014f-48ef-8c68-186d15a930ae)

## Paper solution
![20250225_005544](https://github.com/user-attachments/assets/fcc3582c-90c9-4cdf-a91d-a3fd781f618e)
