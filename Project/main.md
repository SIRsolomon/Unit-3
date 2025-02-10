# Criterion A: Planning
## Problem Definition:
### My client is Nyan owner of Hoffman and Company, a food based delivery business which operates in the local region. As his business is expanding the software at his diposal is in need of an upgrade to enhance the efficiency of his business and increase profits. This has led him to reach out to my company to develop specialized software to math his needs.
### Based on the clients requirements, a web based platform will be created which includes the following: 
- Allowing customers to choose returants from his braches, Allowing customers to view the menu and item availability and automatically.
- Restock on items which are out of stock. 
- Calculating delivery costs to clients locations using their areas. 
- Having a membership rewards based system with milestones at certain numbers of points/orders and resets every month and uses a local database. 
- Having a staff function as well as a user fuction in separate menus with log in system.

## Proposed Solution:
### Software: Python: Python is selected as the programming language due to its open-source nature, ease of use, and cross-platform compatibility. Its high-level programming structure simplifies tasks such as data processing and GUI development, which are critical for this project. Unlike lower-level languages like C/C++, Python automates memory management and offers an extensive library ecosystem, enabling rapid development and scalability. Python also supports seamless integration with many devices, ensuring clear and effective communication of the results to the client.
### Specific solution:  
1. Use of KivyMD for UI Enhancements:
- MDApp: Inherits from MDApp to use Material Design components.
- MDRaisedButton: Used for restaurant selection buttons.
- MDLabel: Displays menu items and other information.
- MDDataTable (potential improvement): Could be used for a more structured menu display.
2. Screen Management:
- ScreenManager: Manages multiple screens for different app functionalities.
- Separate Screens: Login, Home, Restaurant Selection, Menu, Membership, and Delivery.
3. User Authentication System:
- Dictionary-Based User Database: Simulates login credentials (users = {}).
- LoginScreen: Users input credentials to authenticate before accessing features.
4. Restaurant and Menu Management:
- Dictionary-Based Restaurant Data: Holds restaurant names, menu items, and stock levels.
- Dynamic UI Updates: Buttons are generated dynamically for restaurants.
- Stock Management: Items automatically restock when they reach zero.
5. Automatic Restocking System:
- When a menu item is out of stock, it is automatically replenished (restaurants[branch][item] = 5).
- Prevents orders from failing due to stock unavailability.
6. Delivery Cost Calculation:
- Area-Based Pricing: Uses a dictionary to assign costs based on user input.
- Dynamic Updates: Users input their area, and the cost updates dynamically.
7. Membership Rewards System:
- Points Accumulation: Users earn points per order.
- Milestone Tracking: Rewards unlock at 100 points, and the system resets monthly.
- Dictionary Storage (membership_points): Simulates a database to track user progress.
8. Local Database Simulation:
- Dictionaries as Databases: Users, restaurants, and membership points are stored in dictionaries.
9. SQLite:
- Uses the SQL to connect, update, and get information from a local database and serves as the core aspect of the program. 
