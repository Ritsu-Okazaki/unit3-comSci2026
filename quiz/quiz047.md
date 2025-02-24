# This is quiz 47

## Code solution
```.py
class CalorieCount:
    def __init__(self,daily_limit):
        self.daily_limit = daily_limit
        self.daily_intake,self.protein,self.carbs,self.fat=0,0,0,0

    def addMeal(self,cal,pro,car,fat):
        self.daily_intake += cal
        self.protein += pro
        self.carbs += car
        self.fat += fat

    def getProteinPercentage(self):
        print(4*self.protein/self.daily_intake)
        return 4*self.protein/self.daily_intake

    def onTrack(self):
        if self.daily_intake > self.daily_limit:
            print(False)
            return False
        print(True)
        return True

sunday = CalorieCount(1500)

sunday.addMeal(716, 38, 38, 45)
sunday.addMeal(230, 16, 8, 16)
sunday.addMeal(568, 38, 50, 24)

sunday.onTrack() #returns False
sunday.getProteinPercentage()
#returns 0.24
```

## UML Diagram
![image](https://github.com/user-attachments/assets/13bf2fe7-7ee5-42f3-acae-c50fdba8fcb7)

## Proof of work
![image](https://github.com/user-attachments/assets/38aea05d-ad58-42f5-b633-dd055883e25f)

## Paper solution
![20250225_011309](https://github.com/user-attachments/assets/2c02b683-d25b-4678-9ce6-5b6332b8fe7e)
