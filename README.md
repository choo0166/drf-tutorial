## Django REST framework tutorial

Based on the official DRF [tutorial](https://www.django-rest-framework.org/tutorial/1-serialization/).

### Project setup

- Clone and `cd` into project directory. Create a python virtualenv and install dependencies.

  ```bash
  python -m venv .venv
  python -m pip install -r requirements.txt
  ```

- Setup local postgres DB for development (Mac OS)

  Note: Assumes the `homebrew` package manager is installed.

  ```bash
  brew install postgresql@15
  echo 'export PATH="/usr/local/opt/postgresql@15/bin:$PATH"' >> ~/.zshrc
  brew services start postgresql@15
  ```

  Optionally, install `pgAdmin` for administration GUI or use `pgcli` for the command line interface.

  ```bash
  brew install --cask pgadmin4
  ```

  Create a user for the Django ORM.

  ```bash
  psql -U $USER -d postgres
  CREATE USER "<USER>" WITH PASSWORD '<PASSWORD>' # replace <USER> and <PASSWORD>
  ```

  Create the project database and associate the owner to the user created above.

  ```bash
  CREATE DATABASE <DB> OWNER "<USER>"
  GRANT ALL PRIVILEGES ON DATABASE <DB> TO "<USER>"
  \q
  ```

  Edit the `DB_NAME`, `DB_USER` and `DB_PASSWORD` variables in the .env file accordingly.

- Make model migrations to create database tables. Must be run whenever the model definitions (in `models.py`) are updated.

  ```bash
  python manage.py makemigrations snippets
  python manage.py migrate snippets
  ```
  Add the connection details of the database in `pgAdmin` and check for the newly created tables under schemas.

- Finally, start the development server.

  ```bash
  python manage.py runserver
  ```













