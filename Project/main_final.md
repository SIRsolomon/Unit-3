# Criterion A: Planning

## Problem Definition
My client is Nyan, the owner of Hoffman and Company, a food-based delivery business operating in the local region. As his business expands, the current software in use is becoming inefficient in handling orders, inventory, and delivery logistics. To improve business operations and increase profitability, Nyan has requested a new software solution tailored to his needs.

The key requirements of the client include:
- Allowing customers to choose restaurants from his branches.
- Displaying the menu and item availability in real time.
- Automatically restocking items that run out.
- Providing separate functionalities for staff and customers with a login system.

## Client Interview Transcripts

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

This plan ensures that the software solution effectively meets the client's needs while being scalable for future improvements.

#Critera B: 

## Test Plan

### Duration of Development: February 3, 2025 – March 3, 2025

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

## Wireframe for GUI:

## FLow Diagram:

## ER Diagram for Databases:

## UML Diagram for OOP:

