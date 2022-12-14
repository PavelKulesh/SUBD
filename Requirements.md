## Requirements:
1. User roles:
   - default
   - admin
---
1. Default user:
   - authentification
   - rate the product
   - leave a review about the product
   - add product to cart
2. Admin:
   - delete reviews
   - add, delete and edit products
   - edit user info
   - check log list
---
Database diagram:

![alt text](images/diagram.png)
---
Database description:

**Highlighted** fields are primary keys or part of them

- User - all users
   - **IdUser** - uuid
   - IdRole - uuid(foreign key)
   - Name - varchar(20)(user name)
   - LastName - varchar(20)(user last name)
   - PhoneNumber - varchar(20)(user phonenumber)
   - Password - varchar(20)(user password)
   - Email - varchar(30)(user email)

- Role - roles for users
   - **IdRole** - uuid
   - Name - varchar(20)(role name)

- Log - user action logs
   - **IdUser** - uuid(foreign key)
   - Date - datetime(date and time of user action)
   - Info - varchar(100)(user action for log)

- Feedback - feedback of product
   - **IdFeedback** - uuid
   - IdProduct - uuid(foreign key)
   - Text - varchar(200)(product feedback text)
   - User - uuid(IdUser, one to one feedback user)

- Rate - product rate
   - **IdRate** - uuid
   - IdProduct - uuid(foreign key)
   - Value - tinyint(product rate from 1 to 5)
   - User - uuid(IdUser, one to one rate user)

- Category - product category
   - **IdCategory** - uuid
   - Name - varchar(30)(category name)

- Product
   - **IdProduct** - uuid
   - IdCategory - uuid(foreign key)
   - Title - varchar(50)(product title)
   - Description - varchar(500)(product description)
   - Specifications - varchar(500)(product specifications)
   - Cost - float(product cost)
   - Images - varchar(100)(product images path)
   - is_available - bool(is the product available or not)

- Order
   - **IdOrder** - uuid
   - User - uuid(IdUser, one to one cart user)
   - Date - datetime(date and time of the order (blank = True))

- Manufacturer
   - **IdManufacturer** - uuid
   - Name - varchar(50)(manufacturer name)
   - Country - varchar(50)(manufacturer country)

- ManufacturerProduct - many-to-many table between Manufacturer and Product
   - IdManufacturer - uuid(foreign key)
   - IdProduct - uuid(foreign key)

- ProductOrder - many-to-many table between Order and Product
   - IdOrder - uuid(foreign key)
   - IdProduct - uuid(foreign key)
---
Normalized Database diagram:

![alt text](images/Normalized.png)
---
