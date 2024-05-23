# Cafe API

This project provides a RESTful API to manage a collection of cafes. The API allows you to perform CRUD (Create, Read,
Update, Delete) operations on cafes, including searching for cafes by location, retrieving a random cafe, and updating
cafe information.

## Getting Started

These instructions will guide you through setting up and running the project on your local machine for development and
testing purposes.

### Prerequisites

Ensure you have the following installed:

- Python 3.7 or higher
- Flask
- Flask-SQLAlchemy

### Installation

1. **Clone the repository:**
2. **Create a virtual environment and activate it:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate` 
    ```
3. **Install the required packages:**
    ```bash
    pip install -r requirements.txt
    ```
4. **Set up the database:**
    - The SQLite database will be created automatically when you first run the application.

### Running the Application

1. Run the Flask application

```bash
    pyton main.py
```

### API Endpoints

#### Home

- GET /
- Renders the home page.

#### Get a Random Cafe

- GET /random
- Returns a random cafe from the database.

```json
{
  "cafe": {
    "id": 1,
    "name": "Cafe Name",
    "map_url": "http://mapurl.com",
    "img_url": "http://imageurl.com",
    "location": "City",
    "seats": "50",
    "has_toilet": true,
    "has_wifi": true,
    "has_sockets": true,
    "can_take_calls": true,
    "coffee_price": "€2.50"
  }
}

```

#### Get All Cafes

- GET /all
- Returns all cafes in the database.

```json
{
  "cafe": [
    {
      "id": 1,
      "name": "Cafe Name",
      "map_url": "http://mapurl.com",
      "img_url": "http://imageurl.com",
      "location": "City",
      "seats": "50",
      "has_toilet": true,
      "has_wifi": true,
      "has_sockets": true,
      "can_take_calls": true,
      "coffee_price": "€2.50"
    },
    ...
  ]
}
```

#### Search Cafe by Location

- GET /search?loc=<location>
- Returns cafes located in the specified location.

```json
{
  "cafes": [
    {
      "id": 1,
      "name": "Cafe Name",
      "map_url": "http://mapurl.com",
      "img_url": "http://imageurl.com",
      "location": "City",
      "seats": "50",
      "has_toilet": true,
      "has_wifi": true,
      "has_sockets": true,
      "can_take_calls": true,
      "coffee_price": "€2.50"
    }
  ]
}
```

- If no cafes are found:

```json
{
  "error": {
    "Not Found": "Sorry, we don't have a cafe at that location."
  }
}
```

#### Add a New Cafe

- POST /add
    - Adds a new cafe to the database. Requires the following form data:
        - name
        - map_url
        - img_url
        - loc (location)
        - seats
        - sockets (boolean)
        - toilet (boolean)
        - wifi (boolean)
        - calls (boolean)
        - coffee_price (optional)

```json
{
  "response": {
    "success": "Successfully added the new cafe."
  }
}
```

#### Update Cafe Price

- PATCH /update-price/int:cafe_id?new_price=<new_price>
- Updates the coffee price of a specified cafe.

```json
{
  "response": {
    "success": "Successfully updated the price."
  }
}
```

- If the cafe is not found:

```json
{
  "error": {
    "Not Found": "Sorry a cafe with that id was not found in the database."
  }
}
```

#### Delete a Cafe

- DELETE /report-closed/int:cafe_id?api-key=<api_key>
- Deletes a specified cafe from the database. Requires an API key (TopSecretAPIKey).

```json
{
  "response": {
    "success": "Successfully deleted the cafe from the database."
  }
}
```

- If the cafe is not found:

```json
{
  "error": {
    "Not Found": "Sorry a cafe with that id was not found in the database."
  }
}
```

- If the API key is incorrect:

```json
{
  "error": {
    "Forbidden": "Sorry, that's not allowed. Make sure you have the correct api_key."
  }
}
```

## Screenshots

<img alt="RESTFull API Screenshot 1" src="/screenshots/restfull_api_1.png" />
<img alt="RESTFull API Screenshot 1" src="/screenshots/restfull_api_2.png" />
<img alt="RESTFull API Screenshot 1" src="/screenshots/restfull_api_3.png" />