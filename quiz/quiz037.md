# This is quiz 37

## Code solution
### Python
```.py
from kivymd.app import MDApp

class tictactoe(MDApp):
    def build(self):
        self.turn = 0
        return

    def pressed(self, location):
        text_mark = "O"
        if self.turn % 2 == 0:
            text_mark = "O"
            color = "beige"
            self.root.ids.turn.text = "It is X's turn"
        else:
            text_mark = "X"
            color = "red"
            self.root.ids.turn.text = "It is O's turn"

        if location == 1:
            self.root.ids.one.md_bg_color = color
            self.root.ids.one.text = text_mark
            self.turn += 1
        if location == 2:
            self.root.ids.two.md_bg_color = color
            self.root.ids.two.text = text_mark
            self.turn += 1
        if location == 3:
            self.root.ids.three.md_bg_color = color
            self.root.ids.three.text = text_mark
            self.turn += 1
        if location == 4:
            self.root.ids.four.md_bg_color = color
            self.root.ids.four.text = text_mark
            self.turn += 1
        if location == 5:
            self.root.ids.five.md_bg_color = color
            self.root.ids.five.text = text_mark
            self.turn += 1
        if location == 6:
            self.root.ids.six.md_bg_color = color
            self.root.ids.six.text = text_mark
            self.turn += 1
        if location == 7:
            self.root.ids.seven.md_bg_color = color
            self.root.ids.seven.text = text_mark
            self.turn += 1
        if location == 8:
            self.root.ids.eight.md_bg_color = color
            self.root.ids.eight.text = text_mark
            self.turn += 1
        if location == 9:
            self.root.ids.nine.md_bg_color = color
            self.root.ids.nine.text = text_mark
            self.turn += 1
        return
tictactoe().run()
```

### Kivy file
```.kv
Screen:
    size: 500, 300
    rgba: "#000000"


    MDBoxLayout:
        orientation: "vertical"

        MDLabel:
            text: "Tictactoe by Ritsu"
            halign: "center"
            size_hint: 1, .2
            pos_hint: {"center_x":.5}

        MDLabel:
            text: "It is O's turn"
            halign: "center"
            size_hint: 1, .2
            pos_hint: {"center_x":.5}
            id: turn

        GridLayout:
            cols: 3
            size_hint: .5,.7
            pos_hint: {"center_x":.5}

            MDFlatButton:
                text: "."
                text_color: "white"
                size_hint: 1,1
                md_bg_color: "green"
                on_press:
                    app.pressed(1)
                id: one
            MDFlatButton:
                text: "."
                text_color: "white"
                size_hint: 1,1
                md_bg_color: "green"
                on_press:
                    app.pressed(2)
                id: two
            MDFlatButton:
                text: "."
                text_color: "white"
                size_hint: 1,1
                md_bg_color: "green"
                on_press:
                    app.pressed(3)
                id: three
            MDFlatButton:
                text: "."
                text_color: "white"
                size_hint: 1,1
                md_bg_color: "green"
                on_press:
                    app.pressed(4)
                id: four
            MDFlatButton:
                text: "."
                text_color: "white"
                size_hint: 1,1
                md_bg_color: "green"
                on_press:
                    app.pressed(5)
                id: five
            MDFlatButton:
                text: "."
                text_color: "white"
                size_hint: 1,1
                md_bg_color: "green"
                on_press:
                    app.pressed(6)
                id: six
            MDFlatButton:
                text: "."
                text_color: "white"
                size_hint: 1,1
                md_bg_color: "green"
                on_press:
                    app.pressed(7)
                id: seven
            MDFlatButton:
                text: "."
                text_color: "white"
                size_hint: 1,1
                md_bg_color: "green"
                on_press:
                    app.pressed(8)
                id: eight
            MDFlatButton:
                text: "."
                text_color: "white"
                size_hint: 1,1
                md_bg_color: "green"
                on_press:
                    app.pressed(9)
                id: nine
```

## Proof of work
![image](https://github.com/user-attachments/assets/67f453e9-1b9c-4c48-ad2a-e95ec9d2b24f)
