# # Highly Loaded Python API for financial system with multi-tenancy support.


# at http://0.0.0.0:8000/api/docs you will find the documentation for all your endpoints. 
This is the default path for accessing the automatically generated API documentation in FastAPI.

# Start a project with Poetry:

1. Make sure you have Poetry installed. If not, install it with the following command:

https://python-poetry.org/docs/

2. Activate the Poetry virtual environment:

poetry shell

3. Enter your data for the configuration in the .env file.

If you want to use Poetry, for example, first open the .env file. Then you must specify DB_HOST = localhost and define your data in another variable.

4. You can also see the certs directory. I have not written this directory in .gitignore because I have generated a private and a public key for you for HASH_ALGORITHM = HS256 so that you can set up your secret key.

5. Next, an important step before running my project is to use Alembic for migrations and revisions. Here are the actions you can take:

If you only want to apply the latest migration only, please run "alembic upgrade head".

If you want to start fresh with a new migration:

Execute "alembic downgrade base" first. This command deletes all revisions. Then delete my revision from the versions directory. Then, create your own revision with "alembic revision --autogenerate -m "Your message here"". Finally, apply the new revision with "alembic upgrade head". If you encounter errors after running "alembic upgrade head", please create a new database as this problem is not related to my code."


6. Start the project:

/home/anton/.cache/pypoetry/virtualenvs/pythonproject-pflyVAO5-py3.10/bin/python /home/anton/flask_project/pythonProject/start.py

# Start a project with Docker Compose:

1. Install Docker and Docker Compose if they are not already installed.

https://docs.docker.com/compose/install/

2. Change to the root directory of the project (where you will find the docker-compose.yml file).

3. Enter your data for the configuration in the .env file.

For example, if you want to use docek, you must write DB_HOST = postgres and specify your data in another variable 

4. You can also see the directory for the certifications. I have not entered this directory in .gitignore because I have generated a private and a public key for you for HASH_ALGORITHM = HS256 so that you can set up your secret key if you want.

5. "Next, an important step before running my project is to use Alembic for migrations and revisions. Here are the actions you can take:

If you only want to apply the latest migration, please run "docker-compose exec backend upgrade head".

If you want to start with a new migration:

First execute "docker-compose exec backend alembic downgrade base". This command deletes all revisions.
Then delete my revision from the versions directory.
Then create your own revision with "docker-compose exec backend alembic revision --autogenerate -m "Your message here"".
Finally, apply the new revision with "docker-compose exec backend alembic upgrade head".
If you encounter errors after running "docker-compose exec backend alembic upgrade head", please create a new database as this issue is not related to my code."

6. Start the project with Docker Compose:


docker-compose up --build

Note: Before using Docker Compose, make sure that you have installed Docker and Docker Compose on your system.


# Run tests:

To do this, go to the test folder and then type in your console: "pytest"
I'm very sorry I didn't write many tests, but I promise I did test my project.
You can see that I have tested some endpoints with test_db and they work)

# API Endpoints

# Create account:

Method: POST
Path: /auth/create_account

Description: Registers a new user.

Actions: Creates a new user in the database, generates access and update tokens, saves the update in the user session and returns the access tokens.

# Login:

Method: POST

Path: /auth/login

Description: Logs the user into the system.

Actions: Generates access and update tokens for an existing user, stores them in the user's session and returns the access token.

# Refresh:

Method: POST

Path: /auth/refresh

Description: Refreshes the access token.

Actions: Checks the validity of the refresh token, retrieves the user data from the token, creates a new access token and returns it.

# Logout:

Method: GET

Path: /auth/logout

Description: Logs the user out of the system.

Actions: Removes access and update tokens from the user's session, terminates the current session.

Translated with DeepL.com (free version)

# GET /api/users/me

Description: Retrieves the data of the current authorized user.

Response: The data of the current user.

# PATCH /api/users/change/profile

Description: Changes the profile of the current user.

Query parameter: New profile data.

Response: Updated user data.

# POST /api/users/make/password_reset_token

Description: Create a token to reset the password of the current user.
Response: Successful creation of a new token to reset the password.

# POST /api/users/reset_password

Description: Resets the password of the current user.

Request parameter: New password.

Response: Successful execution of the password reset.

# GET /api/users/admin

Description: Retrieves the data of the currently authorized administrator.

Response: Current data of the authorized administrator.

# POST /api/users/deposit/me

Description: Deposit endpoint My account

Query parameter: Amount on my_deposit.

Response: Data on the updated balance of my_account.

# POST /api/users/deposit

Description: Deposit account endpoint

Query parameters: ID of the account to which the deposit is to be made, amount to be deposited.

Response: Data on the updated account balance.

# POST /api/users/withdraw/me

Description: Withdraw my account

Query parameter: Amount to my_withdraw.

Response: Data about the updated account balance of my_account.

# POST /api/users/withdraw

Description: Withdraw account

Query parameters: ID of the account to be withdrawn to, amount to be withdrawn.

Response: Data on the updated account balance.

# POST /api/users/transfer/from_me

Description: Withdraw transfer from my account

Query parameters: ID of the account to which the transfer is to be made, amount to be transferred.

Response: Data on the updated account balance.

# POST /api/users/transfer

Description: Transfer withdrawal from one account to another account

Query parameters: D of the account to be transferred from, ID of the account to be transferred to, Amount to be transferred.

Response: Data on the updated account balance.
