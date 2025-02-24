# This is quiz 48

## Code solution
```.py
class Book:
    def __init__(self,title,author,isbn):
        self.title = title
        self.author = author
        self.isbn = isbn

    def display_info(self):
        print(self.title,self.author,self.isbn)

class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)

    def show_books(self):
        for b in self.books:
            b.display_info()

book1 = Book("red pig", "david oakson", "978-0-596-52068-7")
book2 = Book("blue dog", "sarah forest", "923-0-596-41290-2")
book3 = Book("yellow spider", "brian wattson", "321-0-634-37482-8")

lib = Library()
lib.add_book(book1)
lib.add_book(book2)
lib.add_book(book3)
lib.show_books()
```

## UML Diagram
![image](https://github.com/user-attachments/assets/0e811b5e-672e-4936-a033-e8af3d9ec88d)

## Proof of work
![image](https://github.com/user-attachments/assets/30435ba3-35f6-40d5-9069-b93158d92c33)

## Paper solution
![20250225_011319](https://github.com/user-attachments/assets/e0cebcb3-5065-45e8-93f3-7b5a6be50a52)
