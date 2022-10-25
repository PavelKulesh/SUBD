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
---
Database diagram:

![alt text](Images/notnormalized.png)
---
Database description:

**Highlighted** fields are primary keys or part of them

- User - all users
   - **IdUser** - uuid
   - IdRole - uuid(foreign key)
   - Name - varchar(user name)
   - LastName - varchar(user last name)
   - PhoneNumber - varchar(user phonenumber)
   - Password - varchar(user password)
   - Email - varchar(user email)

- Role - roles for users
   - **IdRole** - uuid
   - Name - varchar(role name)

- Log - user action logs
   - **IdUser** - uuid(foreign key)
   - Date - time(time of user action)
   - Info - varchar(user action for log)

- Feedback - feedback of product
   - **IdFeedback** - uuid
   - IdProduct - uuid(foreign key)
   - Text - varchar(product feedback text)
   - User - uuid(IdUser, one to one feedback user)

- Rate - product rate
   - **IdRate** - uuid
   - IdProduct - uuid(foreign key)
   - Value - int(product rate from 1 to 5)
   - User - uuid(IdUser, one to one rate user)

- Category - product category
   - **IdCategory** - uuid
   - Name - varchar(category name)

- Product
   - **IdProduct** - uuid
   - IdCategory - uuid(foreign key)
   - Title - varchar(product title)
   - Description - varchar(product description)
   - Specifications - varchar(product specifications)
   - Cost - float(product cost)
   - Images - varchar(product images path)
   - Manufacturers - varchar(product manufacturers, many to many product manufacturer)
   - is_available - bool(is the product available or not)

- Cart
   - **IdCart** - uuid
   - Products - varchar(products inside cart)
   - User - uuid(IdUser, one to one cart user)

- Manufacturer
   - **IdManufacturer** - uuid
   - Name - varchar(manufacturer name)
   - Country - varchar(manufacturer country)
   - Products - varchar(manufacturers products)
---
