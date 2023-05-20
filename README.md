# Authentication and Authorization API

This is a simple RESTful API built with Flask that provides user registration, login, and token-based authentication. It allows users to register, log in, and access protected endpoints by providing a valid access token.

## Installation

1. Clone the repository:

   ```shell
   git clone https://github.com/BitH0xker/Authentication-and-Authorization-API.git
   ```

2. Navigate to the project directory:

   ```shell
   cd Authentication-and-Authorization-API
   ```

3. Install the required dependencies:

   ```shell
   pip install -r requirements.txt
   ```

## Usage

1. Start the server:

   ```shell
   python app.py
   ```

2. The API is now running locally at `http://localhost:5000`.

### User Registration

**Endpoint**: `POST /register`

Register a new user by sending a JSON payload with the following fields:

```json
{
  "username": "your-username",
  "email": "your-email@example.com",
  "password": "your-password"
}
```

### User Login

**Endpoint**: `POST /login`

Log in with an existing user by sending a JSON payload with the following fields:

```json
{
  "username": "your-username",
  "password": "your-password"
}
```

The response will contain an access token that can be used for authentication.

### Protected Endpoint

**Endpoint**: `GET /protected`

Access a protected endpoint by including the access token in the `Authorization` header of the request:

```shell
curl -X GET http://localhost:5000/protected -H "Authorization: Bearer your-access-token"
```

## Contributing

Contributions are welcome! If you find a bug or want to enhance the functionality of this API, feel free to open an issue or submit a pull request.

## Update Notes

Version 1.0 - 
1. `User registration`: Allows users to register by providing username, email, and password.
2. `User login`: Authenticates users by verifying their username/email and password.
3. `Token-based authentication`: Generates and returns a token for authenticated users.
4. `User storage`: Stores registered users in a list (database integration can be added).
5. `JSON response`: Returns JSON responses for registration, login, and other API endpoints.
6. `Flask framework`: Utilizes the Flask framework for building the API.
7. `Basic implementation`: Provides a starting point for implementing authentication and authorization features.

Version 1.1 - 
- In this updated code, I've added the following changes:
1. Imported the necessary libraries: `JWTManager` from flask_jwt_extended for token management and `generate_password_hash` and `check_password_hash` from werkzeug.security for password hashing.
2. Configured the `JWT secret key` using app.config['JWT_SECRET_KEY']. Make sure to replace 'your_secret_key_here' with a secure secret key in your actual implementation.
3. Modified the `/register` route to hash the password using `generate_password_hash` before storing it in the database.
4. Modified the `/login` route to check the hashed password using `check_password_hash` and generate an access token using create_access_token.
5. Added the `@jwt_required decorator` to the `/protected route` to ensure authentication is required to access this endpoint. The `get_jwt_identity()` function is used to retrieve the current user's identity from the token.


## License

This project is licensed under the [MIT License](LICENSE).
