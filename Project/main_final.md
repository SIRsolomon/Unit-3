# Criterion A: Planning

## Problem Definition
My client is Nyan, the owner of Hoffman and Company, a food-based delivery business operating in the local region. As his business expands, the current software in use is becoming inefficient in handling orders, inventory, and delivery logistics. To improve business operations and increase profitability, Nyan has requested a new software solution tailored to his needs.

The key requirements of the client include:
- Allowing customers to choose restaurants from his branches.
- Displaying the menu and item availability in real time.
- Automatically restocking items that run out.
- Providing separate functionalities for staff and customers with a login system.

## Proposed Solution
To address these needs, a web-based platform will be developed using Python as the core programming language. Python has been chosen due to its flexibility, ease of use, and extensive library support, allowing for efficient and scalable development. It is also widely used in web development, making it a practical choice for this project. Alternative languages like JavaScript with Node.js or Java were considered, but Python’s simplicity, strong database integration, and rapid development capabilities made it the ideal option.

The software will incorporate KivyMD for an intuitive and visually appealing user interface. KivyMD was chosen over alternatives like Tkinter or PyQt because it provides a modern Material Design aesthetic, making it more suitable for a web-based experience. Additionally, it integrates seamlessly with Python and is well-documented, making development smoother.

For data management, SQLite will be used as the local database solution. While MySQL and PostgreSQL were considered, SQLite was selected because it is lightweight, requires minimal setup, and is sufficient for a single-user or small-business application like this. Since the application does not require extensive concurrent user access, SQLite provides an efficient and effective data storage solution.

The platform will feature a login system that differentiates between customer and staff access. Customers will be able to browse through different restaurant branches, view available menu items, and place orders. A dictionary-based storage system will manage restaurant data dynamically, allowing seamless updates to stock levels. If an item is out of stock, an automatic restocking mechanism will replenish the inventory, preventing order failures and ensuring smooth business operations.

A local database using SQLite will be integrated to store and retrieve user data, restaurant information, and order details. This ensures persistence of data across sessions while maintaining a lightweight and efficient storage solution.

Overall, this web-based platform will enhance business efficiency by automating key processes, improving customer experience, and ensuring smooth inventory and order management. By leveraging Python’s robust capabilities, the proposed solution will meet the client’s needs effectively while allowing for future scalability and enhancements.

## Success Criteria
The project will be considered successful if it meets the following criteria:
- Customers can browse restaurants and view menu availability dynamically.
- A secure login system is implemented for both customers and staff.
- The software integrates with a local database using SQLite for data management.
- The UI is user-friendly and responsive, ensuring a smooth user experience.
- Staff can update menu items and stock levels in real-time.
- The login system should include secure password hashing to prevent unauthorized access.

## Appendix
### First Interview

#### Interviewer: Can you describe the kind of application you need for your business?

**Client:** Okay, so I own a small restaurant team. I have two restaurants, and I want an app that allows customers to order food from either location. Just something simple where they can browse the menu and place an order.

#### Interviewer: Do you need any features for managing the restaurant menu?

**Client:** Yeah, I want employees to be able to add new menu items, set prices, and maybe even upload a picture for each item. It should be easy for them to update the menu when needed.

#### Interviewer: You mentioned something about locations—can you clarify that?

**Client:** Oh yeah, it would be nice if we could add additional restaurant locations in the app if we expand in the future. Also, I was thinking about adding some sort of way to check the customer’s distance—like if they’re too far or too close, we could calculate delivery fees based on that.

#### Interviewer: Would you like a system to track customer orders?

**Client:** Yeah, keeping track of users and their past orders would be great. Maybe something like a simple order history so we know what people are ordering most. Also, it would be useful for employees to have access to orders so they can mark them as completed when they’re done.

#### Interviewer: Do you want any kind of user login system?

**Client:** Yes, definitely. We need to keep track of users, but we also want to make sure we don’t store too much personal information. Just enough for them to log in and place orders without any legal issues.

### Second Interview

#### Interviewer: Now that we have an initial idea, can you go into more detail about the functionality you want?

**Client:** Yeah, so basically, I want an app that's like a DoorDash clone. Customers should be able to choose from a list of restaurants—since I have multiple locations—and then select specific food items. The app should also check if an item is in stock before allowing them to order. If it’s not in stock, they shouldn’t be able to buy it.

#### Interviewer: Would you like a delivery cost feature?

**Client:** Yeah, I was thinking that customers should be able to input their distance from the restaurant, and based on that, we can calculate a delivery fee. Something like $20 per mile, since we’re on a hill and delivery is a bit tricky.

#### Interviewer: You mentioned a membership system before. Can you clarify how that should work?

**Client:** Right, I want a point-based membership system where the more a customer orders, the more points they get. For example, after 10, 20, or 30 orders, they could get a reward—maybe free chicken nuggets or something like that. The points should reset on the first day of every month.

#### Interviewer: Do you need specific permissions for staff?

**Client:** Yes, staff members should be able to update the availability of menu items, but they shouldn't be able to change prices unless they enter a special password. Also, staff should have the option to switch to client mode so they can place orders too.

#### Interviewer: Would you like analytics or tracking features?

**Client:** Yeah, I think it would be nice to have some way of seeing how many users there are and maybe a distribution map showing how far they are from the restaurant.

#### Interviewer: Any other final requests?

**Client:** I trust my developer! Just make sure it runs smoothly and does what we talked about.

# Criterion B: Solution Overview
## Record of Tasks
| **Date**  | **Task Description** | **Planned Outcome** | **Time Estimate** | **Target Completion Date** | **Criterion** |
|-----------|----------------------|----------------------|-------------------|--------------------------|--------------|
| Feb 3  | **Initial Client Interview** | Gather requirements and expectations from the client. | 2 hours | Feb 3 | Criterion A |
| Feb 4  | **Refining Problem Definition** | Create a clear problem statement based on client interviews. | 2 hours | Feb 4 | Criterion A |
| Feb 5  | **Drafting the Proposed Solution** | Outline software requirements and technologies to be used. | 3 hours | Feb 5 | Criterion A |
| Feb 6  | **Second Client Interview** | Validate proposed solution with client and gather additional requirements. | 2 hours | Feb 6 | Criterion A |
| Feb 7  | **Finalizing Criterion A Documentation** | Complete problem definition, proposed solution, and success criteria. | 3 hours | Feb 7 | Criterion A |
| Feb 8  | **Start Criterion B - Solution Overview** | Create system diagrams, wireframes, and flowcharts. | 4 hours | Feb 9 | Criterion B |
| Feb 10 | **Flowchart for Login System** | Design flowchart to represent authentication process. | 3 hours | Feb 10 | Criterion B |
| Feb 11 | **Flowchart for Adding New Menu Items** | Visualize stock updates. | 3 hours | Feb 11 | Criterion B |
| Feb 12 | **Flowchart for Employee Registration** | Outline how new employees are added. | 3 hours | Feb 12 | Criterion B |
| Feb 13 | **Wireframes for UI** | Create layout designs for user and staff interfaces. | 4 hours | Feb 13 | Criterion B |
| Feb 14 | **Database Schematics & ER Diagram** | Design the database structure and relationships. | 4 hours | Feb 14 | Criterion B |
| Feb 15 | **Begin Criterion C - Development** | Initialize SQLite database with users, restaurants, menu, and orders. | 3 hours | Feb 15 | Criterion C |
| Feb 16 | **Set Up UI Framework (KivyMD)** | Develop base UI components for login, home, and menu screens. | 4 hours | Feb 16 | Criterion C |
| Feb 17 | **Implement User Registration System** | Enable users to create accounts with hashed passwords. | 3 hours | Feb 17 | Criterion C |
| Feb 18 | **Implement Login System** | Develop authentication system for customers and employees. | 4 hours | Feb 18 | Criterion C |
| Feb 19 | **Test & Debug Login System** | Ensure authentication works correctly with database queries. | 3 hours | Feb 19 | Criterion C |
| Feb 20 | **Develop Menu Display Feature** | Allow users to browse restaurant menus dynamically. | 4 hours | Feb 20 | Criterion C |
| Feb 21 | **Implement Cart System** | Enable users to add/remove items from cart. | 4 hours | Feb 21 | Criterion C |
| Feb 22 | **Implement Order Placement & Stock Updates** | Ensure stock is deducted when an order is placed. | 4 hours | Feb 22 | Criterion C |
| Feb 23 | **Test & Debug Order Placement** | Fix errors related to stock updates and ordering. | 3 hours | Feb 23 | Criterion C |
| Feb 24 | **Implement Auto-Restocking Feature** | Ensure stock is replenished when reaching zero. | 4 hours | Feb 24 | Criterion C |
| Feb 25 | **Develop Employee Menu Management System** | Allow staff to add/update menu items. | 4 hours | Feb 25 | Criterion C |
| Feb 26 | **Restrict Price Editing to Admins** | Implement password-protected price modification. | 3 hours | Feb 26 | Criterion C |
| Feb 27 | **Security Implementation** | Protect against SQL injection and secure queries. | 4 hours | Feb 27 | Criterion C |
| Feb 28 | **Testing & Debugging Phase** | Conduct full system testing and fix issues. | 5 hours | Mar 1 | Criterion C |
| Mar 2  | **Final UI and UX Testing** | Ensure app is fully functional and user-friendly. | 4 hours | Mar 2 | Criterion C |
| Mar 3  | **Recording Demo Video** | Record a 4-minute video showcasing the software's functionality and testing results. | 2 hours | Mar 3 | Criterion D |
| Mar 3  | **Final Documentation & Submission** | Complete Criterion C documentation with explanations and screenshots. | 6 hours | Mar 3 | Criterion A, B, C, D |

## Test Plan
| Test Case # | Date | Feature | Test Scenario | Input | Expected Output | Actual Output | Pass/Fail |
|---|------------|----------------------|------------------------------------------------|------------------|---------------------------|------------------|-----------|
| 1  | Feb 3  | Database Setup        | Ensure database initializes correctly        | Run app         | Tables created            | Tables created   | Pass   |
| 2  | Feb 3  | Login System          | User logs in with correct credentials        | Valid username & password | Login successful | Login successful | Pass   |
| 3  | Feb 3  | Login System          | User logs in with incorrect password         | Valid username, wrong password | Error message | Error message | Pass   |
| 4  | Feb 5  | Registration          | Register a new user                          | New username & password | Account created | Account created | Pass   |
| 5  | Feb 5  | Registration          | Register a user with an existing username    | Duplicate username | Error message | Error message | Pass   |
| 6  | Feb 7  | Employee Login        | Employee logs in with correct credentials    | Valid credentials | Login successful | Error message | Fail   |
| 7  | Feb 10 | Retest Employee Login | Employee logs in with correct credentials after fix | Valid credentials | Login successful | Login successful | Pass   |
| 8  | Feb 10 | Menu Display          | Display restaurant menu                      | Restaurant selected | Menu appears | No menu displayed | Fail   |
| 9  | Feb 12 | Retest Menu Display   | Display restaurant menu after fix            | Restaurant selected | Menu appears | Menu appears | Pass   |
| 10 | Feb 12 | Cart Functionality    | Remove item from cart                        | Remove one item | Item removed | Item not removed | Fail   |
| 11 | Feb 14 | Retest Cart Removal   | Remove item from cart after fix              | Remove one item | Item removed | Item removed | Pass   |
| 12 | Feb 15 | Order Placement       | Place an order                               | Items in cart, confirm order | Order placed | Order placed | Pass   |
| 13 | Feb 15 | Order Placement       | Place order with empty cart                  | No items in cart | Error message | Error message | Pass   |
| 14 | Feb 17 | Stock Management      | Item stock decreases after order placement   | Order placed | Stock decreases | Stock remains same | Fail   |
| 15 | Feb 19 | Retest Stock Management | Item stock decreases correctly after fix   | Order placed | Stock decreases | Stock decreases | Pass   |
| 16 | Feb 20 | Auto-Restocking       | Restock items automatically when out of stock | Stock = 0 | Item restocked | Item not restocked | Fail   |
| 17 | Feb 22 | Retest Auto-Restocking | Items restock correctly after fix           | Stock = 0 | Item restocked | Item restocked | Fail   |
| 18 | Feb 22 | Employee Menu Update  | Employee adds new menu item                  | New item details | Item added to menu | Item added to menu | Pass   |
| 19 | Feb 22 | Employee Menu Update  | Employee deletes a menu item                 | Item selected | Item removed | Item removed | Pass   |
| 20 | Feb 25 | Order Tracking        | Employee marks order as completed            | Order selected | Order status updated | Order status updated | Pass   |
| 21 | Feb 27 | Security Check        | SQL Injection attempt on login               | SQL query as input | Login fails | Login fails | Pass   |
| 22 | Mar 1  | UI Testing            | Ensure all UI elements are properly aligned  | Navigate through UI | UI looks correct | Some elements misaligned | Fail   |
| 23 | Mar 3  | Retest UI Alignment   | Fix UI alignment issues                      | Navigate through UI | UI looks correct | UI looks correct | Pass   |

## System Diagram:
<img width="1022" alt="Screenshot 2025-03-11 at 11 44 08 PM" src="https://github.com/user-attachments/assets/4d02dcd1-67c0-444f-ba4c-a288e5bebbcc" />

## Wireframe for GUI:
### Wireframe: 
<img width="938" alt="Screenshot 2025-03-11 at 9 34 59 AM" src="https://github.com/user-attachments/assets/ab48f96a-fcae-47c8-a62c-87fadea2abd4" />

## FLow Diagram:
### User Login:
#### Code Segment:
```.py
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
```
#### Dirgram:
![image](https://github.com/user-attachments/assets/11cd89d7-455d-43f5-b571-d511e721b9fd)
### Register New Employee:
#### Code Segment:
```.py
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
```
#### Dirgram:
![image](https://github.com/user-attachments/assets/648d0595-3ed0-49b4-8b8d-c7e14178fc1e)
### Add New Menu Item:
#### Code Segment:
```.py
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
```
#### Dirgram:
![image](https://github.com/user-attachments/assets/68836cc1-6988-4124-8ea4-8b4c95e54630)

## ER Diagram for Databases:
<img width="657" alt="Screenshot 2025-03-11 at 3 15 54 PM" src="https://github.com/user-attachments/assets/7a1d89da-73d7-43a1-b7ab-94ef7792b129" />

## UML Diagram for OOP:
<img width="1070" alt="Screenshot 2025-03-10 at 9 53 27 PM" src="https://github.com/user-attachments/assets/af313079-a802-461e-8844-d5fe4b071493" />

## Data Storage Examples:
### Menu Items:
<img width="858" alt="Screenshot 2025-03-11 at 9 57 41 AM" src="https://github.com/user-attachments/assets/d4c16c20-588a-4595-b74d-134b7426f8df" />

### Users:
<img width="492" alt="Screenshot 2025-03-11 at 9 58 23 AM" src="https://github.com/user-attachments/assets/debdac9c-c286-46cb-a94b-1cb3d0cc3d1b" />

### Restaurants:
<img width="328" alt="Screenshot 2025-03-11 at 9 58 48 AM" src="https://github.com/user-attachments/assets/8c98d1ee-c99b-4fb5-a1fe-7ab165522d14" />

## Developmemt Process:
### **Purpose:**
The project is a food delivery management system that allows customers to browse restaurant menus, place orders, and track their purchases. It also provides employees with tools to manage inventory and order processing while ensuring secure user authentication.

### **Development Steps:**

#### **Setup and Testing:**
- Configured SQLite database to store users, restaurants, menu items, and orders.
- Implemented KivyMD framework for the user interface.
- Developed login authentication using hashed passwords with Passlib.

#### **User Authentication:**
- Created a registration and login system for both customers and employees.
- Implemented error handling for incorrect login attempts.
- Restricted certain actions (e.g., price editing) to admin users with password protection.

#### **Menu and Order Management:**
- Designed a menu display system that dynamically fetches items from the database.
- Implemented cart functionality for adding and removing items before ordering.
- Ensured stock levels update correctly when an order is placed.

#### **Employee Features:**
- Enabled employees to modify stock levels and menu availability.
- Added an order-tracking system where employees can mark orders as completed.

#### **Security and Data Integrity:**
- Implemented SQL injection protection by using parameterized queries.
- Ensured password security using encryption and secure storage.

#### **Testing and Debugging:**
- Conducted multiple test cases to ensure smooth functionality.
- Fixed login authentication bugs and stock update inconsistencies.
- Improved UI responsiveness and error messaging for better user experience.

# Criterion C: Development
## List of Features:

- User Authentification with Password Hashing.
- Database Management using SQLite
- Menu Displays using KIVYmd
- Order Tracking System
  
## Why these features?: 

### **1. User Authentication with Password Hashing**
#### **Problem/Purpose:**
The system needs to securely authenticate users without storing passwords in plain text, ensuring protection against security threats like brute force attacks. To achieve this, I implemented password hashing using Passlib. This feature ensures that even if the database is compromised, user credentials remain secure.

#### **Code:**
```python
from passlib.context import CryptContext

pwd_config = CryptContext(schemes=["pbkdf2_sha256"], default="pbkdf2_sha256", pbkdf2_sha256__default_rounds=30000)

def encryptPass(user_password):
    return pwd_config.hash(user_password)

def check_password(hashed_password, user_password):
    return pwd_config.verify(user_password, hashed_password)
```

#### **Explanation:**
- `pwd_config.hash(user_password)`: This line generates a hashed password using the PBKDF2 algorithm, making it secure against brute-force attacks.
- `pwd_config.verify(user_password, hashed_password)`: This function compares the entered password with the stored hash to authenticate users securely.

### **2. Database Management Using SQLite**
#### **Problem/Purpose:**
The system needs an efficient and structured way to store and retrieve data related to users, restaurants, menu items, and orders. SQLite was chosen due to its lightweight nature and ability to handle structured queries without requiring a separate database server.

#### **Code:**
```python
import sqlite3

class DatabaseManager:
    def __init__(self, name: str):
        self.connection = sqlite3.connect(name)
        self.cursor = self.connection.cursor()

    def search(self, query, params=()):
        self.cursor.execute(query, params)
        return self.cursor.fetchall()

    def execute(self, query, params=()):
        try:
            self.cursor.execute(query, params)
            self.connection.commit()
        except sqlite3.Error as e:
            print(f"Database error: {e}")

    def close(self):
        self.connection.close()
```

#### **Explanation:**
- `sqlite3.connect(name)`: Establishes a connection to the database file, allowing for persistent data storage.
- `search()`: Executes a SELECT query and returns results, allowing dynamic retrieval of data.
- `execute()`: Handles INSERT, UPDATE, and DELETE queries while ensuring changes are committed to the database.
- `close()`: Properly closes the database connection to prevent data corruption.

### **3. Dynamic Menu Display with KivyMD**
#### **Problem/Purpose:**
The system needs a user-friendly way to display menu items dynamically, updating the UI based on restaurant selection. KivyMD was chosen for its flexibility in creating visually appealing Material Design components.

#### **Code:**
```python
def show_menu(self):
    if self.restaurant_id is None:
        self.ids.restaurant.text = "Please select a restaurant first."
        return

    db = DatabaseManager('/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db')
    query = "SELECT item_name, price FROM menu WHERE restaurant_id = ?"
    menu_items = db.search(query, (self.restaurant_id,))
    db.close()

    self.ids.menu_list.clear_widgets()
    if not menu_items:
        self.ids.menu_list.add_widget(OneLineListItem(text="No menu items found."))
        return

    for item_name, price in menu_items:
        item = OneLineListItem(text=f"{item_name} - ${price:.2f}")
        item.bind(on_release=lambda instance, name=item_name, price=price: self.add_to_cart(name, price))
        self.ids.menu_list.add_widget(item)
```

#### **Explanation:**
- `query = "SELECT item_name, price FROM menu WHERE restaurant_id = ?"`: Fetches the menu items for the selected restaurant.
- `clear_widgets()`: Removes previous menu items to prevent duplication.
- `for item_name, price in menu_items:`: Iterates over the retrieved menu items and dynamically updates the UI.
- `OneLineListItem(text=f"{item_name} - ${price:.2f}")`: Creates a UI component displaying the menu item and price.

### **4. Order Tracking System**
#### **Problem/Purpose:**
To ensure efficient order management, the system needs to allow employees to track and mark orders as completed. This feature prevents confusion between active and fulfilled orders and ensures that staff members have clear visibility of pending customer requests.

#### **Code:**
```python
def mark_order_completed(self, order_id):
    db = DatabaseManager('/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db')
    query = "UPDATE orders SET completed = 'Yes' WHERE id = ?"
    db.execute(query, (order_id,))
    db.close()
    self.load_orders()

def load_orders(self):
    self.ids.orders_list.clear_widgets()
    db = DatabaseManager('/Users/ssolomon/PycharmProjects/Unit 3/Project/Your_bizznes.db')
    query = "SELECT id, username, User_Order, completed FROM orders WHERE completed = 'No'"
    orders = db.search(query)
    db.close()

    if not orders:
        self.ids.orders_list.add_widget(OneLineListItem(text="No Orders."))
        return

    for order_id, username, user_order, completed in orders:
        order_text = f"({order_id}) {username}: {user_order} - Pending"
        order_item = TwoLineListItem(text=order_text, secondary_text="Press to mark as completed")
        order_item.bind(on_release=lambda instance, id=order_id: self.mark_order_completed(order_id))
        self.ids.orders_list.add_widget(order_item)
```

#### **Explanation:**
- `mark_order_completed(order_id)`: Updates the order status to 'Yes' in the database, signaling that it has been fulfilled.
- `load_orders()`: Retrieves all pending orders from the database and displays them in the UI.
- `order_item.bind(on_release=lambda instance, id=order_id: self.mark_order_completed(order_id))`: Allows employees to mark orders as completed by clicking on them.

## Sources: 
### KivyMD: 
##### https://kivymd.readthedocs.io/en/latest/
### SQLite: 
##### https://www.youtube.com/watch?v=byHcYRpMgI4
### Troubleshooting Logic: 
##### https://kivycoder.com/using-mysql-database-with-kivy-python-kivy-gui-tutorial-56/
### Diagram Maker:
##### https://www.planttext.com/
### Code for Diagram Maker:
##### Chatgpt
### More Digrams:
##### Whimsical.com
### Extra
##### Past Programs developed during Unit 3.

# Criterion D: Functionality
## Video Overview of Project: 
