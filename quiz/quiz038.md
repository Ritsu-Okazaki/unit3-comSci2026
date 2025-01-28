# This is quiz 38

## Code solution
### Python
```.py
from kivymd.app import MDApp
from kivymd.uix.screen import MDScreen

class quiz037(MDApp):
    def build(self):
        return

class MysteryPageA(MDScreen):
    def message1(self):
        print("This is mystery page A you pressed the button")
        return
    def swap(self):
        self.parent.current = "MysteryPageB"
        return

    pass

class MysteryPageB(MDScreen):
    def message2(self):
        print("This is mystery page B you pressed the button")
        return
    def swap(self):
        self.parent.current = "MysteryPageA"
        return
    pass

quiz038().run()
```

### Kivy file
```.kv
ScreenManager:
    id: scr_manager

    MysteryPageA:
        name: "MysteryPageA"
    MysteryPageB:
        name: "MysteryPageB"

<MysteryPageA>:
    MDFlatButton:
        text: "Cheese"
        on_press:
            root.message1()
    MDFlatButton:
        text: "Page change"
        pos_hint: {"center_x":0.4}
        on_press:
            root.swap()

<MysteryPageB>:
    MDFlatButton:
        text: "Cheese"
        on_press:
            root.message2()

    MDFlatButton:
        text: "Page change"
        pos_hint: {"center_x":0.4}
        on_press:
            root.swap()
```

## Proof of work
![image](https://github.com/user-attachments/assets/86ae0ed7-7b0a-4f37-9f9d-6d6b94a5c6a6)
