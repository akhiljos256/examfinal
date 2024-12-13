# Best Buy Staff Service

This is a simple staff-service microservice built using Flask. It provides CRUD operations for managing staff information.

## API Endpoints

1. **Create staff** (`POST /staff`)
   - Request body:
     ```json
     {
       "name": "John Doe",
       "position": "Sales Associate",
       "department": "Sales",
       "email": "john.doe@bestbuy.com",
       "phone": "123-456-7890"
     }
     ```
   - Response: 201 Created, staff information

2. **Get staff** (`GET /staff/<id>`)
   - Response: 200 OK, staff information

3. **Update staff** (`PUT /staff/<id>`)
   - Request body:
     ```json
     {
       "name": "John Doe",
       "position": "Manager",
       "department": "Sales",
       "email": "john.doe@bestbuy.com",
       "phone": "123-456-7890"
     }
     ```
   - Response: 200 OK, updated staff information

4. **Delete staff** (`DELETE /staff/<id>`)
   - Response: 200 OK, deletion message

## Running the Application

1. Install dependencies:
