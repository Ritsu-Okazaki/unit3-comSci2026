# This is quiz 41

## Code solution
```.py
import sqlite3
from os.path import sameopenfile

from kivymd.app import MDApp
from secure_password import encrypt_password

class database_worker:
    def __init__(self, name):
        self.connection = sqlite3.connect(name)
        self.cursor = self.connection.cursor()

    def search(self, query):
        result = self.cursor.execute(query).fetchall()
        return result

    def run_save(self, query):
        self.cursor.execute(query)
        self.connection.commit()

    def close(self):
        self.connection.close()


class quiz047(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.components = {"basic":0}

    def build(self):
        return

    def save(self):
        pass

    def update(self):
        base = self.root.ids.base.text
        if base:
            base = int(base)
            for_hash = ""
            inhabitant, income, pension, health = self.root.ids.inhabitant.text, self.root.ids.income_tax.text, self.root.ids.pension.text, self.root.ids.health.text
            subtract = 0
            if inhabitant:
                inhabitant_tax = base*int(inhabitant)//100
                subtract += inhabitant_tax
                self.root.ids.inhabitant_label.text = f"{inhabitant_tax} JPY"
            if income:
                income_tax = base*int(income)//100
                subtract += income_tax
                self.root.ids.income_tax_label.text = f"{income_tax} JPY"
            if pension:
                pension_tax = base * int(pension) // 100
                subtract += pension_tax
                self.root.ids.pension_label.text = f"{pension_tax} JPY"
            if health:
                health_tax = base * int(health) // 100
                subtract += health_tax
                self.root.ids.health_label.text = f"{health_tax} JPY"
            total = base - subtract
            for_hash = f"total{total}"
            self.root.ids.salary_label.text = f"{total} JPY"
            net_hash = f"hash{encrypt_password(for_hash)}"
            print(net_hash)
        else:
            return

    def save(self):
        base = self.root.ids.base.text
        if base:
            base = int(base)
            for_hash = ""
            inhabitant, income, pension, health = self.root.ids.inhabitant.text, self.root.ids.income_tax.text, self.root.ids.pension.text, self.root.ids.health.text
            inhabitant_tax, income_tax, pension_tax, health_tax = 0,0,0,0
            subtract = 0
            if inhabitant:
                inhabitant_tax = base * int(inhabitant) // 100
                subtract += inhabitant_tax
                self.root.ids.inhabitant_label.text = f"{inhabitant_tax} JPY"
            if income:
                income_tax = base * int(income) // 100
                subtract += income_tax
                self.root.ids.income_tax_label.text = f"{income_tax} JPY"
            if pension:
                pension_tax = base * int(pension) // 100
                subtract += pension_tax
                self.root.ids.pension_label.text = f"{pension_tax} JPY"
            if health:
                health_tax = base * int(health) // 100
                subtract += health_tax
                self.root.ids.health_label.text = f"{health_tax} JPY"
            total = base - subtract
            hash = f"inhabitant{inhabitant_tax},income_tax{income_tax},pension{pension_tax},total{total}"
            hash = encrypt_password(hash)
            print(hash)
            query = f"""INSERT into payments(
            'base','inhabitant','income_tax','pension','health','total','hash')
            values ({base},{inhabitant_tax},{income_tax},{pension_tax},{health_tax},{total},'{hash}')
            """
            db = database_worker("payments.db")
            db.run_save(query)
            db.close()
        else:
            return
        self.root.ids.hash.text = f"Payment saved"

    def clear(self):
        for label in ["base", "inhabitant","income_tax","pension","health"]:
            self.root.ids[label].text = ""
            self.root.ids[label+"_label"].text = " JPY"

        self.root.ids["salary_label"].text = " JPY"
        self.root.ids.hash.text = "----"


test = quiz047()
create = """CREATE TABLE if not exists payments(
    id INTEGER PRIMARY KEY,
    base INTEGER,
    inhabitant INTEGER,
    income_tax INTEGER,
    pension INTEGER,
    health INTEGER,
    total INTEGER,
    hash CHAR
    )"""
db = database_worker("payments.db")
db.run_save(create)
db.close()
test.run()
```

## UML Diagram
![image](https://github.com/user-attachments/assets/4c65809c-1901-46ef-9687-51962367d727)

## Proof of work (video link)
[https://drive.google.com/file/d/13MltcfpJNtyhxsvmNmFtsCPstk1nIDuc/view?usp=sharing](https://drive.google.com/file/d/13MltcfpJNtyhxsvmNmFtsCPstk1nIDuc/view?usp=sharing)
