# Python code
```.py
import sqlite3
from kivy.uix.screenmanager import Screen
from kivymd.app import MDApp
from kivymd.uix.list import OneLineListItem, TwoLineListItem
from kivymd.uix.menu import MDDropdownMenu
from passlib.context import CryptContext
from collections import Counter

pwd_config = CryptContext(schemes = ["pbkdf2_sha256"],
                          default = "pbkdf2_sha256",
                          pbkdf2_sha256__default_rounds=30000)

def encryptPass(user_password):
    return pwd_config.hash(user_password)

def check_password(hashed_password, user_password):
    return pwd_config.verify(user_password, hashed_password)

class DatabaseManager:
    def __init__(self, name:str):
        self.connection = sqlite3.connect(name)
        self.cursor = self.connection.cursor()

    def search(self, query):
        result = self.cursor.execute(query).fetchall()
        return result

    def execute(self, query, params=()):
        try:
            self.cursor.execute(query, params)
            self.connection.commit()
        except sqlite3.Error as e:
            print(f"Database error: {e}")

    def close(self):
        self.connection.close()

    def run_save(self, query):
        self.cursor.execute(query)
        self.connection.commit()

class LoginScreen(Screen):
    username = ""
    def try_login(self):
        print("trying to login")
        LoginScreen.username = self.ids.username.text
        password = self.ids.password.text
        check_query = f"""SELECT * from users where username = '{LoginScreen.username}'"""
        db = DatabaseManager("/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db")
        result = db.search(check_query)
        db.close()
        if len(result) == 1:
            hash = result[0][1]
            if check_password(hash, password):
                self.parent.current = "HomeScreen"#######
        else:
            self.ids.username.error = True
            self.ids.username.helper_text = "Username or password error"
            print("user doh exis") #change this later
        self.ids.username.text = ""
        self.ids.password.text = ""

    def go_register(self):
        self.parent.current = "RegistrationScreen"
        self.ids.username.text = ""
        self.ids.password.text = ""

    def emp_login(self):
        self.parent.current = "EmployeeLogin"
        self.ids.username.text = ""
        self.ids.password.text = ""

class EmployeeLogin(Screen):
    def try_emp_login(self):
        print("trying to login")
        username = self.ids.username.text
        password = self.ids.password.text
        check_query = f"""SELECT * from employees where username = '{username}'"""
        db = DatabaseManager("/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db")
        result = db.search(check_query)
        db.close()
        if len(result) == 1:
            hash = result[0][1]
            if check_password(hash, password):
                self.parent.current = "EmployeeScreen"
        else:
            self.ids.username.error = True
            self.ids.username.helper_text = "Username or password error"
            print("user doh exis") #change this later
        self.ids.username.text = ""
        self.ids.password.text = ""

    def go_login(self):
        self.parent.current = "LoginScreen"
        self.ids.username.text = ""
        self.ids.password.text = ""

class EMPRegScreen(Screen):
    def register(self):
        username = self.ids.username.text
        password = self.ids.password.text

        check_query = f"""SELECT * from employees where username = '{username}' or password = '{password}'"""
        db = DatabaseManager("/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db")
        result = db.search(check_query)
        if len(result) == 0 and len(username)>0 and len(password)>0:
            hashed_password = encryptPass(password)
            db.run_save(f"""INSERT INTO employees (username, password) VALUES ('{username}', '{hashed_password}')""")
            self.parent.current = "LoginScreen"
        else:
            self.ids.username.error = True
            self.ids.username.helper_text = "Username already exists"
        db.close()
        self.ids.username.text = ""
        self.ids.password.text = ""

    def cancel(self):
        self.parent.current = "EmployeeScreen"
        self.ids.username.text = ""
        self.ids.password.text = ""

class RegistrationScreen(Screen):
    def register(self):
        username = self.ids.username.text
        password = self.ids.password.text

        check_query = f"""SELECT * from users where username = '{username}' or password = '{password}'"""
        db = DatabaseManager("/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db")
        result = db.search(check_query)
        if len(result) == 0 and len(username)>0 and len(password)>0:
            hashed_password = encryptPass(password)
            db.run_save(f"""INSERT INTO users (username, password) VALUES ('{username}', '{hashed_password}')""")
            self.parent.current = "LoginScreen"
        else:
            self.ids.username.error = True
            self.ids.username.helper_text = "Username already exists"
        db.close()
        self.ids.username.text = ""
        self.ids.password.text = ""

    def go_login(self):
        self.parent.current = "LoginScreen"
        self.ids.username.text = ""
        self.ids.password.text = ""

class HomeScreen(Screen):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.cart = []

    def on_enter(self):
        self.db = DatabaseManager('/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db')
        query = "SELECT id, name FROM restaurants"
        self.restaurants = self.db.search(query)
        self.db.close()

        if not self.restaurants:
            self.ids.restaurant_label.text = "No restaurants available."
            return

        # Create a dropdown menu for restaurant selection
        menu_items = [
            {"text": name, "viewclass": "OneLineListItem",
             "on_release": lambda x=name, y=rid: self.select_restaurant(y, x)}
            for rid, name in self.restaurants]

        self.restaurant_menu = MDDropdownMenu(caller=self.ids.restaurant_dropdown, items=menu_items, width_mult=4)

    def select_restaurant(self, restaurant_id, restaurant_name):
        self.restaurant_id = restaurant_id
        self.ids.restaurant_label.text = f"Selected: {restaurant_name}"
        self.restaurant_menu.dismiss()
        self.show_menuu()

    def show_menuu(self):
        if self.restaurant_id is None:
            self.ids.restaurant.text = "Please select a restaurant first."
            return

        db = DatabaseManager('/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db')
        query = f"SELECT item_name, price FROM menu WHERE restaurant_id = {self.restaurant_id}"
        menu_items = db.search(query)
        db.close()
        self.ids.menu_list.clear_widgets()  # Prevent duplication
        if not menu_items:
            self.ids.menu_list.add_widget(OneLineListItem(text="No menu items found."))
            return
        for item_name, price in menu_items:
            item = OneLineListItem(text=f"{item_name} - ${price:.2f}")
            # Attach data to the item
            item.bind(on_release=lambda instance, name=item_name, Price=price: self.add_to_cart(name, Price))
            self.ids.menu_list.add_widget(item)

    def select_menu_item(self, instance_table, instance_row):
        row_data = instance_row.text  # Extract row data
        print(f"Selected Menu Item: {row_data}")

    def add_to_cart(self, item_name, price):
        self.cart.append((item_name, price))
        self.update_cart_display()

    def update_cart_display(self):
        self.ids.cart_list.clear_widgets()
        total_price = sum(price for _, price in self.cart)

        for item_name, price in self.cart:
            self.ids.cart_list.add_widget(OneLineListItem(text=f"{item_name} - ${price:.2f}"))
        self.ids.subtotal_label.text = f"Subtotal: ${total_price:.2f}"

    def place_order(self):
        if not self.cart:
            self.ids.subtotal_label.text = "Cart is empty!"
            return
        username = LoginScreen.username

        item_counts = Counter(item_name for item_name, _ in self.cart)
        order_summary = ", ".join([f"{item} x{count}" for item, count in item_counts.items()])

        db = DatabaseManager('/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db')
        query = """
            INSERT INTO orders (username, User_Order, completed) 
            VALUES (?, ?, ?)
        """
        db.execute(query, (username, order_summary, "No"))
        db.close()
        self.cart.clear()
        self.update_cart_display()
        self.ids.subtotal_label.text = "Order placed successfully!"

    def sign_out(self):
        self.parent.current = "LoginScreen"
    pass

class EmployeeScreen(Screen):
    def on_enter(self):
        self.restaurant_id = None  #Initialize the selected restaurant
        db = DatabaseManager('/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db')
        query = "SELECT id, name FROM restaurants"  #Retrieve ID also
        self.restaurants = db.search(query)
        db.close()

    def open_menu(self, menu_item):
        if not self.restaurants:
            return  # Avoid errors if there are no restaurants

        btn_menu = []
        for restaurant_id, restaurant_name in self.restaurants:
            btn_menu.append({
                'text': restaurant_name,
                'viewclass': 'OneLineListItem',
                'on_release': lambda x=restaurant_id, y=restaurant_name: self.button_pressed(x, y)
            })

        self.menu = MDDropdownMenu(caller=menu_item, items=btn_menu, width_mult=2)
        self.menu.open()

    def button_pressed(self, restaurant_id, name):
        self.restaurant_id = restaurant_id  #Store the selected restauran
        self.ids.restaurant.text = f"You selected {name} (ID: {restaurant_id})"
        self.ids.dropdown_user.text = name
        self.menu.dismiss()

    def show_menu(self):
        if self.restaurant_id is None:  # Check if a restaurant has been selected
            self.ids.restaurant.text = "Please select a restaurant first."
            return

        db = DatabaseManager('/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db')
        query = f"SELECT item_name, stock, price FROM menu WHERE restaurant_id = {self.restaurant_id}"
        menu_items = db.search(query)
        db.close()
        self.ids.menu_list.clear_widgets() #stop duplication
        if not menu_items:
            self.ids.menu_list.add_widget(OneLineListItem(text="No menu items found."))
            return
        for item_name, stock, price in menu_items:
            self.ids.menu_list.add_widget(OneLineListItem(text=f"{item_name} - Stock: {stock}, Price: {price}"))

    def add_menu_item(self):
        if self.restaurant_id is None:
            self.ids.restaurant.text = "Please select a restaurant first."
            return

        item_name = self.ids.item_name_input.text.strip()
        stock = self.ids.stock_input.text.strip()
        price = self.ids.price_input.text.strip()

        if not item_name or not stock or not price:
            self.ids.restaurant.text = "Please enter item name, stock and price."
            return
        try:
            price = int(price)
        except ValueError:
            self.ids.restaurant.text = "Price must be a number."
        try:
            stock = int(stock)
        except ValueError:
            self.ids.restaurant.text = "Stock must be a number."
            return

        db = DatabaseManager('/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db')
        query = "INSERT INTO menu (restaurant_id, item_name, stock, price) VALUES (?, ?, ?, ?)"
        db.execute(query, (self.restaurant_id, item_name, stock, price))
        db.close()

        self.ids.restaurant.text = f"Added {item_name} to menu."
        self.show_menu()

    def new_admin(self):
        self.parent.current = "EMPRegScreen"

    def ViewOrders(self):
        self.parent.current = "OrdersScreen"

    def signout(self):
        self.parent.current = "LoginScreen"

class OrdersScreen(Screen):
    def on_enter(self):
        self.load_orders()

    def load_orders(self):
        self.ids.orders_list.clear_widgets()  # Clear existing orders
        db = DatabaseManager('/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db')
        query = "SELECT id, username, User_Order, completed FROM orders WHERE completed = 'No'"
        orders = db.search(query)
        db.close()

        if not orders:
            self.ids.orders_list.add_widget(OneLineListItem(text="No Orders."))
            return
        for order_id, username, user_order, completed in orders:
            if completed == "Yes":
                order_status = "Completed"
            else:
                order_status = "Pending"
            order_text = f"({order_id}) {username}: {user_order} - {order_status}"
            order_item = TwoLineListItem(text=order_text, secondary_text="Press to mark as completed")
            order_item.bind(on_release=lambda instance, id=order_id: self.mark_order_completed(order_id))
            self.ids.orders_list.add_widget(order_item)

    def mark_order_completed(self, order_id):
        db = DatabaseManager('/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db')
        print(order_id)
        query = "UPDATE orders SET completed = 'Yes' WHERE id = ?"
        db.execute(query, (order_id,)) # passed as a tuple (whatever that means)
        db.close()
        self.load_orders()

    def go_back(self):
        self.parent.current = "EmployeeScreen"


class main_v3(MDApp):
    def build(self):
        conn = sqlite3.connect("/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db")
        cursor = conn.cursor()
        cursor.execute("""
            CREATE TABLE IF NOT EXISTS restaurants (
                id INTEGER PRIMARY KEY AUTOINCREMENT,
                name TEXT UNIQUE
            )
            """)
        cursor.execute("""
            CREATE TABLE IF NOT EXISTS menu (
                id INTEGER PRIMARY KEY AUTOINCREMENT,
                restaurant_id INTEGER,
                item_name TEXT,
                stock INTEGER,
                price FLOAT,
                FOREIGN KEY (restaurant_id) REFERENCES restaurants(id)
            )
            """)
        cursor.execute("""
            CREATE TABLE IF NOT EXISTS users (
                username TEXT PRIMARY KEY,
                password TEXT
            )
            """)
        cursor.execute("""
                    CREATE TABLE IF NOT EXISTS employees (
                        username TEXT PRIMARY KEY,
                        password TEXT
                    )
                    """)
        cursor.execute("""
            CREATE TABLE IF NOT EXISTS membership (
                username TEXT PRIMARY KEY,
                points INTEGER,
                FOREIGN KEY (username) REFERENCES users(username)
            )
            """)
        cursor.execute("""
            CREATE TABLE IF NOT EXISTS orders (
                id INTEGER PRIMARY KEY AUTOINCREMENT,
                username TEXT,
                User_Order TEXT,
                completed TEXT,
                FOREIGN KEY (username) REFERENCES users(username)
            )
            """)
        conn.commit()
        conn.close()
        pass

main_v3().run()
```

# Kivy
```.kv
ScreenManager:
    LoginScreen:
        name: "LoginScreen"
    EmployeeLogin:
        name: "EmployeeLogin"
    HomeScreen:
        name: "HomeScreen"
    EMPRegScreen:
        name: "EMPRegScreen"
    RegistrationScreen:
        name: "RegistrationScreen"
    EmployeeScreen:
        name: "EmployeeScreen"
    OrdersScreen:
        name: "OrdersScreen"

<LoginScreen>
    Image:
        source: "1main_background.webp"  # Replace with the actual file path
        size: self.parent.size
        allow_stretch: True
        keep_ratio: False
        opacity: 0.5  # Set transparency to 50%

    MDBoxLayout:
        orientation: "vertical"
        spacing: dp(10)
        padding: dp(20)
        pos_hint: {"center_x": 0.5, "center_y": 0.5}
        size_hint: None, None
        size: dp(350), dp(450)

        MDCard:
            size_hint: 1, 1
            padding: dp(20)
            elevation: 5
            radius: [20, 20, 20, 20]

            MDBoxLayout:
                orientation: "vertical"
                spacing: dp(20)

                MDLabel:
                    text: "Login"
                    halign: "center"
                    font_style: "H5"
                    theme_text_color: "Primary"

                MDTextField:
                    id: username
                    hint_text: "Username"
                    icon_right: "account"
                    mode: "rectangle"

                MDTextField:
                    id: password
                    hint_text: "Password"
                    password: True
                    icon_right: "eye-off"
                    mode: "rectangle"

                MDRaisedButton:
                    text: "Login"
                    pos_hint: {"center_x": 0.5}
                    on_press: root.try_login()

                MDBoxLayout:
                    orientation: "horizontal"
                    spacing: dp(10)
                    size_hint_y: None
                    height: dp(40)

                    MDRaisedButton:
                        text: "Register"
                        size_hint_x: 0.5
                        on_press: root.go_register()

                    MDRaisedButton:
                        text: "Admin"
                        size_hint_x: 0.5
                        on_press: root.emp_login()

<EmployeeScreen>
    Image:
        source: "1main_background.webp"
        size: self.parent.size
        allow_stretch: True
        keep_ratio: False
        opacity: 0.5  # 50% transparency

    MDBoxLayout:
        orientation: "vertical"
        spacing: dp(20)
        padding: dp(20)

        MDLabel:
            text: "Employee Panel"
            font_style: "H4"
            halign: "center"
            theme_text_color: "Primary"
            size_hint_y: None
            height: dp(50)

        # Restaurant Selection
        MDBoxLayout:
            orientation: "horizontal"
            spacing: dp(10)
            size_hint_y: None
            height: dp(50)

            MDDropDownItem:
                id: dropdown_user
                text: "Select Restaurant"
                size_hint_x: 0.7
                on_release: root.open_menu(self)

            MDRaisedButton:
                text: "View Menu"
                size_hint_x: 0.3
                on_press: root.show_menu()
            MDRaisedButton:
                text: "ViewOrders"
                size_hint_x: 0.3
                on_press: root.ViewOrders()
            MDRaisedButton:
                text: "Admin Registration"
                size_hint_x: 0.3
                on_press: root.new_admin()
            MDRaisedButton:
                text: "Sign Out"
                size_hint_x: 0.3
                on_press: root.signout()

        # Selected Restaurant Info
        MDCard:
            size_hint: (0.95, None)
            height: dp(50)
            pos_hint: {"center_x": 0.5}
            radius: [10]
            md_bg_color: 1, 1, 1, 0.8

            MDLabel:
                id: restaurant
                text: ""
                halign: "center"
                theme_text_color: "Secondary"
                valign: "middle"

        # Menu Display Section (Table)
        MDCard:
            size_hint: (0.95, None)
            height: dp(300)  # Set height to fit the table
            pos_hint: {"center_x": 0.5}
            padding: dp(10)
            radius: [10]
            md_bg_color: 1, 1, 1, 0.9  # White background for contrast

            BoxLayout:
                padding: 30
                orientation: "vertical"

                MDLabel:
                    text: "Menu Items"
                    font_style: "H6"
                    halign: "center"
                    theme_text_color: "Primary"
                    size_hint_y: None
                    height: dp(40)

                ScrollView:
                    MDList:
                        id: menu_list  # Ensure this ID matches the one in the Python code

        # Add Menu Item Section
        MDCard:
            size_hint: (0.95, None)
            height: dp(300)
            pos_hint: {"center_x": 0.5}
            padding: dp(10)
            radius: [10]
            md_bg_color: 1, 1, 1, 0.9

            MDBoxLayout:
                orientation: "vertical"
                spacing: dp(10)

                MDTextField:
                    id: item_name_input
                    hint_text: "Enter item name"
                    mode: "rectangle"
                    size_hint_x: 0.9
                    pos_hint: {"center_x": 0.5}

                MDTextField:
                    id: stock_input
                    hint_text: "Enter stock"
                    mode: "rectangle"
                    input_filter: "int"
                    size_hint_x: 0.9
                    pos_hint: {"center_x": 0.5}

                MDTextField:
                    id: price_input
                    hint_text:"Enter Price"
                    mode: "rectangle"
                    input_filter: "float"
                    size_hint_x: 0.9
                    pos_hint: {"center_x": 0.5}

                MDRaisedButton:
                    text: "Add Menu Item"
                    size_hint_x: 0.5
                    pos_hint: {"center_x": 0.5}
                    on_release: root.add_menu_item()

<EmployeeLogin>
    Image:
        source: "1main_background.webp"  # Replace with the actual file path
        size: self.parent.size
        allow_stretch: True
        keep_ratio: False
        opacity: 0.5  # Set transparency to 50%

    MDBoxLayout:
        orientation: "vertical"
        spacing: dp(10)
        padding: dp(20)
        pos_hint: {"center_x": 0.5, "center_y": 0.5}
        size_hint: None, None
        size: dp(350), dp(450)

        MDCard:
            size_hint: 1, 1
            padding: dp(20)
            elevation: 5
            radius: [20, 20, 20, 20]

            MDBoxLayout:
                orientation: "vertical"
                spacing: dp(20)

                MDLabel:
                    text: "Employee Login"
                    halign: "center"
                    font_style: "H5"
                    theme_text_color: "Primary"

                MDTextField:
                    id: username
                    hint_text: "Username"
                    icon_right: "account"
                    mode: "rectangle"

                MDTextField:
                    id: password
                    hint_text: "Password"
                    password: True
                    icon_right: "eye-off"
                    mode: "rectangle"

                MDRaisedButton:
                    text: "Login"
                    pos_hint: {"center_x": 0.5}
                    on_press: root.try_emp_login()

                MDRaisedButton:
                    text: "Customer Login"
                    pos_hint: {"center_x": 0.5}
                    on_press: root.go_login()

<HomeScreen>
    Image:
        source: "1main_background.webp"
        size: self.parent.size
        allow_stretch: True
        keep_ratio: False
        opacity: 0.5  # 50% transparency

    MDBoxLayout:
        orientation: "vertical"
        spacing: dp(20)
        padding: dp(20)

        MDLabel:
            text: "Home Screen"
            font_style: "H4"
            halign: "center"
            theme_text_color: "Primary"

        # Restaurant Selection
        MDBoxLayout:
            orientation: "horizontal"
            spacing: dp(10)
            size_hint_y: None
            height: dp(50)

            MDDropDownItem:
                id: restaurant_dropdown
                text: "Select Restaurant"
                size_hint_x: 0.7
                on_release: root.restaurant_menu.open()

            MDRaisedButton:
                text: "Place Order"
                size_hint_x: 0.5
                pos_hint: {"center_x": 0.5}
                on_release: root.place_order()

            MDRaisedButton:
                text: "Sign Out"
                size_hint_x: 0.3
                on_press: root.sign_out()

        MDLabel:
            id: restaurant_label
            text: "Select a restaurant to view the menu"
            halign: "center"
            theme_text_color: "Secondary"

        # Menu & Cart Layout (Side-by-Side)
        MDBoxLayout:
            orientation: "horizontal"
            spacing: dp(10)
            size_hint_y: None
            height: dp(400)

            # Menu Section
            MDCard:
                size_hint_x: 0.5
                height: dp(400)
                padding: dp(10)
                radius: [10]
                md_bg_color: 1, 1, 1, 0.9

                MDBoxLayout:
                    orientation: "vertical"
                    spacing: dp(10)

                    MDLabel:
                        text: "Tap an item to add it to the cart"
                        halign: "center"
                        theme_text_color: "Secondary"

                    MDScrollView:
                        MDBoxLayout:
                            orientation: "vertical"
                            id: menu_list
                            adaptive_height: True
                            spacing: dp(10)

            # Cart Section
            MDCard:
                size_hint_x: 0.5
                height: dp(400)
                padding: dp(10)
                radius: [10]
                md_bg_color: 1, 1, 1, 0.9

                MDBoxLayout:
                    orientation: "vertical"
                    spacing: dp(10)

                    MDLabel:
                        text: "Your Cart"
                        font_style: "H6"
                        halign: "center"
                        theme_text_color: "Primary"

                    MDScrollView:
                        MDBoxLayout:
                            orientation: "vertical"
                            id: cart_list
                            adaptive_height: True
                            spacing: dp(10)

                    MDLabel:
                        id: subtotal_label
                        text: "Subtotal: $0.00"
                        halign: "center"
                        theme_text_color: "Primary"
                        font_style: "H6"

<EMPRegScreen>
    Image:
        source: "1main_background.webp"  # Replace with the actual file path
        size: self.parent.size
        allow_stretch: True
        keep_ratio: False
        opacity: 0.5  # Set transparency to 50%

    MDBoxLayout:
        orientation: "vertical"
        spacing: dp(10)
        padding: dp(20)
        pos_hint: {"center_x": 0.5, "center_y": 0.5}
        size_hint: None, None
        size: dp(350), dp(450)

        MDCard:
            size_hint: 1, 1
            padding: dp(20)
            elevation: 10
            radius: [20, 20, 20, 20]

            MDBoxLayout:
                orientation: "vertical"
                spacing: dp(20)

                MDLabel:
                    text: "Register"
                    halign: "center"
                    font_style: "H5"
                    theme_text_color: "Primary"

                MDTextField:
                    id: username
                    hint_text: "Username"
                    icon_right: "account"
                    mode: "rectangle"

                MDTextField:
                    id: password
                    hint_text: "Password"
                    password: True
                    icon_right: "eye-off"
                    mode: "rectangle"

                MDRaisedButton:
                    text: "Register"
                    pos_hint: {"center_x": 0.5}
                    on_press: root.register()

                MDRaisedButton:
                    text: "Cancel"
                    pos_hint: {"center_x": 0.5}
                    on_press: root.cancel()

<RegistrationScreen>
    Image:
        source: "1main_background.webp"  # Replace with the actual file path
        size: self.parent.size
        allow_stretch: True
        keep_ratio: False
        opacity: 0.5  # Set transparency to 50%

    MDBoxLayout:
        orientation: "vertical"
        spacing: dp(10)
        padding: dp(20)
        pos_hint: {"center_x": 0.5, "center_y": 0.5}
        size_hint: None, None
        size: dp(350), dp(450)

        MDCard:
            size_hint: 1, 1
            padding: dp(20)
            elevation: 10
            radius: [20, 20, 20, 20]

            MDBoxLayout:
                orientation: "vertical"
                spacing: dp(20)

                MDLabel:
                    text: "Register"
                    halign: "center"
                    font_style: "H5"
                    theme_text_color: "Primary"

                MDTextField:
                    id: username
                    hint_text: "Username"
                    icon_right: "account"
                    mode: "rectangle"

                MDTextField:
                    id: password
                    hint_text: "Password"
                    password: True
                    icon_right: "eye-off"
                    mode: "rectangle"

                MDRaisedButton:
                    text: "Register"
                    pos_hint: {"center_x": 0.5}
                    on_press: root.register()

                MDRaisedButton:
                    text: "Login"
                    pos_hint: {"center_x": 0.5}
                    on_press: root.go_login()

<OrdersScreen>:
    Image:
        source: "1main_background.webp"  # Replace with the actual file path
        size: self.parent.size
        allow_stretch: True
        keep_ratio: False
        opacity: 0.5  # Set transparency to 50%

    MDLabel:
        title: "View Orders"
        halign: "center"
        font_style: "H5"
        theme_text_color: "Primary"

    MDCard:
        size_hint: 0.7, 0.7
        pos_hint: {"center_x":0.5, "center_y":0.5}
        padding: dp(20)
        elevation: 10
        radius: [20, 20, 20, 20]

        BoxLayout:
            orientation: "vertical"

            ScrollView:
                MDList:
                    id: orders_list

            MDRaisedButton:
                text: "Go Back"
                pos_hint: {"center_x": 0.5}
                on_press: root.go_back()
```
