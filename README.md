# recipe-app-api
Recipe App API

# docker-compose build

# docker-compose run --rm app sh -c "flake8"

# docker-compose up



Connect database to django server using docker:

Engine type of database
hostname or ip address
port number of default for postgres
database name of postgres database
username
password


defined in settings.py file already defined in it.
we are pulling this information from environment variables
environment variables used pull information from environment
so django connect to database

used in local development or production environment both
it means single place to configure our application

easy to pull environment in pythong 
    os.environ.get()

Psycopg2 is django to connect to database module used in the pythong to postgresql

psycopg2-binary
    - ok for development (local development)
    - not good for production
psycopg2
    - compile from source code
    - specific operating system
    - required additional dependencies
    - easy to install with docker
    - list of packages dependencies in docs
        - c compiler
        - python3-dev
        - libpq-dev
    - equivalent package for alpine
        - postgresql-client
        - build-base
        - postgresql-dev
        - musl-dev
    - found by searching and trial and error


Problem with Docker compose
- Using depends_on ensures service starts
    - doesn't ensure application is running

Database RAct Condition:

Docker services timeline

Database                  Django App
__________________________________________________
Service starting          
                          Service starting
Postgres starting         App starting
                          Connect to DB

Solution to avoid crash django app while postgres starting
- Make Django "wait for db"

Database starting > Django starting > Postgres starting > app starting > wait for db > checking postgres start or not once database start is done > app start























