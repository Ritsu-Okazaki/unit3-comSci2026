# This is quiz 32

## Code solution
```.py
class HumanResources:
    def __init__(self, name, occupation):
        self.name = name
        self.email = ""
        self.nationality = ""
        self.occupation = occupation
    
    def set_email(self):
        self.email = f"{self.name.split()[0]}@{self.name.split()[1]}.com"
        return
    
    def set_nationality(self, name):
        self.nationality = name
        return
    
    def get_email(self):
        return self.email
    
    def greet(self):
        return f"hello {self.name} a great {self.nationality}!"
```
