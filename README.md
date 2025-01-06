# urban-matching-app
# UrbanMatch-PythonTask

his project is a Matchmaking API built with FastAPI, designed to manage user profiles and facilitate matchmaking based on location and interests. The API enables the creation, retrieval, updating, and deletion of user profiles, each containing essential information such as the user's email, name, age, gender, city, and interests.

Key features of the API include:

User Profile Management: The ability to create, view, update, and delete user profiles, ensuring seamless profile management for users.

User Matching: An advanced feature that allows users to be matched with others based on shared interests and location (city). This helps to suggest meaningful connections for users, based on their preferences and demographics.

## Assumptions Made

- The `interests` field is treated as a single string, rather than a list of strings. This simplifies the storage and retrieval of user interests but may limit flexibility if users wish to select multiple distinct interests.
- The email field is validated using `Pydantic's EmailStr`, ensuring that only valid email formats are accepted when creating or updating user profiles.
- The `gender` field is assumed to be a string.
- The `age` field is assumed to be an integer. This field stores the user's age as a numerical value, making it easy to perform comparisons or calculations involving age.
- he `city` field is assumed to be a string. It stores the name of the city where the user resides and is used for location-based matching with other users.

## Project Structure

- `main.py`: The main FastAPI application file containing route definitions.
- `models.py`: SQLAlchemy models for the User entity.
- `schemas.py`: Pydantic models for request and response validation.
- `database.py`: Database setup and session creation.
- `requirements.txt`: Dependencies for the project.

## Pre  Requirements

- Python 3.7+
- FastAPI
- SQLAlchemy
- Pydantic
- SQLite 
- Uvicorn

## Setup

1. **Clone the repository:**
    ```sh
    git clone <repository_url>
    ```

2. **Create and activate a virtual environment:**
    ```sh
    python -m venv env
    source env/bin/activate 
    ```

3. **Install dependencies:**
    ```sh
    pip install -r requirements.txt
    ```

4. **Run the application:**
    ```sh
    uvicorn main:app --reload
    ```

## Usage
```sh 
   for better readability 
   check in swagger http://127.0.0.1:8000/docs
   ```

### Endpoints

- **GET /users/**
    - Retrieve all users.
    - Response: List of user profiles.

- **POST /users/**
    - Create a new user.
    - Request body: JSON object containing `email`, `name`, `age`, `gender`, `city`, and `interests`.
    - Response: Created user profile.

- **GET /users/{user_id}**
    - Retrieve a specific user by ID.
    - Response: User profile.

- **PUT /users/{user_id}**
    - Update an existing user by ID.
    - Request body: JSON object containing any of the fields  `name`, `age`, `gender`, `city`, or `interests`.
    - Response: Updated user profile.

- **DELETE /users/{user_id}**
    - Delete a user by ID.
    - Response: Confirmation message.

- **GET /users/{user_id}/matches**
    - Find matches for a user based on city and interests.
    - Response: List of matching user profiles.
