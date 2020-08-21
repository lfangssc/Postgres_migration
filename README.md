# Postgres_migration
## Simple set up on data migration on local postgres

Component
- posgtres setup in local, here use docker managed container to set up 
- Vitural enviroment
- Flask, SQLAlchemy, flask_migrate, flask_script
- apps.py (['SQLALCHEMY_DATABASE_URI'] = "postgresql://postgres:postgres@localhost:5432/postgres")
- DB manager DBeaver 

docker managed container

    $ docker run --name postgres-docker -e POSTGRES_PASSWORD=postgres -p 5432:5432 -d postgres
    $ docker container ls -a
    CONTAINER ID        IMAGE              COMMAND                  CREATED             STATUS                       PORTS                    NAMES
    165beb2a9bbc        postgres          "docker-entrypoint.s…"   12 seconds ago      Up 11 seconds                0.0.0.0:5432->5432/tcp   postgres-docker
    
Virrual enviroment and package install

    python3 -m venv DB_Mg_env
    source ./DB_Mg_env/bin/activate
    (DB_Mg_env) $ pip install psycopg2-binary
    (DB_Mg_env) $ pip install flask-sqlalchemy
    (DB_Mg_env) $ pip install Flask-Migrate
    (DB_Mg_env) $ pip install Flask-Script
    
work on flask ORM apps.py, see attachment

in virtual enviroment

    (DB_Mg_env) $ python apps.py db init
    (DB_Mg_env) $ python apps.py db migrate
    (DB_Mg_env) $ python apps.py db upgrade
    
Dbeaver connect postgres local, schemas should be generated 

migrate db, for example delecte one column in DB schema

delecte the ORM in app.py

in virtual enviroment

    (DB_Mg_env) $ python apps.py db init
    (DB_Mg_env) $ python apps.py db migrate
    (DB_Mg_env) $ python apps.py db upgrade

 disconnect Dbeaver postgres local, reconnect, schemas should be modified.
 
 Alembic and version controll


![ ](tree.png?raw=true "Title")

reference
[SQLAlchemy Migrations Using Flask-Migrate](https://www.youtube.com/watch?v=BAOfjPuVby0&t=393s)


[Using SQLAlchemy with Flask and PostgreSQL](https://stackabuse.com/using-sqlalchemy-with-flask-and-postgresql/)
