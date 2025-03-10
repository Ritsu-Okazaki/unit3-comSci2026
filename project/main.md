# Unit 3 | Hotel Restaurant Manager Application

## Criteria A: Planning
### Problem Definition
My client, Mr. A, is the manager of a restaurant that is integrated into a hotel. While the restaurant ensures that all guests are provided with a seat, it also accepts non-guest visitors. Information of the guests is provided from the paper which the hotel manager gives in daily, while reservations by non-guest visitors are made directly to his restaurant through phone. Non-guest visitors are also allowed without reservations only if there is surplus in the seating.

The manager finds difficulty in taking a grasp of how many hotel guests, reservers and non-reserved visitors are in the restaurant at each moment, because all are being managed by paper. It is causing inefficiency by slowing down the process of bringing non-reserved visitors in, because of the difficulty in finding the total empty seats for the next two hours (one time slot for a reservation).

### Proposed Solution
I will use python to create a local GUI software suitable for the client's situation. There will be one software that, depending on the sign-in process, changes if the app is for the owner of a restaurant, the owner of the hotel, or the reserving visitor. I will use Python because Python is a widely used programming language that is compatible for most devices. Also, Python is multi-purpose due to its expandability of libraries and frameworks, therefore it can create the code for main operation, user interface, and database management without excessive combination of different languages. Additionally, Python's readability makes it easier for other developers that may modify the software in the future to understand the code and apply changes. The solution will be a local software because it will have more stability compared to a web application. A web application might get disturbed by a problem in a browser, or get unwanted intervention from browser expansions or settings. Also, even if the internet is unavailable temporalily, it will still be able to access the database which will be on the hotel's local server, preventing a whole loss of functionality (however, the customer requests would not be received which is tolerable if short span). The solution will have a GUI, because it will be more intuitive and easy to interact with compared to text-based UI. For the UI, I decided to use an open-source UI toolkit for Python called KivyMD to create the GUI. First, KivyMD has cross-platform compatibility, which increases the hardware flexibility for our client and his customers. Also, KivyMD has a visually appealing style and convenient widgets based on Google Material Design, increasing comfort for the client. Finally, for the database, I decided to use SQLite, an open source database management system. Compared to storing data in CSV files, XML files or JSON files, a database is a better solution for managing a table of different parameters and doing relational data transfer between different records. SQLite was a good solution among different databases, for its lightweight processes and no need for configuration, which makes it easier for the client and potential subsequent developers.

### Success Criteria
1. The application has a login function that authenticates and differentiates the hotel restaurant owner, the hotel owner and the reserving visitor.
2. The application, when in reserve mode, can make reservations with the name, number of people and start time. The user can see their own reservation, and it can be cancelled.
3. The application, when in hotel manager mode, can input the dinner resevations of the stayers of the hotel. The user can see the reservations that they have registered.
4. The application, when in hotel restaurant manager mode, can see the reservations made to the restaurant both from the hotel and directly.
5. The application will automatically assign seats, and the manager will be able to see which seats are empty for the next two hours, with a function to change the time.

#### Client Approval of Success Criteria
![image](https://github.com/user-attachments/assets/164416b1-9e3e-4488-8cec-c81ade5ffc39)
![image](https://github.com/user-attachments/assets/46c7ab2e-e2ef-446d-8d63-a2ba2fc279ba)


## Criteria B: Design
## Record of Tasks
|**Planned Action**|**Planned Outcome**|**Time Estimate**|**Completion Date**|**Criteria**|
|---|---|---|---|---|
|Meet with client and clarify problem|Problem definition written|40 min|Jan 30th|A|
|Create a proposed solution|Solution proposal written|30 min|Jan 31st|A|
