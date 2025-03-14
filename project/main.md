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

### 1. Show Dialog + Lambda Expression
To meet Success Criteria 2&3: allowing the user to add reservation data to the database, I decided to create a GUI where a user can click on a empty seat on the MDList that shows the occupancy of the seats in the restaurant to add a reservation. The dialog is a temporary entity in the GUI that is not always present on a screen, so it needed to be binded to an event in the app that will create an instance whenever the user triggers the event. The Kivy framework provides an ```EventDispatcher``` class that provides functions that manages the registeration or manipulation of events for objects that produce events. For my application, ```ThreeLineItem``` is the object that triggers the event, because they are the contents of the ```MDList``` that show the detail of each reservation, along with showing which seats remain empty. ```ThreeLineItem``` has three attributes, ```text```, ```secondary_text``` and ```tertiary_text```. I used the first text to show the seat number and its occupancy state, the second text to show the number of seats and their occupancy state, and the third text to show the time which the reservation begins. Initially, I was directly declaring the ```ThreeLineItem``` individually in different parts of the code. However, because there are set multiple configurations for the attributes depending on the occupancy state of the seat, I created a function named ```make_seat_item``` that returns a ```ThreeLineListItem``` with its attributes declared by input values that are formatted using the lists stored in the dictionary ```status_list```, shown below.
```.py
def make_seat_item(status:str, seat_number:int, start_time:int, rep_name:str=None, reserver_number:int=None):
    status_list = {"unassigned": [f'Seat {seat_number}: Unassigned', f'4 available', f'{start_time}:00~{start_time + 2}:00'],
                   "unavailable": [f'Seat {seat_number}: Reserved for next slot', f'Unavailable', f'{start_time}:00~{start_time + 2}:00'],
                   "assigned": [f'Seat {seat_number}: {rep_name}', f'{reserver_number} people', f'{start_time}:00~{start_time + 2}:00'],
                   "reserved": [f'Seat {seat_number}: Reserved', f'{reserver_number} people', f'{start_time}:00~{start_time + 2}:00']}
    item = ThreeLineListItem(text=status_list[status][0],
                             secondary_text=status_list[status][1],
                             tertiary_text=status_list[status][2])
    return item


item = make_seat_item("unassigned", number_of_people, slider_value)
item.bind(on_press=lambda instance=item, time=slider_value: self.on_touch(instance, time))
```
In the last line, the program binds the created ```ThreeLineListItem``` with an event ```self.on_touch```, using the function ```bind``` from ```EventDispatcher``` that binds an event to a callback. Here, the program uses a lambda expression to declare the ```self.on_touch``` function as a callback attribute to the ```on_press``` event, instead of declaring directly like ```item.bind(on_press = self.on_touch(item, slider_value)``` which is how I did it initially and encountered an error. I figured out that the reason why a lambda expression needed to be used is that ```bind``` asks for a function reference, instead of a function call. When attributes are given to the function like in ```item.bind(on_press = self.on_touch(item, slider_value)```, it is a function call which means that the function is executed, and ```on_press = self.on_touch(item, slider_value)``` declaration will assign the return value of the ```on_touch``` function to the ```on_press``` event, which is unintended. On top of that, because this bind declaration is made in prior to the press by the user and in the initialization process, the function call will execute the function immidiately as the code starts instead of when the user presses the item. To correctly bind a corresponding execution to the event, a function reference is required, while declaring the attributes for the function. A solution for this is to refer to a buffer function without attributes that call the intended function, like below.
```.py
item.bind(on_press=on_touch_wrapper)

def on_touch_wrapper(item, slider_value):
    def wrapper(instance):
        self.on_touch(item, slider_value)

    return wrapper
```
Here, ```on_touch_wrapper``` is a function that returns a reference to ```wrapper``` which includes a call for the function ```on_touch```. This way, the ```on_touch``` gets executed only if the event is triggered.


### Record of Tasks
|**Planned Action**|**Planned Outcome**|**Time Estimate**|**Completion Date**|**Criteria**|
|---|---|---|---|---|
|Meet with client and clarify problem|Problem definition written|40 min|Jan 30th|A|
|Create a proposed solution|Solution proposal written|30 min|Jan 31st|A|
