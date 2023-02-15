- clone the repository:

    via HTTPS:  

    `git clone https://github.com/igorkaruna/codingvalley.git`  
    
    via SSH:  

    `git clone  git@github.com:igorkaruna/codingvalley.git`  

- Run the project via docker-compose:  

    #### Development server  
    To run this project via docker-compose using default development server it's 
    necessary to do the next steps:  

    1. Add the `env.dev` file to `config/.env` directory and add the following environ variables:  

            SECRET_KEY - the secret key of the project;
            DEBUG - debug mode(for development on local machine use '1');
            ALLOWED_HOSTS - allowed hosts(for local machine use '127.0.0.1');
            INTERNAL_IPS - internal ips(for local machine use '127.0.0.1');
            DJANGO_SETTINGS_MODULE - reference to setting.py of project(use 'base.settings');
            PYTHONPATH - base dir for imports(use 'app');
            SQL_ENGINE - database engine(for PostgreSQL use 'django.db.backends.postgresql');
            SQL_DATABASE - database name;
            SQL_USER - database user;
            SQL_PASSWORD - database password;
            SQL_HOST - database service name(use 'db');
            SQL_PORT - database port(use '5432');
            DATABASE - name of RDBMS(for PostgreSQL use 'postgres');
            API_KEY - api key from OMDb API(it's possible to get from https://www.omdbapi.com/apikey.aspx);
            CORS_ALLOWED_ORIGINS - allowed hosts(for local machine use 'http://127.0.0.1');
            REDIS_HOST - database service name(use 'redis');
            EMAIL_PORT - port for email(for gmail use '587');
            EMAIL_HOST - host for email(for gmail use 'smtp.gmail.com');
            EMAIL_HOST_USER - email address of the account(account for the mailing);
            EMAIL_HOST_PASSWORD - email password of the account.  

    2. Add `database-dev` file to `config/db` directory and add the following environ variables:  

            POSTGRES_DB - database name;
            POSTGRES_USER - database user;
            POSTGRES_PASSWORD - database password.  

        **Pay attention: POSTGRES_DB, POSTGRES_USER, POSTGRES_PASSWORD variables must be the same as SQL_DATABASE, SQL_USER, SQL_PASSWORD respectively.**  

    3. Run docker-compose using the following command:  

            docker-compose -f docker-compose.dev.yml up    

        After that you can run the Django project which works at http://0.0.0.0:8000/. 
        The `app` directory is mounted into container so the code changes will be 
        applied authomatically.  

        To stop docker-compose use:  

            docker-compose -f docker-compose.dev.yml down  


    #### Production server  
    To run this project via docker-compose using gunicorn + nginx it's necessary to do the next steps:  

    1. Add the `env.prod` file to `config/.env` directory and add the environ variables which can be 
    the same as in `env.dev` file. Not forget to change `DEBUG` to be 1.  

    2. Add `database-env.prod` file to `config/db` directory and add the environ variables which must be 
    the same as in `database-dev` file.  

    3. Run docker-compose using the following command:  

            docker-compose -f docker-compose.prod.yaml up  

    4. Make migration:  

            docker-compose -f docker-compose.prod.yaml exec web python blog/manage.py migrate --noinput  

    5. Collect static files:  

            docker-compose -f docker-compose.prod.yaml exec web python blog/manage.py collectstatic --no-input --clear  

        After that you can run the Django project which works at http://0.0.0.0:1337/. 
        The `app` directory is not mounted into container so to apply the code change the 
        image must be rebuilt by using --build option.  

        To stop docker-compose use:  

            docker-compose -f docker-compose.prod.yaml down  
