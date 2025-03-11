# Unit 3 | Hotel Restaurant Manager Application

## Criteria A: Planning
### Problem Definition
My client, Mr. A, is the manager of a restaurant that is integrated into a hotel. While the restaurant ensures that all guests are provided with a seat, it also accepts non-guest visitors. Information of the guests is provided from the paper which the hotel manager gives in daily, while reservations by non-guest visitors are made directly to his restaurant through phone. Non-guest visitors are also allowed without reservations only if there is surplus in the seating.

The manager finds difficulty in taking a grasp of how many hotel guests, reservers and non-reserved visitors are in the restaurant at each moment, because all are being managed by paper. It is causing inefficiency by slowing down the process of bringing non-reserved visitors in, because of the difficulty in finding the total empty seats for the next two hours (one time slot for a reservation).

### Proposed Solution
I will use python to create a local GUI software suitable for the client's situation. There will be one software that, depending on the sign-in process, changes if the app is for the owner of a restaurant, the owner of the hotel, or the reserving visitor. I will use Python because Python is a widely used programming language that is compatible for most devices. Also, Python is multi-purpose due to its expandability of libraries and frameworks, therefore it can create the code for main operation, user interface, and database management without excessive combination of different languages. Additionally, Python's readability makes it easier for other developers that may modify the software in the future to understand the code and apply changes. The solution will be a local software because it will have more stability compared to a web application. A web application might get disturbed by a problem in a browser, or get unwanted intervention from browser expansions or settings. Also, even if the internet is unavailable temporalily, it will still be able to access the database which will be on the hotel's local server, preventing a whole loss of functionality (however, the customer requests would not be received which is tolerable if short span). The solution will have a GUI, because it will be more intuitive and easy to interact with compared to text-based UI. For the UI, I decided to use an open-source UI toolkit for Python called KivyMD to create the GUI. First, KivyMD has cross-platform compatibility, which increases the hardware flexibility for our client and his customers. Also, KivyMD has a visually appealing style and convenient widgets based on Google Material Design, increasing comfort for the client. Finally, for the database, I decided to use SQLite, an open source database management system. Compared to storing data in CSV files, XML files or JSON files, a database is a better solution for managing a table of different parameters and doing relational data transfer between different records. SQLite was a good solution among different databases, for its lightweight processes and no need for configuration, which makes it easier for the client and potential subsequent developers.

### Success Criteria
1. The application has a login function that authenticates and differentiates the hotel restaurant owner, the hotel owner and the reserving visitor.
2. The application, when in reserve mode, can make reservations with the name, number of people and start time. The user can see their own reservation.
3. The application, when in hotel manager mode, can input the dinner resevations of the stayers of the hotel. The user can see the reservations that they have registered.
4. The application, when in hotel restaurant manager mode, can see the reservations made to the restaurant both from the hotel and directly.
5. The application will automatically assign seats, and the manager will be able to see which seats are empty for the next two hours, with a function to change the time.

#### Client Approval of Success Criteria
![image](https://github.com/user-attachments/assets/164416b1-9e3e-4488-8cec-c81ade5ffc39)
![image](https://github.com/user-attachments/assets/46c7ab2e-e2ef-446d-8d63-a2ba2fc279ba)


## Criteria B: Design
### Application Wireframe
![image](https://github.com/user-attachments/assets/f12d4ca2-0501-4be1-be95-4ec06c8c4579)

### UML Diagram
![image](https://github.com/user-attachments/assets/28ca0cd9-72d2-49c2-9912-c26f1ef7fe32)

### ER Diagram
![image](https://github.com/user-attachments/assets/dba1bfae-726f-4768-b5da-13a0fcb607c5)

### Flow diagram
![image](https://github.com/user-attachments/assets/0eaa2ad8-7930-4137-bcc6-9bfa2abd55b8)
_Flow diagram of get_slider_value from class MainScreen, CustomerScreen and HotelMainScreen_

## Criteria C: Development

### 1. Database manager
In order to work with a SQLite database, there are set steps that needs to be completed for each process in the creation of relational database, insertion of values and extraction of values. First, in the establishment of connection with the database, sqlite3 provides a module function ```sqlite3.connect``` that creates a ```Connection``` object which represent the connection to the database by providing a path to the database. Once the connection is established, to execute queries and fetch results from specific rows of the relational database, a cursor needs to be created, which is possible by using the ```cursor``` method which creates a ```cursor``` object. To a ```cursor``` object, using the ```cursor.execute``` method will execute the provided SQL statements. To make changes to the database, the transaction has to be commited by using the ```connection.commit``` method. To read results, the results of ```execute``` can be assiged to a variable, which can be converted into a list by using the ```.fetchall()``` method that will return the list of each row in the database that matches the conditions which the SQL statements specified.
```.py
import sqlite3
con = sqlite3.connect("tutorial.db") # create connection
cur = con.cursor() # create cursor
cur.execute("CREATE TABLE table (id PRIMARY KEY INTEGER UNIQUE, value TEXT)") # execute SQL statement
con.commit() # confirm transaction

res = cur.execute("SELECT * FROM table") # reading SQL queries
lis = res.fetchall() # convert each row to a list
```
However, it is repetitive and inconvenient that this sequence needs to happen every time we manipulate or read from the database. So, I created a class called ```DatabaseManager``` which turns the database connection into an object which can be used to call methods in simpler, shorter lines of code that does not repeatedly declare the connection or the cursor.
```
import sqlite3

class DatabaseManager:
    def __init__(self, name: str):
        self.connection = sqlite3.connect(name)
        self.cursor = self.connection.cursor()

    def search(self, query):
        result = self.cursor.execute(query).fetchall()
        return result

    def close(self):
        self.connection.close()

    def run_save(self, query):
        self.cursor.execute(query)
        self.connection.commit()
```.py


### 2. Meeting Success Criteria 4: Seeing reservations both by the hotel and directly
To meet Success Criteria 4: "The application, when in hotel restaurant manager mode, can see the reservations made to the restaurant both from the hotel and directly.", I created a table called ```joint_table``` in ```database.db```, that stores the information of the reservations.
```.py
db = DatabaseManager('database.db')
db.run_save(query="""CREATE TABLE IF NOT EXISTS joint_table (id INTEGER PRIMARY KEY UNIQUE, stayer INTEGER, rep_name TEXT, number INTEGER, start_time INTEGER, assigned_seat INTEGER)""")
```


### 2. Meeting Success Criteria 2: Making a reservation
To meet Success Criteria 2: "The application, when in reserve mode, can make reservations with the name, number of people and start time. The user can see their own reservation.", 
   

### Record of Tasks
|**Planned Action**|**Planned Outcome**|**Time Estimate**|**Completion Date**|**Criteria**|
|---|---|---|---|---|
|Meet with client and clarify problem|Problem definition written|40 min|Jan 30th|A|
|Create a proposed solution|Solution proposal written|30 min|Jan 31st|A|
