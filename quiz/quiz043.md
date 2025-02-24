# This is quiz 43

## Code solution
```.py
class palNam:
    def __init__(self):
        return

    def get_pal_list(self,A,B):
        self.A = A
        self.B = B
        pals = []
        for i in range(A,B):
            if str(i) == str(i)[::-1]:
                pals.append(i)
        return pals

print(palNam().get_pal_list(10,199))
```

## Proof of work
![image](https://github.com/user-attachments/assets/fea0da6f-4272-446d-9441-adae2b353e70)

## UML Diagram
![image](https://github.com/user-attachments/assets/651d2e9b-3207-4429-99fb-5926360ca68b)

## Paper solution
![20250225_000559](https://github.com/user-attachments/assets/4e05c688-f420-4ac3-92f6-2d5eae64a9d6)
