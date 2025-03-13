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
