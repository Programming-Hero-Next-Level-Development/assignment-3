# assignment-3

### Assignment Requirements: Online Cow Selling Backend for Eid Ul Adha


You have been assigned the task of building the backend for an Online Cow Selling platform in preparation for Eid Ul Adha. The main focus of this assignment is to implement error handling, CRUD operations, pagination and filtering, transactions (including a simple transaction without a payment gateway), and additional routes as deemed necessary. 

### Technology Stack:

- Use TypeScript as the programming language.
- Use Express.js as the web framework.
- Use Mongoose as the Object Data Modeling (ODM) and validation library for MongoDB.


### Error Handling:

Implement proper error handling throughout the application.
Use middleware to catch and handle errors, providing appropriate error responses with status codes and error messages.

Error Response Object Should include the following properties:
- success  →  false
- message → Error Type 
- errorMessage : [
          {
            path: '',
            message:''
          }
        ]\
- stack: '' → Do this for both production and developmentb to evaluale your assignment
                  
                        ]
### Model:

### User:
- _id
- phoneNumber
- role   → enums → [‘seller’,’buyer’]
- password 
- name	
- firstName
- lastName
- address
- amount → Savings for buying cow


### Cow:

-name: The name of the cow.
-age: The age of the cow in years.
-price: The price of the cow.
-location: Enums of location
  -Dhaka
  -Chattogram
  -Barishal
  -Rajshahi
  -Sylhet
  -Comilla
  -Rangpur
  -Mymensingh

-breed: The breed of the cow → embedded 
  -Brahman 
  -Nellore 
  -Sahiwal 
  -Gir 
  -Indigenous 
  -Tharparkar 
  -Kankrej 

-weight: The weight of the cow in kilograms.
-label: The enums of the label.
  -For sale
  -Sold out

-category: An enum representing the category of the cow.
  -Dairy = "Dairy",  // Represents cows bred primarily for milk production.
  -Beef = "Beef", // Represents cows bred primarily for meat production.
  -DualPurpose = "Dual Purpose", // Represents cows bred for both milk and meat production.

-seller: A reference ID that identifies the seller of the cow, allowing for tracking and association with the seller's information .


### Implement Create, Read, Update Operations for Users Listing

### Create a new User 

 Route:  /api/v1/auth/signup (POST)
 Request body:
 {
  "_id":"ObjectId(“6473c6a50c56d0d40b9bb6a3)",  
  "phoneNumber":"01711111111",
  "password":"abrakadabra",
  "role":"buyer",
  "address":"Chattogram",
  "amount":30000  // saved money to buy cow
}
         
 Response: The newly created user object.
 Response Sample Pattern:

 {
      success: true, 
      statusCode:200 ,
      message:'Users created successfully',
      data: {} , 
  }


           
### Get All Users

 Route:  /api/v1/users (GET)
 Request body:
 Response: The users array of objects.
 Response Sample Pattern:

  {
      success: true, 
      statusCode:200 ,
      message:'Users retrieved successfully',
      meta: {
        page: 3,
        limit: 10,
        }
      data: [{}] , 
  }

### Retrieve paginated and filtered cow listings: ( You do not need to implement pagination like we implemented , you can do as you want )

Route:  /api/v1/cows
Query parameters:
          page: The page number for pagination (e.g., ?page=1).
          limit: The number of cow listings per page (e.g., ?limit=10).
          sortBy: The field to sort the cow listings (e.g., ?sortBy=price).
          sortOrder: The order of sorting, either 'asc' or 'desc' (e.g., ?sortOrder=asc).
          minPrice: The minimum price for filtering (e.g., ?minPrice=1000).
          maxPrice: The maximum price for filtering (e.g., ?maxPrice=5000).
l         ocation: The location for filtering (e.g., ?location=chattogram).
          searchTerm: The search query string for searching cows (e.g., ?query=Dhaka). (Search Fields should be location, breed, category) 

Response: An array of cow listing objects that match the provided filters, limited to the specified page and limit.

Response Sample Pattern:

  {
      success: true, 
      statusCode:200 ,
      message:'Users retrieved successfully',
      meta: {
        page: 3,
        limit: 10,
        }
      data: [{}] , 
  }



### Get a Single User

Route:  /api/v1/users/:id (GET)
Request Param: :id
Response: The user object.
Response Sample Pattern:

  {
      success: true,  
      statusCode:200 ,
      message:'User retrieved successfully',
      data: {} , 
  }

### Update a Single User

 Route:  /api/v1/users/"id (PATCH)
 Request Param: :id
 Response: 'User updated successfully;
 Response Sample Pattern:

  {
      success: true, 
      statusCode:400 ,
      message:'Uers retrieved successfully',
      data: {} , 
  }
  
  
  ### Delete a User

 Route:  /api/v1/users/"id (PATCH)
 Request Param: :id
 Response: 'User deleted successfully;
 Response Sample Pattern:

  {
      success: true, 
      statusCode:200 ,
      message:'Uers deleted successfully',
      data: {} , 
  }


### Implement Create, Read, Update , Delete Operations for COW listings.



### Create a new cow listing:


### Create a New Cow

 Route:  /api/v1/cows (POST)
 Request body:
 {
  "_id":"ObjectId(“6473c6a50c56d0d40b9bb6a3)",  
  "name": " Cow",
  "age": 3,
  "price": 5000,
  ..............
}
 Response: The newly created cow object.
 Response Sample Pattern:

 {
      success: true, 
      statusCode:200 ,
      message:'Users created successfully',
      data: {} , 
  }


           
### Get All Cows

 Route:  /api/v1/cows (GET)
 Request body:
 Response: The cows array of objects.
 Response Sample Pattern:

  {
      success: true, 
      statusCode:200 ,
      message:'cows retrieved successfully',
      meta: {
        page: 3,
        limit: 10,
        }
      data: [{}] , 
  }


### Get a Single Cow

Route:  /api/v1/cows/:id (GET)
Request Param: :id
Response: The cow object.
Response Sample Pattern:

  {
      success: true,  
      statusCode:200 ,
      message:'Cow retrieved successfully',
      data: {} , 
  }

### Update a Single Cow

 Route:  /api/v1/cow/:id (PATCH)
 Request Param: :id
 Response: 'Cow updated successfully;
 Response Sample Pattern:

  {
      success: true, 
      statusCode:400 ,
      message:'Cow retrieved successfully',
      data: {} , 
  }
  
  
  ### Delete a Cow

 Route:  /api/v1/cows/:id (PATCH)
 Request Param: :id
 Response: 'Cows deleted successfully;
 Response Sample Pattern:

  {
      success: true, 
      statusCode:200 ,
      message:'Cow deleted successfully',
      data: {} , 
  }

     


### Bonus :  Implement Create, Read Operations for Order History Listings.

Route:  /api/v1/orders  (POST)
Request body:{
{
  "cow":"ObjectId(“6473c6a50c56d0d40b9bb6a3)", // cow reference _id
  "buyer":"ObjectId(“6473c6a50c56d0d40b9bb6a3)", // user reference  _id
}
}
Response: The  newly created order object.



Route:  /api/v1/orders  (GET)
Request body:
Response: The orders array of object.

Implement a transactional operation for buying a cow.  When a user requests to buy a cow, simulate a transaction process without involving an actual payment gateway.Upon successful transaction simulation, update the cow's status as sold, transfer money from buyer to seller account, and provide appropriate response messages.

Steps:
-The user initiates a purchase order using the "api/v1/orders" POST API.
-Check that the user has enough money in their account to buy the cow.
-If the user needs more money, show them an error message.
-If the user has enough money, begin the buying process (start a transaction). This involves a few steps:
-Change the cow's label from 'for sale' to 'sold out'.
-Deduct the cost of the cow from the buyer's account
-Put the same amount of  cost into the seller's account
-Make an entry in the orders collection
-Commit transaction
-End transaction session
-If any error happens abort the transaction 





### Sample Data: (User)

{
  "_id":"ObjectId(“6473c6a50c56d0d40b9bb6a3)",  
  "password":"abrakadabra",
  "role":"buyer",
   "name":{
      firstName:"Mr. Babull"
      latName:"Bro"
    },
  "phoneNumber":"01711111111",
  "address":"Chattogram",
  "amount":30000  
}



