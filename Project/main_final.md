# Criterion A: Planning
## Problem Definition:
 My client, Nyan, is the owner of Hoffman and Company, a food-based delivery business operating in the local region. As his business expands, the current software is failing to manage key operational aspects efficiently, leading to bottlenecks in order processing, inventory tracking, and delivery coordination. These inefficiencies are negatively impacting customer satisfaction and business profitability. See the evidence of consultation in the appendix.

The specific challenges faced by the client include:
- Inefficient order processing: The current system does not effectively manage multiple restaurant locations, causing delays in customer orders.
- Inventory mismanagement: There is no automated system to track stock levels, resulting in frequent shortages or overstocking.
- Lack of role-based access: Employees and customers currently use the same interface, leading to security and operational inefficiencies.
- Inaccurate menu availability: Customers often place orders for unavailable items due to a lack of real-time menu updates.

To address these issues, the client requires a robust software solution that can streamline business operations, minimize human intervention in inventory control, and ensure smooth customer interactions.

## Proposed Solution
 A web-based platform will be developed to centralize business operations and provide structured management for orders, inventory, and staff roles. The solution will include:
- A multi-branch restaurant selection system.
- A real-time menu display with automatic updates on item availability.
- An inventory management system that triggers restocking when items run out.
- A login system differentiating between staff and customers, with role-specific functionalities.

Justification of Tools:

To develop this system, the programming language options considered were C and Python. C offers high performance but lacks built-in support for rapid web development and database integration. Python, on the other hand, supports web frameworks and database connectivity, making it a better choice for this application, where structured data handling and business logic implementation are key requirements. Due to these factors, Python was selected as the primary language.

The application will use KivyMD for the interface. While other options were considered, they are primarily suited for desktop applications and lack the responsiveness required for a web-based solution. KivyMD supports a structured UI approach while ensuring compatibility with the selected development stack.

For data management, a database is required to store persistent business data, including customer orders, menu availability, and inventory levels. Without a structured database, tracking transactions across sessions would be inefficient and unreliable. The options considered were MySQL, PostgreSQL, and SQLite. Given that the application is for a small business with limited concurrent users, SQLite was chosen due to its lightweight nature and minimal setup requirements.

By addressing these specific business challenges, this software solution will improve operations, ensure seamless order processing, and allow for future scalability. 

#### See the evidence of consultation in the appendix for further details on client requirements.

## Success Criteria
The project will be considered successful if it meets the following criteria:
- The code will allow customers to browse restaurants and view menu availability dynamically.
- The code will provide users with a secure login system for both customers and staff.
- The code will be able to integrate with a local database using SQLite for data management.
- The program will allow staff to update menu items and stock levels in real-time.
- The program's login system will ensure secure password hashing to prevent unauthorized access.

# Criterion B: Solution Overview
## Record of Tasks: 
| **Task No** | **Planned Action** | **Planned Outcome** | **Time Estimate** | **Target Completion Date** | **Criterion** |
|------------|-------------------|---------------------|-------------------|--------------------------|--------------|
| 1  | Conduct initial client interview | Gather requirements and expectations from the client | 2 hours | Feb 3 | Criterion A |
| 2  | Refine problem definition | Create a clear problem statement based on client interviews | 2 hours | Feb 4 | Criterion A |
| 3  | Draft the proposed solution | Outline software requirements and technologies to be used | 3 hours | Feb 5 | Criterion A |
| 4  | Conduct second client interview | Validate proposed solution with client and gather additional requirements | 2 hours | Feb 6 | Criterion A |
| 5  | Finalize Criterion A documentation | Complete problem definition, proposed solution, and success criteria | 3 hours | Feb 7 | Criterion A |
| 6  | Create system diagrams, wireframes, and flowcharts | Provide a visual representation of how the system functions | 4 hours | Feb 9 | Criterion B |
| 7  | Develop flowchart for login system | Represent authentication process graphically | 3 hours | Feb 10 | Criterion B |
| 8  | Develop flowchart for order placement & stock management | Visualize order processing and inventory updates | 3 hours | Feb 11 | Criterion B |
| 9  | Develop flowchart for employee menu management | Outline how employees update and modify menu items | 3 hours | Feb 12 | Criterion B |
| 10 | Design UI wireframes | Create layout designs for user and staff interfaces | 4 hours | Feb 13 | Criterion B |
| 11 | Design database schema & ER diagram | Define relationships between entities in the database | 4 hours | Feb 14 | Criterion B |
| 12 | Initialize SQLite database | Set up tables for users, restaurants, menu items, and orders | 3 hours | Feb 15 | Criterion C |
| 13 | Set up UI framework using KivyMD | Develop base UI components for login, home, and menu screens | 4 hours | Feb 16 | Criterion C |
| 14 | Implement user registration system | Enable users to create accounts with hashed passwords | 3 hours | Feb 17 | Criterion C |
| 15 | Implement login system | Develop authentication system for customers and employees | 4 hours | Feb 18 | Criterion C |
| 16 | Test and debug login system | Ensure authentication works correctly with database queries | 3 hours | Feb 19 | Criterion C |
| 17 | Develop dynamic menu display feature | Allow users to browse restaurant menus dynamically | 4 hours | Feb 20 | Criterion C |
| 18 | Implement cart system | Enable users to add/remove items from cart | 4 hours | Feb 21 | Criterion C |
| 19 | Implement order placement & stock updates | Ensure stock is deducted when an order is placed | 4 hours | Feb 22 | Criterion C |
| 20 | Test and debug order placement | Fix errors related to stock updates and ordering | 3 hours | Feb 23 | Criterion C |
| 21 | Implement auto-restocking feature | Ensure stock is replenished when reaching zero | 4 hours | Feb 24 | Criterion C |
| 22 | Develop employee menu management system | Allow staff to add/update menu items | 4 hours | Feb 25 | Criterion C |
| 23 | Restrict price editing to admins | Implement password-protected price modification | 3 hours | Feb 26 | Criterion C |
| 24 | Implement order tracking system | Allow employees to mark orders as completed | 4 hours | Feb 27 | Criterion C |
| 25 | Conduct security implementation | Protect against SQL injection and secure database queries | 4 hours | Feb 28 | Criterion C |
| 26 | Conduct full system testing and debugging | Fix remaining issues to ensure stability | 5 hours | Mar 1 | Criterion C |
| 27 | Conduct final UI and UX testing | Ensure the application is fully functional and user-friendly | 4 hours | Mar 2 | Criterion C |
| 28 | Complete final documentation | Prepare Criterion C documentation with explanations and screenshots | 6 hours | Mar 3 | Criterion A, B, C |
| 29 | Record demo video | Demonstrate application functionality for submission | 2 hours | Mar 3 | Criterion D |

## Test Plan:
| **Test No** | **Test Type** | **Procedure** | **Expected Outcome** |
|------------|-------------|-------------|--------------------|
| 1 | Secure Login System | 1. Open the application and navigate to the login screen.<br>2. Enter a valid customer username 'user' in the "Username" input field.<br>3. Enter the correct password 'pass' in the "Password" input field.<br>4. Tap the "Login" button.<br>5. Verify that the application redirects the user to the home screen. | The user is authenticated and redirected to the home screen. |
| 2 | Dynamic Menu Display | 1. Open the application and log in as a customer with username: user and password: new.<br>2. On the home screen, tap the "Select Restaurant" dropdown menu.<br>3. Choose the first restaurant from the list by tapping on its name (Prince Hotel).<br>4. Verify that the menu list updates to display items available at the selected restaurant (Apple Pie, Peach Cobbler, Potato). | The menu dynamically updates to display available items for the selected restaurant. |
| 3 | Database Integration | 1. Open the application and navigate to the registration screen.<br>2. Enter any new username in the "Username" input field.<br>3. Enter any password in the "Password" input field.<br>4. Tap the "Register" button.<br>5. Close the application by pressing escape and open the SQLite database file.<br>6. Run a query to check if the new username exists in the "users" table by entering [Select * from users].<br>7. Verify that the new user’s data is stored in the database. | The new account is successfully stored in the database. |
| 4 | Staff Menu Management | 1. Open the application and log in as a staff member, by selecting 'admin' then login with username: empl and password: pass.<br>2. Select any restaurant of your choice in the by using the select restaurant drop down menu.<br>3. Tap "View Menu" to access the menu.<br>4. Select an existing menu item by tapping on it.<br>5. Using the entry fields at the bottom of the screen enter 'enter item name': Bread, 'enter stock': 10, 'enter price': 10.<br>6. Tap the "Add Menu Item" button.<br>7. Look at the menu screen and verify that the stock update is reflected in the system. | The updated stock value is reflected in the system. |
| 5 | Password Security | 1. Open the application and navigate to the registration screen by pressing register.<br>2. Register a new user by entering any username and password in the respective fields.<br>3. Close the application and open the SQLite database file.<br>4. Run a query to check the stored password in the "users" table using [Select * from users].<br>5. Verify that the username appears but next to it is a random string of text that was not entered which shows that the password is hashed and not in plaintext. | Passwords are hashed and not stored in plaintext. |

## System Diagram:
<img width="1022" alt="Screenshot 2025-03-11 at 11 44 08 PM" src="https://github.com/user-attachments/assets/4d02dcd1-67c0-444f-ba4c-a288e5bebbcc" />

- Figure 1: System diagram of the program.
## Wireframe: 
<img width="938" alt="Screenshot 2025-03-11 at 9 34 59 AM" src="https://github.com/user-attachments/assets/ab48f96a-fcae-47c8-a62c-87fadea2abd4" />

- Figure 2: Wireframe diagram showing GUI relationships.
  
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

- Figure 3: Diagram showing the above code segment.
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

- Figure 4: Diagram showing the above code segment.

### Load Orders:
#### Code Segment:
```.py
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
```
#### Dirgram:
<img width="614" alt="Screenshot 2025-03-14 at 8 23 21 AM" src="https://github.com/user-attachments/assets/0bb7e605-36c5-409f-9309-0983b58d45d9" />

- Figure 5: Diagram showing the above code segment.

## ER Diagram:
<img width="931" alt="Screenshot 2025-03-14 at 0 46 22 PM" src="https://github.com/user-attachments/assets/dc6f4df8-f710-4349-b9e7-c84a177eb692" />

- Figure 6: Entity relationship diagram.
  
## UML Diagram for OOP:
<img width="1070" alt="Screenshot 2025-03-10 at 9 53 27 PM" src="https://github.com/user-attachments/assets/af313079-a802-461e-8844-d5fe4b071493" />

- Figure 7: Diagram showing the relationships in my OOP.
## Data Storage Examples:
### Menu Items:
<img width="858" alt="Screenshot 2025-03-11 at 9 57 41 AM" src="https://github.com/user-attachments/assets/d4c16c20-588a-4595-b74d-134b7426f8df" />

- Figure 8: Example data for menu items.
### Users:
<img width="492" alt="Screenshot 2025-03-11 at 9 58 23 AM" src="https://github.com/user-attachments/assets/debdac9c-c286-46cb-a94b-1cb3d0cc3d1b" />

- Figure 9: Example data for users.
### Restaurants:
<img width="328" alt="Screenshot 2025-03-11 at 9 58 48 AM" src="https://github.com/user-attachments/assets/8c98d1ee-c99b-4fb5-a1fe-7ab165522d14" />

- Figure 10: Example data for restaurants.
  
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

- User Authentication with Password Hashing
- Database Management using SQLite
- Menu Display using KivyMD
- Order Tracking System

## Why these features?

### **1. User Authentication with Password Hashing**
#### **Problem/Purpose:**
In the early stages of development, I realized that storing passwords in plain text was a major security risk. To prevent brute force attacks and protect user data, I implemented Passlib for password hashing. This was a challenging aspect as I had to learn about hashing algorithms and the PBKDF2 standard.

#### **Code:**
```python
from passlib.context import CryptContext

pwd_config = CryptContext(schemes=["pbkdf2_sha256"], default="pbkdf2_sha256", pbkdf2_sha256__default_rounds=30000)

def encryptPass(user_password):
    return pwd_config.hash(user_password)

def check_password(hashed_password, user_password):
    return pwd_config.verify(user_password, hashed_password)
```

#### **Challenges and Solutions:**
- **Challenge:** Understanding how to store the hash in the database and verify it during login.
- **Note:** Initially, I tried manually encrypting the passwords with basic Python hash functions, but this was not long and inefficient.
- **Solution:** I researched the Passlib library and implemented a simple yet secure function for both hashing and verification.

#### **Skills Demonstrated:**
- Secure handling of user data
- Working with cryptographic libraries

---

### **2. Database Management Using SQLite**
#### **Problem/Purpose:**
To efficiently handle user data, restaurant menus, and order history, I opted for SQLite due to its simplicity and compatibility with KivyMD.

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

#### **Challenges and Solutions:**
- **Challenge:** Preventing SQL injection when handling user input.
- **Note:** Using the sql while the code was running took me a while to get right and I had to take andvantage of lambda functions which I learned to use.
- **Solution:** I switched to using parameterized queries to secure the database.

#### **Skills Demonstrated:**
- Database management
- Secure handling of data input

---

### **3. Dynamic Menu Display with KivyMD**
#### **Problem/Purpose:**
I needed to display the menu dynamically based on the restaurant selected by the user. KivyMD allowed me to create a user-friendly interface that updates in real time.

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

#### **Challenges and Solutions:**
- **Challenge:** Preventing duplication of menu items when switching between restaurants.
- **Note:** Initially, I did not know to clear the previous menu items, leading to duplicated listings when switching between restaurants and infinite menus.
- **Solution:** Using `clear_widgets()` to refresh the UI before displaying the new menu.

#### **Skills Demonstrated:**
- UI/UX development
- Real-time data display

---

### **4. Order Tracking System**
#### **Problem/Purpose:**
To ensure that employees can keep track of pending orders and mark them as completed, I implemented an order tracking system that interacts with the database.

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

#### **Challenges and Solutions:**
- **Challenge:** Avoiding data duplication and ensuring the UI updates after marking an order as complete.
- **Note:** I updated the database without reloading the UI so even though it was not a widget I still had duplicated data and infinite menus again.
- **Solution:** Using the `load_orders()` function to refresh the order list after updating the database.

#### **Skills Demonstrated:**
- Backend-frontend interaction
- Real-time database updates

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
