# This is quiz 40



## 1. UML Diagram
![image](https://github.com/user-attachments/assets/79f811d0-e11a-42b0-948d-3d512330ea60)

## 2. SQL Queries to identify the fraudulent transaction
```.py
import sqlite3

db_name = "smallCase.db"
connection = sqlite3.connect(db_name)
cursor = connection.cursor()

read = f"SELECT * FROM transactions"

cursor.execute(read)
transactions = cursor.fetchall()
connection.commit()

read = f"SELECT * FROM accounts"

cursor.execute(read)
accounts = cursor.fetchall()
connection.commit()

read = f"SELECT * FROM customers"

cursor.execute(read)
customers = cursor.fetchall()
connection.commit()

connection.close()


for a in accounts:
    account_plusminus = 0
    for t in transactions:
        if t[4] == a[0]:
            if t[1] == "deposit":
                account_plusminus += t[2]
            else:
                account_plusminus -= t[2]
    if account_plusminus != a[2]:
        print(f"Fraudulent transaction by id {a[0]}, {customers[a[0]-1]}")
```

## Proof of work
![image](https://github.com/user-attachments/assets/4af503dc-a9b4-4f57-ae4d-16cbb7f7bcf2)
