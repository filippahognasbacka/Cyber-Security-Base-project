# Cyber Security Base project

### Startup Instructions:

1. Install Poetry in case you haven't already following these instructions:
https://python-poetry.org/docs/#installation

2. Install dependencies by doing: `poetry install`

3. Activate the virtual environment with: `poetry shell`

4. Run Flask application with: `flask run`

5. Access the application in your web browser with `http://127.0.0.1:5000`


## OWASP 2021 vulnerabilities:

### Vulnerability 1

#### A01:2021 – Broken Access Control

https://github.com/filippahognasbacka/Cyber-Security-Base-project/blob/main/app.py#L128

https://github.com/filippahognasbacka/Cyber-Security-Base-project/blob/main/app.py#L147

A vulnerability for broken access control is the lack of inspecting whether a user owns a note or not. Before, any user was able to view and delete another user's notes simply by guessing the id of the note. The fix checks whether a user is the owner of the note.

Appropriate fix would be to uncomment:
https://github.com/filippahognasbacka/Cyber-Security-Base-project/blob/main/app.py#L138-139

and

https://github.com/filippahognasbacka/Cyber-Security-Base-project/blob/main/app.py#L157-163
