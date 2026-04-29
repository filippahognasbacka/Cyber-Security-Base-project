# Cyber Security Base project

A simple note app where users can write, add and delete notes.

### Startup Instructions:

1. Start by cloning the repository to a directory

2. Install Poetry in case you haven't already following these instructions:
https://python-poetry.org/docs/#installation

3. Install dependencies by doing `poetry install`

4. Activate the virtual environment with `poetry shell`

5. Run Flask application with `flask run`

6. Access the application in your web browser with `http://127.0.0.1:5000`


## OWASP 2021 5 vulnerabilities:

### Vulnerability 1

#### A01:2021 – Broken Access Control

https://github.com/filippahognasbacka/Cyber-Security-Base-project/blob/main/app.py#L128

https://github.com/filippahognasbacka/Cyber-Security-Base-project/blob/main/app.py#L147

A vulnerability for broken access control is the lack of inspecting whether a user owns a note or not. Before, any user was able to view and delete another user's notes simply by guessing the id of the note. The fix checks whether a user is the owner of the note.

In the screenshots we can see that both users alice and heips both see the same notes that are originally made by Alice. In the after photo when heips tries to access the note, their access is denied since the owner is Alice.

Appropriate fix would be to uncomment:
https://github.com/filippahognasbacka/Cyber-Security-Base-project/blob/main/app.py#L138-139

and

https://github.com/filippahognasbacka/Cyber-Security-Base-project/blob/main/app.py#L157-163

### Vulnerability 2

#### A06:2021 - Vulnerable and Outdated Components

https://github.com/filippahognasbacka/Cyber-Security-Base-project/blob/main/poetry.lock#L190

Here we can find a vulnerability by using an old Werkzeug version that has been classified as high risk by https://security.snyk.io/package/pip/werkzeug.

The fix is to change the version to a more recent, safe one:

`version = "3.1.8"` and then running `poetry update`

### Vulnerability 3

#### A02:2021 – Cryptographic Failures

https://github.com/filippahognasbacka/Cyber-Security-Base-project/blob/main/app.py#L66-67

Here a serious vulnerability is storing the password as itself without hashing it. Incase attackers would have access to the database they would immediately get access to all users passwords.

In the screenshot we can see that this is possible in terminal by first doing `sqlite3 app.db` and then the query `SELECT username, password FROM users;`. By doing this we see a list of all users and their passwords.

The fix is to use a default hashing by for example Werkzeug library which prolongs cracking of individual passwords.

https://github.com/filippahognasbacka/Cyber-Security-Base-project/blob/main/app.py#L52-55

In the screenshots we first see a list of users and their passwords but after making the changes and deleting the old database and making a new user, we can now see the password for the user is hashed.

### Vulnerability 4

#### A07:2021 – Identification and Authentication Failures

https://github.com/filippahognasbacka/Cyber-Security-Base-project/blob/main/app.py#L81-82