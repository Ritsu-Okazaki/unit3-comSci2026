![image](https://github.com/user-attachments/assets/be8a0e50-733e-4d92-93a2-d26ecdf3a7fb)# This is quiz 44

## Code solution
```.py
class rainDrops:
    def __init__(self):
        pass

    def pour(self,n):
        result = ""
        if n%3==0:
            result += "Pling"
        if n%5==0:
            result += "Plang"
        if n%7==0:
            result += "Plong"
        if result == "":
            result = "34"
        return result

print(rainDrops().pour(28))
print(rainDrops().pour(30))
print(rainDrops().pour(34))
```

## Proof of work
![image](https://github.com/user-attachments/assets/28b23b50-4518-4c1b-8a3c-25edc261cd99)

## UML Diagram
![image](https://github.com/user-attachments/assets/a4245116-e279-468e-b458-6025a67174b9)

## Paper solution
![20250225_001426](https://github.com/user-attachments/assets/dd941e96-d464-4c7d-a388-c69fe4c7917f)
