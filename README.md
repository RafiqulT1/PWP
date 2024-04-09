# PWP SPRING 2024
# Hotel Booking Assistant
# Group information
* Rafiqul Talukder
* Piyumi Weebadu Arachchige
* Julius Norrena

# Hotel Booking Assistant

This Flask application serves as a hotel booking assistant, managing hotel, room, booking, customer, and admin information in a database.

## Dependencies

To run this Flask based application please install the dependencies mentioned bellow:

- Flask: `pip install Flask`(for more information check: https://flask.palletsprojects.com/en/3.0.x/)    
- Flask-SQLAlchemy: `pip install Flask-SQLAlchemy` (for more information check: https://flask-sqlalchemy.palletsprojects.com/en/3.1.x/)

## Database

The application uses SQLite as the database. SQLAlchemy is the ORM (Object-Relational Mapping) library for interacting with the database.

### Database Setup

1. **Install SQLite:**
   - Follow the instructions on the [SQLite website](https://www.sqlite.org/download.html) to download and install SQLite for your operating system.
   - during our test run we used SQLite version 3.41.2

2. **Create a Virtual Environment:**
   - It's recommended to create a virtual environment for your project. Run the following commands:
     ```
     On MacOS / Linux (bash)
     python -m venv venv
     source venv/bin/activate
     
     On Windows, use 'venv\Scripts\activate'
     ```
     For more information about python vertual environment please check: https://docs.python.org/3/library/venv.html

3. **Install Dependencies:**
   - Install the required dependencies using:
     ```bash
     pip install -r requirements.txt
     ```
     
More infomation about specific version of Flask and other technologies can be found in requirements.txt file

### Populate Database

To populate the database with sample data:

1. Ensure that `data.json` is in the same directory as `hotel_booking_assistant.db`, `orm.py` & `populate.py`.
2. Run the `populate.py` script.


# RESTful API Functional Testing

## Test Cases

### Test Case 1: Generate API Key
Description: Tests the API's ability to generate an API key for an administrator using their credentials.
Expected Outcome: The API should return a 201 status code and a new API key for valid admin credentials, a 401 error for incorrect credentials, or a 409 error if an API key already exists for the admin.

### Test Case 2: Delete API Key
Test Case 2: API Key Deletion
Description: Tests the API's functionality to delete an existing API key associated with an admin.
Expected Outcome: The API should successfully delete the API key, returning a 204 status code, or a 404 error if the API key does not exist.

### Test Case 3: Customer Information Retrieval
Description: Tests retrieving customer information using the `/api/customers/{customer_id}/` endpoint with admin authorization.
Expected Outcome: The API should return customer information for a valid request, a 403 error if the admin is unauthorized, or a 404 error if the customer does not exist.

### Test Case 4: Create Customer
Description: Tests the `/api/customers/` endpoint for creating a new customer profile.
Expected Outcome: The API should return a 201 status code if the customer is successfully created, a 409 error if the email is already in use, or an appropriate error for other issues.

### Test Case 5: Delete Customer
Description: Tests the API's ability to delete a customer profile using the `/api/customers/{customer_id}/` endpoint.
Expected Outcome: The API should return a 204 status code if the customer is successfully deleted, a 403 error if the requestor doesn't have permission, a 405 error if deletion is not permitted (the customer has bookings), or a 404 error if the customer does not exist.

### Test Case 6: Customer Information Update
Description: Tests updating information for an existing customer via the `/api/customers/{customer_id}/` endpoint.
Expected Outcome: The API should return a 204 status code if the update is successful, a 409 error if the email is in use, or a 404 error if the customer does not exist or other problems.

### Test Case 7: Room Availability Check
Description: Tests checking room availability based on specific criteria via the `/api/rooms/{country}/{city}/` endpoint.
Expected Outcome: The API should return a list of available rooms with status code of 200, or a 409 error if no rooms are available.

### Test Case 8: Booking Information Retrieval
Description: Tests retrieving information for a specific booking through the `/api/bookings/{booking_ref}/` endpoint.
Expected Outcome: The API should return the booking information with the status code of 200, if the booking exists, a 403 error if the admin is unauthorized, or a 404 error if the booking does not exist.

### Test Case 9: Delete Booking
Description: Tests the API's capability to delete a booking using the `/api/bookings/{booking_ref}/` endpoint.
Expected Outcome: The API should return a 204 status code if the booking is successfully deleted, a 403 error if the admin is unauthorized, a 404 error if the booking does not exist, or an appropriate error for other issues.

### Test Case 10: Create Booking
Description: Tests the `/api/bookings/` endpoint for creating a new booking.
Expected Outcome: The API should return a 201 status code if the booking is successfully created, a 409 error if no room of the request is/are available, otherwise it will return 404 status code.

### Test Case 11: Booking Update
Description: Tests updating an existing booking's details via the `/api/bookings/{booking_ref}/` endpoint with the right admin authorization.
Expected Outcome: The API should update the booking and return a 204 status code, a 409 error if no rooms meet the criteria, or a 404 error if the booking does not exist.
