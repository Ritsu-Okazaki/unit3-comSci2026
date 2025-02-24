# This is quiz 45

## Code solution
```.py
class WordCounter:
    def __init__(self):
        self.result = {}
        pass

    def WordCounter(self,text):
        words = text.split()
        result = {}
        for w in words:
            w=w.strip(".!").lower()
            if w not in result:
                result[w]=1
            else:
                result[w]=result[w]+1
        self.result = result
        return self.result

print(WordCounter().WordCounter("This is a sample text. It contains some words that will be counted."))
```

## Proof of work
![image](https://github.com/user-attachments/assets/a107fa46-6af1-48a7-8cb2-2ec792afea5c)

## UML Diagram
![image](https://github.com/user-attachments/assets/f5642380-9d21-4572-8576-fdbcf3e57f57)

## Paper solution
![20250225_003934](https://github.com/user-attachments/assets/036fe627-f06b-4743-9541-d4d26f56b99a)
