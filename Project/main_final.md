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
- Orders are processed efficiently, with automatic restocking when necessary.
- A secure login system is implemented for both customers and staff.
- The software integrates with a local database using SQLite for data management.
- The UI is user-friendly and responsive, ensuring a smooth user experience.
- Staff can update menu items and stock levels in real-time.
- The database should efficiently handle at least 100 orders per day without performance degradation.
- The login system should include secure password hashing to prevent unauthorized access.

This plan ensures that the software solution effectively meets the client's needs while being scalable for future improvements.

