# This is quiz 39
## Code solution
```.py
import sqlite3

db_name = "word_list.sql"
connection = sqlite3.connect(db_name)
cursor = connection.cursor()

haiku = """Code flows like a stream
Algorithm guide its way
In silence, it solves"""

query_create = """CREATE TABLE IF NOT EXISTS words(
    id INTEGER PRIMARY KEY,
    lengtha INTEGER,
    word TEXT not null
);
"""

cursor.execute(query_create)
connection.commit()

for worda in haiku.split():
    new_word = f"INSERT OR REPLACE INTO words(length, word) values ({len(worda)}, '{worda}');"
    cursor.execute(new_word)
    connection.commit()

obtain_avg_wrdlgth = f"SELECT * FROM words"
cursor.execute(obtain_avg_wrdlgth)
words = cursor.fetchall()
connection.close()
print(words)

temp = 0
for w in words:
    temp += w[1]
avg_lgth = temp // len(words)

print("average word length is", avg_lgth)
```

## UML Diagram
![image](https://github.com/user-attachments/assets/e558cb26-f985-4289-bc63-00b55b096a4c)

## Proof of work
![image](https://github.com/user-attachments/assets/87b6901c-58f1-46d3-a17b-294b9473ccda)
