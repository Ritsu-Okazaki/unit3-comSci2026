# This is quiz 42

## Code solution
```.py
from passlib.context import CryptContext
from passlib.hash import sha256_crypt

import sqlite3

db_name = "bitcoin_exchange.db"

hash_function = sha256_crypt.using(rounds=30000)

connection = sqlite3.connect(db_name)
cursor = connection.cursor()

query = """SELECT * FROM LEDGER
"""

a = cursor.execute(query).fetchall()
connection.commit()

for exchange in a:
    id, sender_id, receiver_id, amount, sent_hash = exchange
    hash_origin = f"id {id},sender_id {sender_id},receiver_id {receiver_id},amount {amount}"
    generated_hash = sha256_crypt.hash(hash_origin)
    if sha256_crypt.verify(hash_origin, sent_hash):
        print(f"Tx{id} is correct")
    else:
        print(f"Tx{id} is incorrect")
```

## UML Diagram
![image](https://github.com/user-attachments/assets/f169caef-a1a9-43ac-bd14-abe46fe198ee)

## Proof of work
![image](https://github.com/user-attachments/assets/433914ec-3be1-439d-9ab4-d0fceb97d9e7)
