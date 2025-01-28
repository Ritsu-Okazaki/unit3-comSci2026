# This is quiz 36

## Code solution
### Python
```.py
from kivymd.app import MDApp

class quiz034(MDApp):
    def build(self):
        self.color = "light"
        return

    def switch(self):
        if self.color == "light":
            self.root.ids.bg.md_bg_color = "#000000"
            self.root.ids.txt.text_color = "white"
            self.color = "dark"
        elif self.color == "dark":
            self.root.ids.bg.md_bg_color = "#ffffff"
            self.root.ids.txt.text_color = "black"
            self.color = "light"
        return

quiz034().run()
```

### Kivy file
```.kv
Screen:
    size: 500, 500

    MDBoxLayout:
        id: bg
        md_bg_color: "#ffffff"

        MDLabel:
            text: "Your Name"
            halign: "center"
            font_size: "34pt"
            id: txt
            theme_text_color: "Custom"
            text_color: "black"

        MDRaisedButton:
            text: "Click me"
            size_hint: .1, 0.1
            font_size: "15pt"
            md_bg_color: "#00ffff"
            pos_hint : {"center_x": 0.1, "center_y": 0.1}
            on_press:
                app.switch()
```

## Proof of work
![image](https://github.com/user-attachments/assets/b4ce239e-c2e8-4468-96fd-c23acb626cad)
